---
title: 导出 Power BI 分页报表 API
description: 了解如何导出嵌入式 Power BI 分页报表
author: KesemSharabi
ms.author: kesharab
ms.topic: how-to
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 04/05/2020
ms.openlocfilehash: bb06f5b0a170189c3c98b734a09259645a650c55
ms.sourcegitcommit: 6bc66f9c0fac132e004d096cfdcc191a04549683
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/06/2020
ms.locfileid: "91748163"
---
# <a name="export-paginated-report-to-file-preview"></a>将分页报表导出为文件（预览）

使用 `exportToFile` API，可通过 REST 调用来导出 Power BI 分页报表。 支持以下文件格式：
* **.pptx** (PowerPoint)
* **.pdf**
* **.xlsx** (Excel)
* **.dox** (Word)
* **.csv**
* **.xml**
* **.mhtml**
* **图像**
    * 导出为图像时，可以通过 `OutputFormat` 格式设置来设置图像格式
    * 支持的 OutputFormat 值：.bmp、.emf、.gif、.jpeg、.png 或 .tiff（默认）

## <a name="usage-examples"></a>用法示例

可以多种方式使用导出功能。 下面是几个示例：

* **“发送到打印程序”按钮** - 在应用中创建一个按钮；如果有人单击此按钮，就会触发导出作业。 此作业可以将查看后的报表导出为 .pdf 或 .pptx；完成后，用户可以下载文件。 使用报表参数和格式设置，你可以以特定的状态导出报表，包括筛选数据、自定义页面大小和其他特定于格式的设置。 由于此 API 是异步的，因此可能需要一段时间才能获取文件。

* **电子邮件附件** - 每隔一段时间自动发送包含 .pdf 报表附件的电子邮件。 如果需要自动向主管发送每周报表，就会发现此方案非常有用。

## <a name="using-the-api"></a>使用 API

此 API 是异步的。 调用后，[exportToFile](/rest/api/power-bi/reports/exporttofile) API 会触发导出作业。 在导出作业触发后，使用[轮询](/rest/api/power-bi/reports/getexporttofilestatus)来跟踪此作业，直到它完成。

在导出完成后，轮询 API 调用返回用于获取文件的 [Power BI URL](/rest/api/power-bi/reports/getfileofexporttofile)。 此 URL 在 24 小时内有效。

## <a name="supported-features"></a>支持的功能

### <a name="format-settings"></a>格式设置

为每种文件格式指定各项格式设置。 支持的属性和值等同于分页报表 URL 参数的[设备信息参数](../../paginated-reports/report-builder-url-parameters.md#report-commands-rdl)。

下面是两个示例，其中一个示例使用报表页面大小将报表的前四页导出为 .pptx 文件，而另一个示例将报表的第三页导出为 .jpeg 文件。

**将前四页导出为 .pptx**

```json
{
      "format": "PPTX",
      "paginatedReportConfiguration":{
            "formatSettings":{
                  "UseReportPageSize": "true",
                  "StartPage": "1",
                  "EndPage": "4"
            }
      }
}
```

**将第三页导出为 .jpeg**

```json
{
      "format": "IMAGE",
      "paginatedReportConfiguration":{
            "formatSettings":{
                  "OutputFormat": "JPEG",
                  "StartPage": "3",
                  "EndPage": "3"
            }
      }
}
```

### <a name="report-parameters"></a>报表参数

你可以使用 `exportToFile` API，通过一组报表参数以编程方式导出报表。 这种方法是使用[报表参数](../../paginated-reports/paginated-reports-parameters.md)功能实现的。

下面是设置报表参数值的示例。

```json
{
      "format": "PDF",
      "paginatedReportConfiguration":{
            "parameterValues":[
                  {"name": "State", "value": "WA"},
                  {"name": "City", "value": "Seattle"},
                  {"name": "City", "value": "Bellevue"},
                  {"name": "City", "value": "Redmond"}
            ]
      }
}
```

### <a name="authentication"></a>Authentication

只能使用用户（或主用户）或[服务主体](embed-service-principal.md)进行身份验证。

### <a name="row-level-security-rls"></a>行级别安全性 (RLS)

使用定义了行级别安全性 (RLS) 的 Power BI 数据集作为数据源时，你可以导出显示仅对某些用户可见的数据的报表。 例如，若要导出使用区域角色定义的销售报表，可以编程方式将报表筛选为只显示特定区域。

若要使用 RLS 进行导出，必须对报表用作数据源的 Power BI 数据集具有读取权限。

下面是为 RLS 提供有效用户名的示例。

```json
{
      "format": "PDF",
      "paginatedReportConfiguration":{
            "identities": [
                  {"username": "john@contoso.com"}            
            ]
      }
}
```

## <a name="code-examples"></a>代码示例

代码示例中使用的 Power BI API SDK 可从[此处](https://www.nuget.org/packages/Microsoft.PowerBI.Api)下载。

创建导出作业时，要遵循以下三个步骤：

1. 发送导出请求。
2. 轮询。
3. 获取文件。

此部分举例说明了各个步骤。

### <a name="step-1---sending-an-export-request"></a>第 1 步 - 发送导出请求

第 1 步是发送导出请求。 在本示例中，导出请求是针对特定报表页范围、大小和报表参数值发送的。

```csharp
private async Task<string> PostExportRequest(
    Guid reportId,
    Guid groupId)
{
    // For documentation purposes the export configuration is created in this method
    // Ordinarily, it would be created outside and passed in
    var paginatedReportExportConfiguration = new PaginatedReportExportConfiguration()
    {
        FormatSettings = new Dictionary<string, string>()
        {
            {"PageHeight", "14in"},
            {"PageWidth", "8.5in" },
            {"StartPage", "1"},
            {"EndPage", "4"}
        },
        ParameterValues = new List<ParameterValue>()
        {
            { new ParameterValue() {Name = "State", Value = "WA"} },
            { new ParameterValue() {Name = "City", Value = "Redmond"} }
        }
    };

    var exportRequest = new ExportReportRequest
    {
        Format = FileFormat.PDF,
        PaginatedReportExportConfiguration = paginatedReportExportConfiguration,
    };

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
    const int secToMillisec = 1000;
    do
    {
        if (DateTime.UtcNow.Subtract(startTime).TotalMinutes > timeOutInMinutes || token.IsCancellationRequested)
        {
            // Error handling for timeout and cancellations
            return null;
        }

        var httpMessage = 
            await Client.Reports.GetExportToFileStatusInGroupWithHttpMessagesAsync(groupId, reportId, exportId);
            
        exportStatus = httpMessage.Body;
        if (exportStatus.Status == ExportState.Running || exportStatus.Status == ExportState.NotStarted)
        {
            // The recommended waiting time between polling requests can be found in the RetryAfter header
            // Note that this header is only populated when the status is either Running or NotStarted
            var retryAfter = httpMessage.Response.Headers.RetryAfter;
            var retryAfterInSec = retryAfter.Delta.Value.Seconds;

            await Task.Delay(retryAfterInSec * secToMillisec);
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
        var httpMessage = 
            await Client.Reports.GetFileOfExportToFileInGroupWithHttpMessagesAsync(groupId, reportId, export.Id);

        return new ExportedFile
        {
            FileStream = httpMessage.Body,
            ReportName = export.ReportName,
            FileExtension = export.ResourceFileExtension,
        };
    }

    return null;
}

public class ExportedFile
{
    public Stream FileStream;
    public string ReportName;
    public string FileExtension;
}
```

### <a name="end-to-end-example"></a>端到端示例

这是导出报表的端到端示例。 此示例包括以下几个阶段：
1. [发送导出请求](#step-1---sending-an-export-request)。
2. [轮询](#step-2---polling)。
3. [获取文件](#step-3---getting-the-file)。

```csharp
private async Task<ExportedFile> ExportPaginatedReport(
    Guid reportId,
    Guid groupId,
    int pollingtimeOutInMinutes,
    CancellationToken token)
{
    try
    {
        var exportId = await PostExportRequest(reportId, groupId);

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
>[将报表导出为文件](export-to.md)

> [!div class="nextstepaction"]
>[为客户嵌入内容](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[为组织嵌入内容](embed-sample-for-your-organization.md)