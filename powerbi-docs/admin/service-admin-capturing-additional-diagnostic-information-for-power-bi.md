---
title: 捕获诊断信息以获取支持
description: 说明了如何手动从 Power BI 服务收集诊断信息。 将此信息发送给支持人员，以帮助他们排查问题。
author: kfollis
ms.author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 01/21/2021
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 59e434d571c5b8d10c944bc385fb4e18ed89963c
ms.sourcegitcommit: 84f0e7f31e62cae3bea2dcf2d62c2f023cc2d404
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/26/2021
ms.locfileid: "98781036"
---
# <a name="capture-diagnostic-information-from-the-power-bi-service"></a>捕获来自 Power BI 服务的诊断信息

在你就 Power BI 服务遇到的问题联系 Microsoft 支持部门寻求帮助之前，可以收集可帮助我们解决问题的文件。 建议从浏览器会话获取浏览器跟踪。 浏览器跟踪是一种诊断文件，可提供有关在发生问题时在 Power BI 服务中发生的情况的重要详细信息。

Power BI 管理员可以使用 [Power Platform 管理中心](https://admin.powerplatform.microsoft.com/)的“帮助 + 支持”体验获取自助解决方案并与支持人员联系。 使用以下步骤收集的诊断文件可附加到支持请求，以帮助进行故障排除。 有关更多支持选项，请参阅 [Power BI 支持选项](service-support-options.md)。

若要为你所用的浏览器收集浏览器跟踪和其他会话信息，请按照以下步骤操作。

## <a name="collect-a-browser-trace"></a>收集浏览器跟踪

> [!IMPORTANT]
>登录到 [Power BI 服务](https://app.powerbi.com)，然后开始收集浏览器跟踪信息（无论使用哪种浏览器）。 此步骤非常重要，可确保跟踪信息不包括与登录相关的敏感信息。

#### <a name="google-chrome-or-microsoft-edge"></a>[Google Chrome 或 Microsoft Edge](#tab/google-chrome-or-microsoft-edge)

Google Chrome 和 (Chromium)都基于 [Chromium 开放源代码项目](https://www.chromium.org/Home)。 以下步骤演示如何使用开发人员工具，这些工具在这两个浏览器中类似。 有关详细信息，请参阅 [Chrome DevTools](https://developers.google.com/web/tools/chrome-devtools) 和 [Microsoft Edge (Chromium) 开发工具](/microsoft-edge/devtools-guide-chromium)。

1. 登录后，按键盘上的 F12。 或者在 Microsoft Edge 中，选择“设置和更多 (...)” > “更多工具” > “开发人员工具”。 在 Google Chrome 中，选择“自定义和控制 Google Chrome” :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/chromium-icon-settings.png" alt-text="Google Chrome 设置菜单。" border="false"::: > **更多工具** > **开发人员工具**。
1. 准备通过设置跟踪选项来收集浏览器跟踪。 在开始重现问题之前，还应停止并清除收集的所有信息。 默认情况下，浏览器只保留当前加载页的跟踪信息。 按照这些步骤进行操作，将浏览器设置为保留所有跟踪信息，即使重现转到多个页面：
    1. 在“开发人员工具”窗口中，选择“网络”选项卡。然后，选择“保留日志”。
    
       :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/browser-trace-preserve-log.png" alt-text="选择了“网络”选项卡和“保留日志”的开发人员工具。" :::

     2. 选择“控制台”选项卡，然后选择“设置” > “保留日志”。 
   
           :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/browser-trace-console-settings.png" alt-text="选择了“控制台”选项卡和“保留日志”的开发人员工具。" :::

        再次选择“设置”以关闭“控制台设置”。

3. 接下来，停止并清除正在进行的任何记录。 选择“网络”选项卡，选择“停止记录网络日志”，然后选择“清除”。
   
   :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/browser-trace-stop-recording.png" alt-text="选择了“网络”选项卡、“停止记录”和“清除记录”选项的开发人员工具。" :::
     
2. 现在，你将重现 Power BI 服务中遇到的问题。 若要开始，在“开发人员工具”中选择“网络”选项卡。选择“记录网络日志”。

    > [!IMPORTANT]
    >在开始重现问题之前，刷新 Power BI 服务的浏览器页面，以便正确捕获跟踪。

   重现导致你需要帮助解决问题的步骤。

     :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/browser-trace-record-network-log.png" alt-text="选择了“网络”选项卡和“网络日志”的开发人员工具。" :::

    重现此问题时，你会在“开发人员工具”窗口中看到类似于下图的输出。

    :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/browser-trace-output.png" alt-text="带有“网络”选项卡显示会话输出的开发人员工具。" :::
    
3. 在重现问题后，需要保存日志文件并将其附加到支持请求。
    1. 若要导出网络日志，在“开发人员工具”中选择“网络”选项卡。选择“停止记录网络日志”。 然后选择“导出 HAR...”并保存文件。

         :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/browser-trace-export-har.png" alt-text="选择了“网络”选项卡、“停止记录”和“导出 HAR”选项的开发人员工具。" :::

    2. 若要导出控制台输出，请在“开发人员工具”中选择“控制台”选项卡。右键单击显示的消息，然后选择“另存为...”，将控制台输出保存到文本文件中。
    
         :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/browser-trace-save-as.png" alt-text="选择了“控制台”选项卡和显示“另存为”选项的开发人员工具。" :::

   以压缩格式（例如 .zip）打包保存的 HAR 文件、控制台输出和屏幕记录，并将该文件附加到支持请求。

#### <a name="apple-safari"></a>[Apple Safari](#tab/apple-safari)

以下步骤说明如何在 Apple Safari 中使用开发人员工具。 有关详细信息，请参阅 [Safari 开发人员工具概述](https://support.apple.com/guide/safari-developer/safari-developer-tools-overview-dev073038698/11.0/mac)。

1. 登录后，在 Apple Safari 中启用开发人员工具：
    1. 在页面页眉中，选择“Safari” > “首选项”。
    
       :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/safari-preferences.png" alt-text="选择了“首选项”的 Apple Safari 菜单。" :::

    2. 选择“高级”，然后选择“在菜单栏中显示开发菜单”以启用开发人员工具。
    
       :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/safari-show-develop-menu.png" alt-text="选择了“在菜单栏中显示开发菜单”的 Safari 高级菜单。" :::

2. 接下来，将在“Web 检查器”中设置选项，使浏览器可以保留所有跟踪信息。 默认情况下，浏览器只保留当前加载页的跟踪信息。 这些设置可确保，即使重现需要转到多个页面，也会收集跟踪信息。

    1. 选择“开发” > “显示 Web 检查器”。
    
        :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/safari-web-inspector.png" alt-text="选择了“显示 Web 检查器”的“开发”菜单。" :::

    2. 选择“网络” > “保留日志”
       
         :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/safari-network-preserve-log.png" alt-text="选择了“网络”和“保留日志”的“Web 检查器”菜单。" :::

    1. 选择“控制台” > “保留日志”
   
       :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/safari-console-preserve-log.png" alt-text="选择了“控制台”和“保留日志”的“Web 检查器”菜单。" :::

3. 设置这些选项后，选择“网络” > “清除网络项”，确保日志只包含有关问题重现的详细信息。

    :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/safari-clear-network-items.png" alt-text="选择了“网络”和“清除网络项”的“Web 检查器”菜单。" :::


4. 现在可以重现问题了。 
    > [!IMPORTANT]
    >在开始重现问题之前，刷新 Power BI 服务的浏览器页面，以便正确捕获跟踪。

    完成这些步骤，重现你遇到的问题。 重现问题时，你会在“网络”窗口中看到类似于下图的输出。

    :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/safari-session-output.png" alt-text="显示示例输出的“网络”窗口。" :::

5. 在重现问题后，需要保存日志文件并将其附加到支持请求。

    1. 若要导出网络日志，请从“网络”选项卡中，选择“导出”，并将该文件另存为 HAR 格式。

         :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/safari-export.png" alt-text="选择了“导出”选项的“网络”选项卡。" :::

    2. 若要导出控制台输出，请在“开发”工具窗格中，选择“控制台”选项卡，然后展开该窗口。 将光标置于控制台输出的开头，然后拖动并选择输出的整个内容。 按命令键+C 复制输出，并将其保存到文本文件中。

   以压缩格式（例如 .zip）打包保存的 HAR 文件、控制台输出和屏幕记录，并将该文件附加到支持请求。

#### <a name="firefox"></a>[Firefox](#tab/firefox)

以下步骤说明如何在 Firefox 中使用开发人员工具。 有关详细信息，请参阅 [Firefox 开发人员工具](https://developer.mozilla.org/docs/Tools)。

1. 登录后，按键盘上的 F12。 或者，在 Firefox 中，选择“打开菜单”:::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/firefox-menu.png" alt-text="Firefox 菜单图标。" border="false"::: > “Web 开发人员” > “切换工具”。 这些工具显示在屏幕底部。

1. 接下来，将在“检查器”中设置选项，使浏览器可以保留所有跟踪信息。 默认情况下，浏览器只保留当前加载页的跟踪信息。 这些设置可确保，即使重现需要转到多个页面，也会收集跟踪信息。

    1. 在“检查器”窗口中，选择“网络”选项卡。然后，选择“保留日志”。
    
       :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/firefox-network-persist-logs.png" alt-text="选择了“网络”选项卡和“保留日志”的检查器工具。" :::

     2. 选择“控制台”选项卡，然后选择“控制台设置” > “保留日志”。 
   
           :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/firefox-console-persist-logs.png" alt-text="选择了“控制台”选项卡和“保留日志”的检查器工具。" :::

3. 设置这些选项后，请清除正在进行的任何记录。 选择“网络”选项卡，然后选择“清除”。
   
   :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/browser-trace-stop-recording.png" alt-text="选择了“网络”选项卡、“停止记录”和“清除记录”选项的开发人员工具。" :::
     
2. 现在可以重现问题了。 
    > [!IMPORTANT]
    >在开始重现问题之前，刷新 Power BI 服务的浏览器页面，以便正确捕获跟踪。
 
    完成这些步骤，重现你遇到的问题。
    
3. 在重现问题后，需要保存日志文件并将其附加到支持请求。
    1. 若要导出网络日志，请选择“网络” > “HAR 导出/导入”，然后选择“全部另存为 HAR”。

         :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/firefox-save-har.png" alt-text="选择了“HAR 导出/导入”菜单和“保存全部”选项的“网络”选项卡。" :::

    2. 若要导出控制台输出，请选择“控制台”选项卡。右键单击显示的消息，然后选择“将可见消息导出到”，并将控制台输出保存到文本文件中。
    
         :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/firefox-export-visible-messages.png" alt-text="选择的“控制台”选项卡和显示的”导出可见消息“选项。" :::

   以压缩格式（例如 .zip）打包保存的 HAR 文件、控制台输出和屏幕记录，并将该文件附加到支持请求。

---

收集诊断文件后，将它们附加到支持请求，以帮助支持工程师解决你的问题。 HAR 文件将包含有关浏览器窗口与 Power BI 服务之间的网络请求的所有信息，包括：

* 每个请求的活动 ID。

* 每个请求的精确时间戳。

* 返回到客户端的任何错误信息。

此跟踪还会包含用于填充屏幕上显示的视觉对象的数据。

## <a name="next-steps"></a>后续步骤

* [在 Microsoft 365 中跟踪 Power BI 服务运行状况](service-admin-health.md)
* [启用服务中断通知](service-interruption-notifications.md)
* [加入 Power BI 社区](https://community.powerbi.com/)
