---
title: 分页报表中的 URL 参数 - Power BI 报表生成器
description: 本主题介绍了 Power BI 分页报表生成器报表参数的常见用法、可以设置的属性及其他内容。
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
ms.reviewer: cfinlan
ms.custom: ''
ms.date: 09/10/2019
ms.openlocfilehash: e39864081ce4dd1ad415224454b75404e882e9ce
ms.sourcegitcommit: 01de0b01f66f28ca45b8d309d7864f261d6c9a85
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/16/2019
ms.locfileid: "74128311"
---
# <a name="url-parameters-in-paginated-reports-in-power-bi"></a>Power BI 的分页报表中的 URL 参数

可以通过将参数添加到 URL，将命令发送到 Power BI 中的分页报表。 例如，你可能已使用一组特定的报表参数值查看了报表。 你可使用预定义的 URL 访问参数在 URL 中封装这些信息。 可通过嵌入参数来呈现格式或设计报表工具栏的外观，进一步自定义 Power BI 处理报表的方式。 然后，可以将此 URL 直接粘贴到电子邮件或网页中，让他人在浏览器中采用相同的方式体验你的报表。 

下面是可以通过 URL 访问参数执行的操作： 

- 将报表参数发送到报表。 
- 以支持的文件格式启动报表内容导出。 
- 隐藏或查看参数窗格。 
- 指定 DeviceInfo 设置。 

如需获取通过 URL 访问提供的命令和设置的完整列表，请参阅本文后面的  [URL 访问参数参考](#url-access-parameter-reference)。 

## <a name="url-access-concepts"></a>URL 访问概念 

Power BI 的 URL 请求包含服务处理的参数。 服务处理 URL 请求的方式取决于在 URL 中包括的参数、参数前缀和项的类型。 分页报表 URL 功能与支持标准 URL 寻址的大多数浏览器和应用程序兼容。 

## <a name="url-access-syntax"></a>URL 访问语法 

URL 请求可包含以任何顺序列出的多个参数。 参数用和号 (&) 分隔。 名称和值对用等号 (=) 分隔。 例如：

```
powerbiserviceurl?rp:parametervalueh&rdl:parameter=value  
```

## <a name="syntax-description"></a>语法说明 

### <a name="powerbiserviceurl"></a>powerbiserviceurl 

Power BI 租户的 Web 服务 URL。 例如： 

**&** 用于分隔 URL 访问参数的名称和值对。

**前缀** URL 参数（例如 rp: 或 rdl:）的前缀，用于指定 Power BI 服务中的操作。 

> [!NOTE]
> 报表参数需要参数前缀并且区分大小写。 

**参数** 参数名称。 

### <a name="value"></a>值 

与所使用参数的值相对应的 URL 文本。 

有关在 URL 中传递报表参数的示例，请参阅 [在 URL 中传递报表参数](report-builder-url-pass-parameters.md)。

## <a name="url-access-parameter-reference"></a>URL 访问参数参考

可使用以下参数作为 URL 的一部分，在 Power BI 中配置分页报表的外观。 此部分列出了最常用的参数。 参数不区分大小写，如果与输出格式相关，则以参数前缀  `rdl:`  开头。  

### <a name="report-commands-rdl"></a>报表命令 (`rdl:`) 

**导出格式** 指定呈现和导出报表采用的格式。 可用值为：
 
- PPTX (PowerPoint)
- MHTML 
- 图像 
- EXCELOPENXML (EXCEL) 
- WORDOPENXML (WORD) 
- CSV 
- PDF 
- XML 

**设备信息** 可以为以下导出格式指定其他输出参数。 

PDF：

- rdl:AccessiblePDF=true/false
- rdl:Columns=integer
- rdl:ColumnSpacing=decimal(in)
- rdl:DpiX=integer
- rdl:DpiY=integer
- rdl:EndPage=integer
- rdl:HumanReadablePDF=true/false
- rdl:MarginBottom=decimal(in)
- rdl:MarginLeft=decimal(in)
- rdl:MarginRight=decimal(in)
- rdl:MarginTop=decimal(in)
- rdl:PageHeight=decimal(in)
- rdl:PageWidth=decimal(in)
    - rdl:StartPage=integer
    
CSV：

- rdl:Encoding=string
- rdl:ExcelMode=true/false
- rdl:FieldDelimiter=string
- rdl:FileExtension=string
- rdl:NoHeader=true/false
- rdl:Qualifier=string
- rdl:RecordDelimiter=string
- rdl:SuppressLineBreaks=true/false
    - rdl:UseFormattedValues=true/false
    
WORDOPENXML (WORD)：

- rdl:AutoFit=string -> True/False/Never/Default
- rdl:ExpandToggles=true/false
- rdl:FixedPageWidth=true/false
- rdl:OmitHyperlinks=true/false
- rdl:OmitDrillthroughs=true/false

EXCELOPENXML (EXCEL)：

- rdl:OmitDocumentMap=true/false
- rdl:OmitFormulas=true/false
    - rdl:SimplePageHeaders=true/false
    
PPTX (PowerPoint)：
 
- rdl:Columns=integer
- rdl:ColumnSpacing=decimal(in)
- rdl:DpiX=integer
- rdl:DpiY=integer
- rdl:EndPage=integer
- rdl:MarginBottom=decimal(in)
- rdl:MarginLeft=decimal(in)
- rdl:MarginRight=decimal(in)
- rdl:MarginTop=decimal(in)
- rdl:PageHeight=decimal(in)
- rdl:PageWidth=decimal(in)
- rdl:StartPage=integer
    - rdl:UseReportPageSize=true/false

XML：

- rdl:XSLT=string
- rdl:MIMEType=string
- rdl:UseFormattedValues=true/false
- rdl:Indented=true/false
- rdl:OmitNamespace=true/false
- rdl:OmitSchema=true/false
- rdl:Encoding=string
- rdl:FileExtension=string
- rdl:Schema=true/false

## <a name="next-steps"></a>后续步骤

- [在 Power BI 分页报表的 URL 中传递报表参数](report-builder-url-pass-parameters.md)
- [Power BI Premium 中的分页报表是什么？](paginated-reports-report-builder-power-bi.md)
