---
title: 使用适用于 Power BI 报表服务器的 REST API 进行开发
description: REST API 提供以编程方式访问 Power BI 报表服务器目录中对象的选项。
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 05/25/2018
ms.openlocfilehash: 154415f3662aebaa086d3452eb84e589333ecd28
ms.sourcegitcommit: e9c45d6d983e8cd4cb5af938f838968db35be0ee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57327840"
---
# <a name="develop-with-the-rest-apis-for-power-bi-report-server"></a>使用适用于 Power BI 报表服务器的 REST API 进行开发

Power BI 报表服务器支持表述性状态转移 (REST) API。 REST API 是支持一组 HTTP 操作（方法）的服务终结点，支持在报表服务器中创建、检索、更新或删除资源访问权限。

REST API 提供以编程方式访问 Power BI 报表服务器目录中对象的选项。 对象的示例包括文件夹、报表、KPI、数据源、数据集、刷新计划、订阅等。 例如，你可以使用 REST API 导航文件夹层次结构，查找文件夹内容或下载报表定义等。 另外，还可以创建、更新和删除对象。 使用对象的示例包括上传报表、执行刷新计划、删除文件夹等。

[!INCLUDE [GDPR-related guidance](../includes/gdpr-hybrid-note.md)]

## <a name="components-of-a-rest-api-requestresponse"></a>REST API 请求/响应的组件

REST API 请求/响应对可以分为五个组件：

* 请求 URI，其中包括：`{URI-scheme} :// {URI-host} / {resource-path} ? {query-string}`。 尽管请求 URI 包含在请求消息标头中，但我们还是可以在此单独调出，因为大多数语言或框架都要求你单独将其从请求消息传递出去。
  
  * URL 方案：指示用来传输请求的协议。 例如 `http` 或 `https`。
  * URI 主机：指定托管 REST 服务终结点的服务器的域名或 IP 地址，如 `myserver.contoso.com`。
  * 资源路径：指定资源或资源集合，其可能包括服务使用的用于确定资源选择的多个段。 例如：`CatalogItems(01234567-89ab-cdef-0123-456789abcdef)/Properties` 可用于获取 CatalogItem 的指定属性。
  * 查询字符串（可选）：提供附加的简单参数，如 API 版本或资源选择条件。
* HTTP 请求消息标头字段：
  
  * 必需的 [HTTP 方法](https://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html)（也称为操作或谓词），它会告诉服务所请求的操作类型。 Reporting Services REST API 支持 DELETE、GET、HEAD、PUT、POST 和 PATCH 方法。
  * 指定的 URI 和 HTTP 方法需要的其他可选标头字段。
* 可选 HTTP“请求消息正文”字段，用于支持 URI 和 HTTP 操作。 例如，POST 操作包含作为复杂的参数传递的 MIME 编码对象。 对于 POST 或 PUT 操作，正文的 MIME 编码类型也应在 `Content-type` 请求标头中指定。 某些服务要求你使用特定的 MIME 类型，如 `application/json`。
* HTTP“响应消息标头”字段：
  
  * [HTTP 状态代码](http://www.w3.org/Protocols/HTTP/HTRESP.html)涉及的范围从 2xx 成功代码到 4xx 或 5xx 错误代码。 或者，可能会返回服务定义的状态代码，如 API 文档中所指示。
  * 可选的其他标头字段，根据需要支持请求的响应，例如 `Content-type` 响应标头。
* 可选 HTTP**响应消息正文**字段：
  
  * HTTP 响应正文中会返回 MIME 编码的响应对象，例如来自返回数据的 GET 方法的响应。 通常情况下，这些对象以结构化格式返回，例如 JSON 或 XML，如 `Content-type` 响应标头所指示。

## <a name="api-documentation"></a>API 文档

对于现代 API 文档，需要现代的 REST API 调用。 REST API 在 OpenAPI 规范（又称 Swagger 规范） 的基础之上构建，并且文档可在 [SwaggerHub](https://app.swaggerhub.com/apis/microsoft-rs/PBIRS/2.0) 上找到。 除了记录 API 外，SwaggerHub 还可用选择的语言（JavaScript TypeScript、C#、Java、Python、Ruby 等）帮助生成客户端库。

## <a name="testing-api-calls"></a>测试 API 调用

用于测试 HTTP 请求/响应消息的一种工具是 [Fiddler](http://www.telerik.com/fiddler)。 Fiddler 是一个免费的 Web 调试代理，可以截获 REST 请求，从而便于诊断 HTTP 请求/响应消息。

## <a name="next-steps"></a>后续步骤

在 [SwaggerHub](https://app.swaggerhub.com/apis/microsoft-rs/PBIRS/2.0) 上查看可用的 API。

示例可在 [GitHub](https://github.com/Microsoft/Reporting-Services) 上找到。 此示例包含基于 TypeScript、React、Webpack 和 PowerShell 示例构建的 HTML5 应用。

更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)