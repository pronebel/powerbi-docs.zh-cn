---
title: 教程：连接到 SQL Server 中的本地数据
description: 了解如何将 SQL Server 用作网关数据源，包括如何刷新数据。
author: mgblythe
manager: kfile
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: tutorial
ms.date: 07/15/2019
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 54ef11b51fb02b6913b4d591967a140c5affc1b8
ms.sourcegitcommit: 9d13ef7a257b5006fca5f92acf5b611f5cd143a2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/18/2019
ms.locfileid: "68307396"
---
# <a name="refresh-data-from-an-on-premises-sql-server-database"></a>从本地 SQL Server 数据库刷新数据

在本教程中，将了解如何从本地网络中存在的关系数据库中刷新 Power BI 数据集。 具体而言，本教程使用示例 SQL Server 数据库，Power BI 必须通过本地数据网关访问该数据库。

在本教程中，将完成以下步骤：

> [!div class="checklist"]
> * 创建并发布从本地 SQL Server 数据库导入数据的 Power BI Desktop (.pbix) 文件。
> * 通过数据网关在 Power BI for SQL Server 连接中配置数据源和数据集设置。
> * 配置刷新计划，确保 Power BI 数据集包含最新数据。
> * 执行数据集的按需刷新。
> * 查看刷新历史记录，分析过去刷新周期的结果。
> * 删除本教程中创建的项目来清理资源。

## <a name="prerequisites"></a>先决条件

- 如果你还没有，请在开始之前注册 [Power BI 免费试用版](https://app.powerbi.com/signupredirect?pbi_source=web)。
- 在本地计算机上[安装 Power BI Desktop](https://powerbi.microsoft.com/desktop/)。
- 在本地计算机上[安装 SQL Server ](/sql/database-engine/install-windows/install-sql-server)，并还原[来自备份的示例数据库](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksDW2017.bak)。 有关 AdventureWorks 的详细信息，请参阅 [AdventureWorks 安装和配置](/sql/samples/adventureworks-install-configure)。
- 在与 SQL Server 相同的本地计算机上[安装本地数据网关](service-gateway-onprem.md)（在生产环境中，通常为其他计算机）。

> [!NOTE]
> 如果你不是网关管理员且不想自己安装网关，请与组织中的网关管理员联系。 他们可创建所需的数据源定义，以将数据集连接到 SQL Server 数据库。

## <a name="create-and-publish-a-power-bi-desktop-file"></a>创建并发布 Power BI Desktop 文件

按照以下过程通过 AdventureWorksDW 示例数据库创建基本 Power BI 报表。 将报表发布到 Power BI 服务，以便在 Power BI 中获取数据集，然后可在后续步骤中配置和刷新。

1. 在 Power BI Desktop 的“主页”选项卡上，选择“获取数据”\>“SQL Server”    。

2. 在“SQL Server 数据库”对话框中，输入“服务器”和“数据库(可选)”名称，确保数据连接模式为“导入”，然后选择“确定”       。

    ![SQL Server 数据库](./media/service-gateway-sql-tutorial/sql-server-database.png)

3. 验证凭据，然后选择“连接”   。

    > [!NOTE]
    > 如果无法进行身份验证，请确保选择正确的身份验证方法并使用具有数据库访问权限的帐户。 在测试环境中，可使用具有显式用户名和密码的数据库身份验证。 在生产环境中，通常使用 Windows 身份验证。 请参阅[刷新方案疑难解答](refresh-troubleshooting-refresh-scenarios.md)，并联系数据库管理员联系获取其他帮助。

1. 如果出现“加密支持”对话框，请选择“确定”   。

2. 在“导航器”对话框中，选择“DimProduct”表，然后选择“加载”    。

    ![数据源导航器](./media/service-gateway-sql-tutorial/data-source-navigator.png)

3. 在 Power BI Desktop“报表”  视图的“可视化效果”  窗格中，选择“堆积柱形图”  。

    ![堆积柱形图](./media/service-gateway-sql-tutorial/stacked-column-chart.png)

4. 在报表画布中选择柱形图后，在“字段”窗格中选择“EnglishProductName”和“ListPrice”字段    。

    ![字段窗格](./media/service-gateway-sql-tutorial/fields-pane.png)

5. 将“EndDate”拖到报表级筛选器，在“基本筛选”下，仅选中“(空白)”复选框     。

    ![报表级筛选器](./media/service-gateway-sql-tutorial/report-level-filters.png)

    此时，图表应如下所示。

    ![已完成的柱形图](./media/service-gateway-sql-tutorial/finished-column-chart.png)

    请注意，列出的 5 件“Road-250”产品标价最高  。 在本教程稍后部分更新数据和刷新报表时，此内容将出现变化。

6. 使用名称“AdventureWorksProducts.pbix”保存报表。

7. 在“主页”选项卡上，选择“发布”\>“我的工作区”\>“选择”     。 如果系统要求你登录到 Power BI 服务，请登录。

8. 在“成功”屏幕上，选择[在 Power BI 中打开“AdventureWorksProducts.pbix”]   。

    [发布到 Power BI](./media/service-gateway-sql-tutorial/publish-to-power-bi.png)

## <a name="connect-a-dataset-to-a-sql-server-database"></a>将数据集连接到 SQL Server 数据库

在 Power BI Desktop 中，可直接连接到本地 SQL Server 数据库，但 Power BI 服务需要一个数据网关来充当云与本地网络之间的网桥。 按照以下步骤将本地 SQL Server 数据库作为数据源添加到网关，然后将数据集连接到此数据源。

1. 登录到 Power BI。 在右上角，选择设置齿轮图标，然后选择“设置”  。

    ![Power BI 设置](./media/service-gateway-sql-tutorial/power-bi-settings.png)

2. 在“数据集”选项卡上，选择“AdventureWorksProducts”数据集，以便可通过数据网关连接到本地 SQL Server 数据库   。

3. 展开网关连接，并验证是否至少列出了一个网关  。 如果没有网关，请参阅本教程前面的[先决条件](#prerequisites)部分，获取有关安装和配置网关的产品文档链接。

    ![网关连接](./media/service-gateway-sql-tutorial/gateway-connection.png)

4. 在“操作”下，展开切换按钮以查看数据源，然后选择“添加到网关”链接   。

    ![将数据源添加到网关](./media/service-gateway-sql-tutorial/add-data-source-gateway.png)

    > [!NOTE]
    > 如果你不是网关管理员且不想自己安装网关，请与组织中的网关管理员联系。 他们可创建所需的数据源定义，以将数据集连接到 SQL Server 数据库。

5. 在“网关”管理页的“数据源设置”标签上，输入并验证以下信息，然后选择“添加”    。

    | 选项 | 值 |
    | --- | --- |
    | 数据源名称 | AdventureWorksProducts |
    | 数据源类型 | SQL Server |
    | 服务器 | SQL Server 实例名称，例如 SQLServer01（必须与 Power BI Desktop 中指定的名称相同）。 |
    | 数据库 | SQL Server 数据库名称，例如 AdventureWorksDW（必须与 Power BI Desktop 中指定的名称相同）。 |
    | 身份验证方法 | Windows 或 Basic（通常为 Windows）。 |
    | 用户名 | 用于连接到 SQL Server 的用户帐户。 |
    | 密码 | 用于连接到 SQL Server 的帐户的密码。 |

    ![数据源设置](./media/service-gateway-sql-tutorial/data-source-settings.png)

6. 在“数据集”选项卡上，再次展开“网关连接”部分   。 选择你配置的数据网关（它显示在安装它的计算机上运行的状态），然后选择“应用”   。

    ![更新网关连接](./media/service-gateway-sql-tutorial/update-gateway-connection.png)

## <a name="configure-a-refresh-schedule"></a>配置刷新计划

现在，你已通过数据网关将 Power BI 中的数据集连接到本地 SQL Server 数据库，接下来请按照以下步骤配置刷新计划。 按计划刷新数据集有助于确保报表和仪表板具有最新数据。

1. 在左侧的导航窗格中，打开“我的工作区”\>“数据集”   。 为 AdventureWorksProducts 数据集选择省略号 (...)，然后选择“计划刷新”    。

    > [!NOTE]
    > 请确保为 AdventureWorksProducts 数据集选择省略号，而不是为名称相同的报表选择省略号  。 AdventureWorksProducts 报表的上下文菜单没有“计划刷新”选项   。

2. 在“计划刷新”部分的“不断更新数据”下，将刷新设置为“开”    。

3. 选择适当的刷新频率（本例中为每日），然后在“时间”下选择“添加其他时间”，以指定所需刷新时间（本例中为上下午 6:30）     。

    ![配置计划刷新](./media/service-gateway-sql-tutorial/configure-scheduled-refresh.png)

    > [!NOTE]
    > 如果数据集位于共享容量上，则每天最多可配置 8 个时间段；如果位于 Power BI Premium 上，则每天最多可配置 48 个时间段。

4. 将“向我发送刷新失败通知电子邮件”复选框保留为启用状态，并选择“应用”   。

## <a name="perform-an-on-demand-refresh"></a>执行按需刷新

你现已配置刷新计划，Power BI 会在下一计划时间（15 分钟内）刷新数据集。 如果要加快数据刷新速度以执行网关和数据源配置测试等操作，请使用左侧导航窗格的数据集菜单中的“立即刷新”选项进行按需刷新  。 按需刷新不影响下一计划刷新时间，但会计入在上一部分中提到的每日刷新限制。

为便于说明，通过使用 SQL Server Management Studio (SSMS) 更新 AdventureWorksDW 数据库中的 DimProduct 表来模拟对示例数据的更改。

```sql

UPDATE [AdventureWorksDW].[dbo].[DimProduct]
SET ListPrice = 5000
WHERE EnglishProductName ='Road-250 Red, 58'

```

现按照以下步骤操作，使更新后的数据可通过网关连接传输到数据集并进入 Power BI 中的报表。

1. 在 Power BI 服务的左侧导航窗格中，选择并展开“我的工作区”  。

2. 在“数据集”下，针对 AdventureWorksProducts 数据集选择省略号 (...)，然后选择“立即刷新”     。

    ![立即刷新](./media/service-gateway-sql-tutorial/refresh-now.png)

    请注意，右上角显示 Power BI 正在准备执行请求的刷新。

3. 选择“我的工作区”\>“报表”\>“AdventureWorksProducts”  。 查看更新后的数据是如何传输的，现标价最高的产品是“Road-250 Red, 58”  。

    ![更新后的柱形图](./media/service-gateway-sql-tutorial/updated-column-chart.png)

## <a name="review-the-refresh-history"></a>查看刷新历史记录

最好在刷新历史记录中定期查看既往刷新周期的结果。 数据库凭据可能已过期，或者所选网关在计划刷新到期时可能已脱机。 按照以下步骤检查刷新历史记录并检查问题。

1. 在 Power BI 用户界面的右上角，选择设置齿轮图标，然后选择“设置”  。

2. 切换到“数据集”并选择要检查的数据集，例如 AdventureWorksProducts   。

3. 选择“刷新历史记录”链接，打开“刷新历史记录”对话框   。

    ![刷新历史记录链接](./media/service-gateway-sql-tutorial/refresh-history-link.png)

4. 在“计划”选项卡上，请注意过去计划的刷新和按需刷新及其“开始”和“结束”时间，状态为“已完成”，这表示 Power BI 已成功刷新      。 对于失败的刷新，可看到错误消息并检查错误详细信息。

    ![刷新历史记录详细信息](./media/service-gateway-sql-tutorial/refresh-history-details.png)

    > [!NOTE]
    > OneDrive 选项卡仅与连接到 OneDrive 或 SharePoint Online 上的 Power BI Desktop 文件、Excel 工作簿或 CSV 文件的数据集相关，详见 [Power BI 中的数据刷新](refresh-data.md)。

## <a name="clean-up-resources"></a>清理资源

如果你不想再使用示例数据，请在 SQL Server Management Studio (SSMS) 中删除该数据库。 如果你不想使用 SQL Server 数据源，请从数据网关中删除该数据源。 如果安装数据网关的目的只是要完成本教程，请考虑卸载它。 还应删除上传 AdventureWorksProducts.pbix 文件时由 Power BI 创建的 AdventureWorksProducts 数据集和 AdventureWorksProducts 报表。

## <a name="next-steps"></a>后续步骤

在本教程中，你学习了如何将本地 SQL Server 数据库中的数据导入 Power BI 数据集，还学习了如何按计划和按需刷新此数据集，让使用此数据集的报表和仪表板在 Power BI 中保持更新状态。 接下来，你可在 Power BI 中详细了解如何管理数据网关和数据源。 查看“Power BI 中的数据刷新”这篇概念性文章可能也是一个好方法。

- [管理本地数据网关](/data-integration/gateway/service-gateway-manage)
- [管理数据源 - 导入/计划刷新](service-gateway-enterprise-manage-scheduled-refresh.md)
- [Power BI 中的数据刷新](refresh-data.md)
