---
title: 用于导出 Power BI 报表的 API
description: 了解如何导出嵌入的 Power BI 报表
author: KesemSharabi
ms.author: kesharab
ms.topic: how-to
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 03/24/2020
ms.openlocfilehash: 546f712c87e67240fd15ee2563252d8f322212c7
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85220991"
---
# <a name="export-power-bi-report-to-file-preview"></a>将 Power BI 报表导出到文件（预览）

使用 `exportToFile` API，可通过 REST 调用来导出 Power BI 报表。 支持以下文件格式：
* **.pptx** (PowerPoint)
* **.pdf**
* **.png**
    * 导出为 .png 时，包含多个报表页的报表会压缩为 zip 文件
    * .zip 中的每个文件都代表一个报表页
    * 报表页名称与 [Get Pages](https://docs.microsoft.com/rest/api/power-bi/reports/getpages) 或 [Get Pages in Group](https://docs.microsoft.com/rest/api/power-bi/reports/getpagesingroup) API 返回的值相同

## <a name="usage-examples"></a>用法示例

可以多种方式使用导出功能。 下面是几个示例：

* **“发送到打印程序”按钮** - 在应用中创建一个按钮；如果有人单击此按钮，就会触发导出作业。 此作业可以将查看后的报表导出为 .pdf 或 .pptx；完成后，用户可以下载文件。 使用书签，可以导出处于特定状态（包括应用配置的筛选器、切片器和其他设置）的报表。 由于此 API 是异步的，因此可能需要一段时间才能获取文件。

* **电子邮件附件** - 每隔一段时间自动发送包含 .pdf 报表附件的电子邮件。 如果需要自动向主管发送每周报表，就会发现此方案非常有用。

## <a name="using-the-api"></a>使用 API

使用此 API 前，请先验证是否已启用以下[管理员租户设置](../../admin/service-admin-portal.md#tenant-settings)：
* **将报表导出为 PowerPoint 演示文稿或 PDF 文档** - 默认处于启用状态。
* **将报表导出为图像文件** - 只有导出为 .png 才需要启用，默认处于禁用状态。

此 API 是异步的。 调用后，[exportToFile](https://docs.microsoft.com/rest/api/power-bi/reports/exporttofile) API 会触发导出作业。 在导出作业触发后，使用[轮询](https://docs.microsoft.com/rest/api/power-bi/reports/getexporttofilestatus)来跟踪此作业，直到它完成。

在轮询期间，此 API 返回表示已完成工作量的数字。 每个导出作业中的工作量都是根据报表页数计算的。 所有报表页的权重都相同。 例如，如果要导出的报表包含 10 个报表页，且轮询返回 70，则表示此 API 已处理导出作业中 10 个报表页中的 7 个。

在导出完成后，轮询 API 调用返回用于获取文件的 [Power BI URL](https://docs.microsoft.com/rest/api/power-bi/reports/getfileofexporttofile)。 此 URL 在 24 小时内有效。

## <a name="supported-features"></a>支持的功能

### <a name="selecting-which-pages-to-print"></a>选择要打印哪些报表页

根据 [Get Pages](https://docs.microsoft.com/rest/api/power-bi/reports/getpages) 或 [Get Pages in Group](https://docs.microsoft.com/rest/api/power-bi/reports/getpagesingroup) 返回值，指定要打印的报表页。 还可以指定要导出的报表页的顺序。

### <a name="bookmarks"></a>书签

 使用 `exportToFile` API，可以编程方式导出在应用筛选器后处于特定状态的报表。 这是通过使用[书签](../../consumer/end-user-bookmarks.md)功能完成的。 要使用书签导出报表，请使用[书签 JavaScript API](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Bookmarks)。

 例如，可以使用书签的 `capturedBookmark.state` 方法来捕获特定用户对报表所做的更改，然后导出当前状态下的报表。

不支持导出使用[个人书签](../../consumer/end-user-bookmarks.md#personal-bookmarks)和[永久性筛选器](https://powerbi.microsoft.com/blog/announcing-persistent-filters-in-the-service/)的报表。

### <a name="authentication"></a>身份验证

只能使用用户（或主用户）或[服务主体](embed-service-principal.md)进行身份验证。

### <a name="row-level-security-rls"></a>行级别安全性 (RLS)

使用[行级别安全性 (RLS)](embedded-row-level-security.md)，可以导出仅对特定用户显示数据的报表。 例如，若要导出使用区域角色定义的销售报表，可以编程方式将报表筛选为只显示特定区域。

若要使用 RLS 导出报表，必须拥有以下权限：
* 对报表连接到的数据集的写入和重新共享权限
* 如果报表驻留在 v1 工作区中，你必须是工作区管理员
* 如果报表驻留在 v2 工作区中，你必须是工作区成员或管理员

### <a name="data-protection"></a>数据保护

.pdf 和 .pptx 格式支持[敏感度标签](../../admin/service-security-data-protection-overview.md#sensitivity-labels-in-power-bi)。 如果将包含敏感度标签的报表导出为 .pdf 或 .pptx，导出的文件会显示包含其敏感度标签的报表。

无法使用[服务主体](embed-service-principal.md)将具有敏感度标签的报表导出到 .pdf 或 .pptx。

### <a name="localization"></a>本地化

使用 `exportToFile` API 时，可以传递相应本地化设置。 本地化设置会影响报表的显示方式（例如，根据所选的本地化设置来更改格式设置）。

## <a name="concurrent-requests"></a>并发请求

`exportToFile` 支持并发导出作业请求。 下表列出了可同时运行的作业数，具体视报表所驻留在的 SKU 而定。 并发请求引用报表页。 例如，在 A6 SKU 上，一个导出请求中的 20 个报表页会同时得到处理。 这与发送 20 个导出请求（每个报表页一个请求）所花费的时间大致相同。

超出并发请求数的作业不会终止。 例如，如果在 A1 SKU 中导出三个报表页，第一个作业将运行，后两个作业将等待后面两个执行周期。

|Azure SKU  |Office SKU  |并发报表页数上限  |
|-----------|------------|-----------|
|A1         |EM1         |1          |
|A2         |EM2         |2          |
|A3         |EM3         |3          |
|A4         |P1          |6          |
|A5         |P2          |12         |
|A6         |P3          |24         |

## <a name="limitations"></a>限制

* 要导出的报表必须驻留在高级容量或嵌入式容量中。
* 要导出的数据集必须驻留在高级容量或嵌入式容量中。
* 对于公共预览版，每小时导出的 Power BI 报表页数限制为每个容量 50 张。
* 导出的报表的文件大小不得超过 250MB。
* 导出为 .png 时，不支持敏感度标签。
* 无法使用[服务主体](embed-service-principal.md)将具有敏感度标签的报表导出到 .pdf 或 .pptx。
* 导出的报表中可包含 30 个报表页。 如果报表包含更多报表页，此 API 会返回错误，导出作业也会遭取消。
* 不支持导出使用[个人书签](../../consumer/end-user-bookmarks.md#personal-bookmarks)和[永久性筛选器](https://powerbi.microsoft.com/blog/announcing-persistent-filters-in-the-service/)的报表。
* 不支持导出包含下列 Power BI 视觉对象的报表。 如果你导出包含这些视觉对象的报表，包含这些视觉对象的报表部分将不会呈现，并会显示错误符号。
    * 未经认证的 Power BI 视觉对象
    * R 视觉对象
    * PowerApps
    * Python 视觉对象
    * Visio

## <a name="code-examples"></a>代码示例

创建导出作业时，要遵循以下三个步骤：

1. 发送导出请求。
2. 轮询。
3. 获取文件。

此部分举例说明了各个步骤。

### <a name="step-1---sending-an-export-request"></a>第 1 步 - 发送导出请求

第 1 步是发送导出请求。 在下面的示例中，导出请求是针对特定报表页发送的。

```csharp
/////// Export sample ///////
private async Task<string> PostExportRequest(
    Guid reportId,
    Guid groupId,
    FileFormat format,
    IList<string> pageNames = null /* Get the page names from the GetPages API */)
{
    var powerBIReportExportConfiguration = new PowerBIReportExportConfiguration
    {
        Settings = new ExportReportSettings
        {
            Locale = "en-us",
        },
        // Note that page names differ from the page display names.
        // To get the page names use the GetPages API.
        Pages = pageNames?.Select(pn => new ExportReportPage(pageName = pn)).ToList(),
    };
    var exportRequest = new ExportReportRequest
    {
        Format = format,
        PowerBIReportConfiguration = powerBIReportExportConfiguration,
    };

    // The 'Client' object is an instance of the Power BI .NET SDK
    var export = await Client.Reports.ExportToFileInGroupAsync(groupId, reportId, exportRequest);

    // Save the export ID, you'll need it for polling and getting the exported file
    return export.Id;
}
```

### <a name="step-2---polling"></a>第 2 步 - 轮询

发送导出请求后，使用轮询来确定等待的导出文件何时就绪。

```csharp
private async Task<Export> PollExportRequest(
    Guid reportId,
    Guid groupId,
    string exportId /* Get from the ExportToAsync response */,
    int timeOutInMinutes,
    CancellationToken token)
{
    Export exportStatus = null;
    DateTime startTime = DateTime.UtcNow;
    const int c_secToMillisec = 1000;
    do
    {
        if (DateTime.UtcNow.Subtract(startTime).TotalMinutes > timeOutInMinutes || token.IsCancellationRequested)
        {
            // Error handling for timeout and cancellations 
            return null;
        }

        // The 'Client' object is an instance of the Power BI .NET SDK
        var httpMessage = await Client.Reports.GetExportToFileStatusInGroupWithHttpMessagesAsync(groupId, reportId, exportId);
        exportStatus = httpMessage.Body;

        // You can track the export progress using the PercentComplete that's part of the response
        SomeTextBox.Text = string.Format("{0} (Percent Complete : {1}%)", exportStatus.Status.ToString(), exportStatus.PercentComplete);
        if (exportStatus.Status == ExportState.Running || exportStatus.Status == ExportState.NotStarted)
        {
            // The recommended waiting time between polling requests can be found in the RetryAfter header
            // Note that this header is only populated when the status is either Running or NotStarted
            var retryAfter = httpMessage.Response.Headers.RetryAfter;
            var retryAfterInSec = retryAfter.Delta.Value.Seconds;
            await Task.Delay(retryAfterInSec * c_secToMillisec);
        }
    }
    // While not in a terminal state, keep polling
    while (exportStatus.Status != ExportState.Succeeded && exportStatus.Status != ExportState.Failed);
    return exportStatus;
}
```

### <a name="step-3---getting-the-file"></a>第 3 步 - 获取文件

在轮询返回 URL 后，参照下面的示例来获取收到的文件。

```csharp
private async Task<ExportedFile> GetExportedFile(
    Guid reportId,
    Guid groupId,
    Export export /* Get from the GetExportStatusAsync response */)
{
    if (export.Status == ExportState.Succeeded)
    {
        // The 'Client' object is an instance of the Power BI .NET SDK
        var fileStream = await Client.Reports.GetFileOfExportToFileAsync(groupId, reportId, export.Id);
        return new ExportedFile
        {
            FileStream = fileStream,
            FileSuffix = export.ResourceFileExtension,
        };
    }
    return null;
}
public class ExportedFile
{
    public Stream FileStream;
    public string FileSuffix;
}
```

### <a name="end-to-end-example"></a>端到端示例

这是导出报表的端到端示例。 此示例包括以下几个阶段：
1. [发送导出请求](#step-1---sending-an-export-request)。
2. [轮询](#step-2---polling)。
3. [获取文件](#step-3---getting-the-file)。

```csharp
private async Task<ExportedFile> ExportPowerBIReport(
    Guid reportId,
    Guid groupId,
    FileFormat format,
    int pollingtimeOutInMinutes,
    CancellationToken token,
    IList<string> pageNames = null /* Get the page names from the GetPages API */)
{
    try
    {
        var exportId = await PostExportRequest(reportId, groupId, format, pageNames);
        var export = await PollExportRequest(reportId, groupId, exportId, pollingtimeOutInMinutes, token);
        if (export == null || export.Status != ExportState.Succeeded)
        {
            // Error, failure in exporting the report
            return null;
        }
        return await GetExportedFile(reportId, groupId, export);
    }
    catch
    {
        // Error handling
        throw;
    }
}
```

## <a name="next-steps"></a>后续步骤

了解如何为客户和组织嵌入内容：

> [!div class="nextstepaction"]
>[将分页报表导出为文件](export-paginated-report.md)

> [!div class="nextstepaction"]
>[为客户嵌入内容](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[为组织嵌入内容](embed-sample-for-your-organization.md)
