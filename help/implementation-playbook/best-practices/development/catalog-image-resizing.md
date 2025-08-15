---
title: 目录图像大小调整最佳实践
description: 了解如何在Adobe Commerce网站生产启动之前防止性能下降。
feature: Best Practices
role: Developer
exl-id: 591b1a62-bdba-4301-858a-77620ee657a9
source-git-commit: 823498f041a6d12cfdedd6757499d62ac2aced3d
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 0%

---

# 目录图像大小调整最佳实践

在商店投入生产之前，应调整所有目录图像的大小。 在生产之前无法调整图像大小会在页面加载期间强制调整图像大小，这会显着降低网站速度并在启动后的前几天到几周内增加服务器负载。

## 慢条斯理

使用默认的CLI命令调整所有映像的大小：

```bash
bin/magento catalog:images:resize
```

这种方法的缺点包括：

- 此过程是单线程的
- 该过程会调整已调整大小的图像的大小
- 此过程无法中断，可能需要几天时间

## 快速方式

Adobe Commerce 2.4中引入了异步图像大小调整功能，可更快地调整图像大小。

1. 在每台Web服务器上，临时启动一些额外的队列处理程序（每台服务器的物理处理器数的两倍）：

   ```bsh
   for i in {1.."$((2 * `nproc --all`))"};do bin/magento queue:consumers:start media.storage.catalog.image.resize &;done;
   ```

1. 验证队列处理程序是否正在运行：

   ```bash
   pgrep -fl media.storage.catalog.image.resize
   ```

1. 用所有图像大小调整请求填充队列：

   ```bash
   bin/magento catalog:images:resize --async
   ```

1. 调整所有图像大小后，终止进程：

   ```bash
   pkill -f media.storage.catalog.image.resize
   ```

## 快捷方式

还有另一种使用前端来调整图像大小的方法。

此方法的优点包括：

- 此过程是多线程的
- 进程是多服务器（如果您有多个Web节点、负载平衡器以及`media/`目录的共享磁盘空间）
- 流程会跳过已调整大小的图像

此方法在不到8小时内就调整了100,000个映像的大小，而CLI命令需要6天才能完成。

1. 登录到服务器。
1. 导航到`pub/media/catalog/product`并记下其中一个哈希(例如，0047d83143a5a3a4683afdf1116df680)。
1. 在以下示例中，将`www.example.com`替换为您商店的域，并将哈希替换为您指出的域。

>[!BEGINTABS]

>[!TAB sed]

```bash
cd pub/
find ./media/catalog/product -path ./media/catalog/product/cache -prune -o -type f -print | sed 's~./media/catalog/product/~https://www.example.com/media/catalog/product/cache/0047d83143a5a3a4683afdf1116df680/~g' > images.txt
```

>[!TAB 围攻]

`siege`的缺点是，如果并发设置为10，则它访问10次中的所有URL。

```bash
siege --file=./images.txt --user-agent="image-resizer" --no-follow --no-parser --concurrent=10 --reps=once
```

>[!TAB curl]

```bash
xargs -0 -n 1 -P 10 curl -X HEAD -s -w "%{http_code} %{time_starttransfer} %{url_effective}\n" < <(tr \\n \\0 <images.txt)
```

`-P`参数确定线程数。

>[!TAB bash one-liner]

`find/curl`示例的单行，以防您可以从映像所在的同一计算机上运行`curl`：

```bash
find ./media/catalog/product -path ./media/catalog/product/cache -prune -o -type f -print | sed 's~./media/catalog/product/~https://www.example.com/media/catalog/product/cache/0047d83143a5a3a4683afdf1116df680/~g' | xargs -n 1 -P 10 curl -X HEAD -s -w "%{http_code} %{time_starttransfer} %{url_effective}\n"
```

再次将`www.example.com`替换为您的网站域，并将`-P`设置为您的服务器可以处理的线程数，而不会崩溃。

>[!ENDTABS]

输出将返回商店中所有产品图像的列表。 您可以使用所有可用的服务器和处理器内核来爬网图像（使用`siege`或任何其他爬网程序），并以比其他方法快得多的速度生成大小调整缓存。

访问一个图像缓存URL时，如果背景中的所有图像大小尚不存在，则会生成这些大小。 此外，它会跳过已调整大小的文件。

>[!NOTE]
>
>- 云基础架构项目上的Adobe Commerce可以将产品图像大小调整卸载到Fastly服务。 请参阅[云指南](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization.html?lang=zh-Hans#deep-image-optimization)中的&#x200B;_深度图像优化_。
>- 如果使用远程存储模块，还可以尝试将图像大小调整卸载到nginx。 请参阅[配置指南](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/storage/remote-storage/remote-storage-image-resize.html?lang=zh-Hans)中的&#x200B;_为远程存储配置映像大小_。
