---
title: 在 Power BI Desktop 中使用 SAP Business Warehouse (BW) 连接器
description: 在 Power BI Desktop 中使用 SAP BW 连接器
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 01/13/2020
LocalizationGroup: Connect to data
ms.openlocfilehash: 1808638ad0ccaa2adc57d56bf1677dea0ca24440
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/01/2020
ms.locfileid: "96404654"
---
# <a name="use-the-sap-business-warehouse-connector-in-power-bi-desktop"></a>在 Power BI Desktop 中使用 SAP Business Warehouse 连接器

使用 Power BI Desktop 可以访问 SAP BusinessWarehouse (BW)  数据。

有关 SAP 客户如何在连接 Power BI 和现有 SAP BW 系统的过程中受益的信息，请参阅 [Power BI 和 SAP BW 白皮书](https://aka.ms/powerbiandsapbw)。 有关将 DirectQuery 与 SAP BW 结合使用的详细信息，请参阅 [DirectQuery 和 SAP Business Warehouse (BW)](desktop-directquery-sap-bw.md)。

从 Power BI Desktop 的 2018 年 6 月版本和 2018 年 10 月的正式版开始，SAP BW 连接器  将包含一个具有重大性能和功能改进的实现。 Microsoft 开发了 SAP BW 连接器 Implementation 2.0  。 可选择 SAP BW 连接器版本 1 或 Implementation 2.0 SAP 连接器。 以下部分依次介绍每个版本的安装。 从 Power BI Desktop 连接到 SAP BW 时，可选择其中一个连接器。

建议尽可能使用 Implementation 2.0 SAP 连接器。

## <a name="installation-of-version-1-of-the-sap-bw-connector"></a>安装 SAP BW 连接器版本 1

建议尽可能使用 Implementation 2.0 SAP 连接器。 本部分介绍如何安装 SAP BW 连接器版本 1。

1. 在本地计算机上安装 SAP NetWeaver  库。 可以从 SAP 管理员处获取 SAP NetWeaver 库，也可以直接从 [SAP 软件下载中心](https://support.sap.com/swdc)下载。 由于 SAP 软件下载中心的结构经常发生变化，因此没有有关站点导航的更多具体指导。 SAP NetWeaver 库通常包括在 SAP 客户端工具安装中。

   可以搜索 *SAP Note #1025361* 获取最新版本的下载位置。 请确保 SAP NetWeaver 库（32 位或 64 位）体系结构与你的 Power BI Desktop 安装相匹配。 然后，按照 SAP 说明安装 SAP NetWeaver RFC SDK  中包含的所有文件。
2. 在 Power BI Desktop 中，选择“获取数据”  。 “数据库”  选项包含“SAP Business Warehouse 应用程序服务器”  和“SAP Business Warehouse 消息服务器”  。

   ![获取适用于 SAP 的数据选项](media/desktop-sap-bw-connector/sap_bw_2a.png)

## <a name="installation-of-implementation-20-sap-connector"></a>Implementation 2.0 SAP 连接器的安装

SAP 连接器的 Implementation 2.0 需要使用 SAP .NET 连接器 3.0。 只有有效的 S 用户才能访问下载。 请与 SAP Basis 团队联系以获取 SAP .NET 连接器 3.0。

可以从 SAP 下载 [SAP .NET 连接器 3.0](https://support.sap.com/en/product/connectors/msnet.html)。

连接器随附 32 位和 64 位版本。 选择与 Power BI Desktop 安装匹配的版本。 当前网站列出了 .NET 4.0 framework 的两个版本：

* 适用于 Windows 32 位 (x86) 的 Microsoft .NET 3.0.22.0 的 SAP 连接器，zip 文件 (6.896 KB)，2019 年 6 月 1 日发布
* 适用于 Windows 64 位 (x64) 的 Microsoft .NET 3.0.22.0 的 SAP 连接器，zip 文件 (7.180 KB)，2019 年 6 月 1 日发布

安装时，在“可选安装步骤”  中，确保选择“将程序集安装到 GAC”  。

![SAP 可选安装步骤](media/desktop-sap-bw-connector/sap_bw_2b.png)

> [!NOTE]
> SAP BW 实现版本 1 需要使用 NetWeaver DLL。 如果使用 SAP 连接器的 Implementation 2.0 而不使用版本 1，则无需使用 NetWeaver DLL。

## <a name="version-1-sap-bw-connector-features"></a>SAP BW 连接器版本 1 的功能

通过 Power BI Desktop 中的 SAP BW 连接器版本 1，可从 SAP Business Warehouse 服务器  多维数据集导入数据，或者可使用 DirectQuery。

若要深入了解 SAP BW 连接器以及如何将其与 DirectQuery 一起使用，请参阅 [DirectQuery 和 SAP Business Warehouse (BW)](desktop-directquery-sap-bw.md)。

连接时，指定服务器  、系统编号  和客户端 ID  才能建立连接。

![SAP 服务器连接设置](media/desktop-sap-bw-connector/sap_bw_3a.png)

还可以指定两个其他高级选项  ：“语言代码”  ，以及针对指定服务器运行的自定义“MDX 语句”  。

![其他连接信息](media/desktop-sap-bw-connector/sap_bw_4a.png)

如果未指定 MDX 语句，连接设置将显示服务器中可用的多维数据集的列表。 可以向下钻取并选择可用多维数据集中的项目，包括维度和度量值。 Power BI 显示由[开放分析接口](https://help.sap.com/saphelp_nw70/helpdata/en/d9/ed8c3c59021315e10000000a114084/content.htm)公开的查询和多维数据集。

当从服务器中选择一个或多个项时，“导航器”对话框将创建输出表的预览。

![SAP 表预览](media/desktop-sap-bw-connector/sap_bw_5.png)

“导航器”  对话框还提供显示选项：

* **仅显示选定项**。 默认情况下，“导航器”  显示所有项。  此选项可用于验证最终选定的一组项。 查看选定项的另一种方法是选择预览区域中的列名称。
* **启用数据预览**。 此值为默认值。 显示数据预览。 禁用数据预览会减少服务器调用的数量，因其将不再请求数据进行预览。
* **技术名称**。 对于多维数据集中的对象，SAP BW 支持技术名称的概念  。 技术名称允许多维数据集所有者公开多维数据集对象的友好名称  ，而不是仅公开多维数据集中的那些对象的物理名称  。

![导航器窗口](media/desktop-sap-bw-connector/sap_bw_6.png)

选择所有必要的对象之后，可以通过选择以下选项之一来决定接下来要执行的操作：

* 选择“加载”  将输出表的整个行集加载到 Power BI Desktop 数据模型中。 此时将打开“报表”  视图。 可以使用“数据”  或“关系”  视图来开始可视化数据或进行进一步的修改。
* 选择“编辑”  以打开“查询编辑器”  。 在整个行集引入到 Power BI Desktop 数据模型之前，请在其中指定其他数据转换和筛选步骤。

除了从 SAP BW 多维数据集导入数据之外，你还可以从 Power BI Desktop 中的很多其他数据源导入数据，然后将它们合并到单一报表中。 此功能在 SAP BW 数据顶部演示各种有趣的报表和分析方案。

## <a name="using-implementation-20-sap-bw-connector"></a>使用 Implementation 2.0 SAP BW 连接器

创建新连接，以使用 SAP BW 连接器的 Implementation 2.0。 要创建新连接，请执行以下步骤。

1. 选择“获取数据”  。 选择“SAP Business Warehouse 应用程序服务器”  或“SAP Business Warehouse 消息服务器”  ，然后连接。

2. 在“新建连接”对话框中，选择实现。 选择 Implementation  2.0  （如下图所示）会启用“执行模式”  、“批大小”  和“启用特征结构”  。

    ![“SAP 连接”对话框](media/desktop-sap-bw-connector/sap_bw_7.png)

3. 选择“确定”。  至此，体验与[SAP BW 连接器版本 1 的功能](#version-1-sap-bw-connector-features)中所述的 SAP BW 连接器版本 1 一样。

### <a name="new-options-for-implementation-20"></a>Implementation 2.0 的新选项

Implementation 2.0 支持以下选项：

* ExecutionMode  指定用于执行服务器查询的 MDX 接口。 以下选项是有效的：

  * `SapBusinessWarehouseExecutionMode.BasXml`
  * `SapBusinessWarehouseExecutionMode.BasXmlGzip`
  * `SapBusinessWarehouseExecutionMode.DataStream`

    默认值为 `SapBusinessWarehouseExecutionMode.BasXmlGzip`。

    使用 `SapBusinessWarehouseExecutionMode.BasXmlGzip` 可在大数据集出现高延迟的情况下提高性能。

* BatchSize  指定执行 MDX 语句时一次检索的最大行数目。 检索大数据集时，少量的行会转换为较多的服务器调用。 大量的行可能会提高性能，但可能导致 SAP BW 服务器的内存问题。 默认值为 50000 行。

* EnableStructures  指示是否识别出特征结构。 此选项的默认值为 false。 影响可选择的对象列表。 本机查询模式下不支持。

此实现已弃用 ScaleMeasures 选项  。 现在，此行为与将 ScaleMeasures  设置为 false 相同，始终显示不成比例的值。

### <a name="additional-improvements-for-implementation-20"></a>Implementation 2.0 的其他改进

以下列表介绍了新实现的一些其他改进：

* 改进的性能。
* 可检索几百万行数据，通过批大小参数微调。
* 可切换执行模式。
* 支持压缩模式。 对高延迟连接或大型数据集特别有用。
* `Date` 变量检测改进。
* [实验性] 将日期 `Date`（ABAP 类型 DATS）和 `Time`（ABAP 类型 TIMS）维度分别公开为日期和时间，而不是文本值。
* 更好的异常处理。 现在，显示 BAPI 调用中发生的错误。
* BasXml 和 BasXmlGzip 模式下的列折叠。 例如，如果生成的 MDX 查询检索 40 列，但当前选择仅需要 10 列，此请求将传递到服务器，以检索较小的数据集。

### <a name="changing-existing-reports-to-use-implementation-20"></a>更改现有报表以使用 Implementation 2.0

仅在“导入”模式下，才能更改现有报表以使用 Implementation 2.0。 执行以下步骤:

1. 打开现有报表，选择功能区中的“编辑查询”  ，然后选择要更新的 SAP Business Warehouse 查询。

1. 右键单击查询，选择“高级编辑器”  。

1. 在“高级编辑器”  中，按如下所示更改 `SapBusinessWarehouse.Cubes` 调用：

    确定查询是否已包含选项记录，如以下示例所示：

    ![屏幕截图显示包含选项记录的纯文本查询。](media/desktop-sap-bw-connector/sap_bw_9.png)

    如果包含，请添加 `Implementation` 2.0 选项，如果存在，则删除 `ScaleMeasures` 选项，如下所示：

    ![屏幕截图显示已添加值实现 = 2.0 的纯文本查询。](media/desktop-sap-bw-connector/sap_bw_10.png)

    如果查询不包含选项记录，请添加。 对于以下选项：

    ![屏幕截图显示添加了选项记录的纯文本查询。](media/desktop-sap-bw-connector/sap_bw_11.png)

    只需将其更改为：

    ![屏幕截图显示已添加值实现 = 2.0 的新选项的纯文本查询。](media/desktop-sap-bw-connector/sap_bw_12.png)

我们已尽最大努力使 SAP BW 连接器的 Implementation 2.0 与版本 1 兼容。 但是，由于使用的 SAP BW MDX 执行模式不同，因此可能不一致。 若要解决任何不一致问题，请尝试在不同执行模式之间切换。

## <a name="troubleshooting"></a>故障排除

本部分提供有关使用 SAP BW 连接器的故障排除情景（和解决方案）。

1. 来自 SAP BW 的数值数据返回小数点，而不是逗号。 例如，1,000,000 的返回形式为 1.000.000。

   SAP BW 返回以 `,`（逗号）或 `.`（点）作为十进制分隔符的十进制数据。 为指定哪些 SAP BW 可用于十进制分隔符，Power BI Desktop 使用的驱动程序会调用 `BAPI_USER_GET_DETAIL`。 该调用返回一个名为 `DEFAULTS` 的结构，它包含一个名为 `DCPFM` 的字段，用于存储十进制格式表示法  。 该字段采用下列值之一：

   * “ ”（空格）= 小数点是逗号：N.NNN,NN
   * "X" = 小数点为句点：N,NNN.NN
   * "Y" = 小数点为 N NNN NNN,NN

   报告此问题的客户发现，对于特定用户（显示不正确的数据的用户），对 `BAPI_USER_GET_DETAIL` 的调用失败，并显示类似于以下消息的错误消息：

   ```xml
    You are not authorized to display users in group TI:
        <item>
            <TYPE>E</TYPE>
            <ID>01</ID>
            <NUMBER>512</NUMBER>
            <MESSAGE>You are not authorized to display users in group TI</MESSAGE>
            <LOG_NO/>
            <LOG_MSG_NO>000000</LOG_MSG_NO>
            <MESSAGE_V1>TI</MESSAGE_V1>
            <MESSAGE_V2/>
            <MESSAGE_V3/>
            <MESSAGE_V4/>
            <PARAMETER/>
            <ROW>0</ROW>
            <FIELD>BNAME</FIELD>
            <SYSTEM>CLNTPW1400</SYSTEM>
        </item>
   ```

   为了修复此错误，用户必须要求他们的 SAP 管理员授予在 Power BI 中使用的 SAPBW 用户执行 `BAPI_USER_GET_DETAIL` 的权限。 需要确定的另一点是，用户是否具有必需的 `DCPFM` 值，如本故障排除解决方案前面的内容所述。

2. SAP BEx 查询的连接
   
   你可以通过启用特定属性在 Power BI Desktop 中执行“BEx”查询，如下图所示：
   
   ![启用外部访问版本](media/desktop-sap-bw-connector/sap_bw_8.png)
   
3. “导航器”  窗口不显示数据预览，而是提供“对象引用未设置为对象实例”  的错误消息。
   
   SAP 用户需要访问特定 BAPI 功能模块才能获取元数据，并从 SAP BW 的 InfoProviders 中检索数据。 这些模块包括：

   * BAPI_MDPROVIDER_GET_CATALOGS
   * BAPI_MDPROVIDER_GET_CUBES
   * BAPI_MDPROVIDER_GET_DIMENSIONS
   * BAPI_MDPROVIDER_GET_HIERARCHYS
   * BAPI_MDPROVIDER_GET_LEVELS
   * BAPI_MDPROVIDER_GET_MEASURES
   * BAPI_MDPROVIDER_GET_MEMBERS
   * BAPI_MDPROVIDER_GET_VARIABLES
   * BAPI_IOBJ_GETDETAIL

   要解决此问题，请验证用户是否有权访问各种 MDPROVIDER 模块和 `BAPI_IOBJ_GETDETAIL`。 若要进一步排查此问题或类似问题，可以启用跟踪。 选择“文件”   > “选项和设置”   > “选项”  。 在“选项”  中，选择“诊断”  ，然后选择“启用跟踪”  。 在跟踪处于活动状态时尝试从 SAP BW 检索数据，并检查跟踪文件以获取更多详细信息。

## <a name="sap-bw-connection-support"></a>SAP BW 连接支持

下表详细说明了当前对 SAP BW 的支持。

|产品  |模型  |身份验证  |连接器  |SNC 库  |支持  |
|---------|---------|---------|---------|---------|---------|
|Power BI Desktop     |任何         | 用户/密钥  | 应用程序服务 | 不适用  | 是  |
|Power BI Desktop     |任何         | Windows          | 应用程序服务 | sapcrypto + gsskrb5/gx64krb5  | 是  |
|Power BI Desktop     |任何         | 通过模拟的 Windows | 应用程序服务 | sapcrypto + gsskrb5/gx64krb5  | 是  |
|Power BI Desktop     |任何         | 用户/密钥        | 消息服务器 | 不适用  | 是  |
|Power BI Desktop     |任何         | Windows        | 消息服务器 | sapcrypto + gsskrb5/gx64krb5  | 是  |
|Power BI Desktop     |任何         | 通过模拟的 Windows | 消息服务器 | sapcrypto + gsskrb5/gx64krb5  | 是  |
|Power BI Gateway     |导入      | 与 Power BI Desktop 相同 |         |   |   |
|Power BI Gateway     |DirectQuery | 用户/密钥        | 应用程序服务 | 不适用  | 是  |
|Power BI Gateway     |DirectQuery | 通过模拟的 Windows（固定用户、无 SSO） | 应用程序服务 | sapcrypto + gsskrb5/gx64krb5  | 是  |
|Power BI Gateway     |DirectQuery | 通过 Kerberos 使用 SSO 进行 DirectQuery 查询选项 | 应用程序服务 | sapcrypto + gsskrb5/gx64krb5   | 是  |
|Power BI Gateway     |DirectQuery | 用户/密钥        | 消息服务器 | 不适用  | 是  |
|Power BI Gateway     |DirectQuery | 通过模拟的 Windows（固定用户、无 SSO） | 消息服务器 | sapcrypto + gsskrb5/gx64krb5  | 是  |
|Power BI Gateway     |DirectQuery | 通过 Kerberos 使用 SSO 进行 DirectQuery 查询选项 | 消息服务器 | gsskrb5/gx64krb5  | 否  |
|Power BI Gateway     |DirectQuery | 通过 Kerberos 使用 SSO 进行 DirectQuery 查询选项 | 消息服务器 | sapcrypto  | 是  |

## <a name="next-steps"></a>后续步骤

有关 SAP 和 DirectQuery 的详细信息，请查看以下资源：

* [DirectQuery 和 SAP HANA](desktop-directquery-sap-hana.md)
* [DirectQuery 和 SAP Business Warehouse (BW)](desktop-directquery-sap-bw.md)
* [在 Power BI 中使用 DirectQuery](desktop-directquery-about.md)
* [Power BI 数据源](power-bi-data-sources.md)
* [Power BI 和 SAP BW 白皮书](https://aka.ms/powerbiandsapbw)
