---
title: Power BI 中的连接器扩展性
description: 连接器扩展能力、功能、安全设置和经过认证的连接器
author: cpopell
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/22/2019
ms.author: gepopell
LocalizationGroup: Connect to data
ms.openlocfilehash: 16b96d91a9dd37fa8a502bbcca772438c703cb63
ms.sourcegitcommit: d88cc6a87d4ba82ad2c4d496a3634f927e4ac529
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/30/2019
ms.locfileid: "66412968"
---
# <a name="connector-extensibility-in-power-bi"></a>Power BI 中的连接器扩展性

在 Power BI 中，客户和开发人员可以扩展与它们连接在很多方面的数据源。 它们使用现有的连接器和泛型数据源 （如 ODBC、 OData、 Oledb、 Web、 CSV、 XML、 JSON）。 或者，开发人员创建数据扩展插件，称为**自定义连接器**，并使其**认证连接器**。

目前，启用**自定义连接器**使用一个菜单，让你安全地控制你想要让您的系统上运行的自定义代码的级别。 您可以选择所有自定义连接器或连接器认证并由 Microsoft 在分布式**获取数据**对话框。

## <a name="custom-connectors"></a>自定义连接器

**自定义连接器**可以纳入各种各样的可能性，范围从小型 Api 关键到你的业务，大型的特定于行业的服务，Microsoft 尚未发布的连接器。 由供应商分发多个连接器。 如果您需要为特定的数据连接器，你应该联系供应商。

若要使用**自定义连接器**，将其放入 *\[文档]\\Power BI Desktop\\自定义连接器*文件夹，并调整安全设置，如中所述下一节。

无需调整安全设置即可使用“经认证的连接器”  。

## <a name="data-extension-security"></a>数据扩展插件安全性

若要更改数据扩展插件的安全设置，在**Power BI Desktop**选择**文件 > 选项和设置 > 选项 > 安全性**。

![控制是否想要加载的数据扩展插件安全选项的自定义连接器](media/desktop-connector-extensibility/data-extension-security-1.png)

在“数据扩展插件”下，可从两个安全级别中进行选择  ：

* （推荐）仅允许加载经过认证的扩展
* （不推荐）允许加载任何插件而不发出警告

如果你打算使用**自定义连接器**或您或第三方开发的连接器，必须选择 **"(Not Recommended) 允许任何扩展插件加载而不发出警告"** 。 除非您绝对信任自定义连接器，我们不建议此安全设置。 因为，在其中的代码可以处理凭据，包括将它们发送通过 HTTP，并忽略隐私级别。

在 **"（推荐）"** 安全设置，如果您的系统上有自定义连接器，出现错误，将显示描述连接器无法加载由于安全的。

![一个对话框，说明由于安全设置，请在此事例 TripPin 不能加载的自定义连接器](media/desktop-connector-extensibility/data-extension-security-2.png)

若要解决此错误和使用这些连接器，更改到您的安全设置 **"(Not Recommended) 允许任何扩展插件加载而不发出警告"** 设置，如前面所述。 然后，重新启动**Power BI Desktop**。

## <a name="certified-connectors"></a>经过认证的连接器

数据扩展插件的受限子网被视为**认证**。 访问中的已认证的连接器**获取数据**对话框。 但是，第三方开发人员创建连接器负责其维护和支持。 Microsoft 发布连接器，而不负责其性能或持续的函数。

如果想要认证自定义连接器，请让供应商联系 dataconnectors@microsoft.com。
