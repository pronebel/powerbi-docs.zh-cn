---
title: 在 Power BI 中通过 Analysis Services 表格模型实现动态行级别安全性
description: 通过 Analysis Services 表格模型实现动态行级别安全性
author: selvarms
manager: amitaro
ms.reviewer: davidi
editor: davidi
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 05/08/2019
ms.author: selvar
LocalizationGroup: Connect to data
ms.openlocfilehash: 57a285b075b17b2229ec4267a476cdd4b86ea7ad
ms.sourcegitcommit: 10a87c016f497dbeba32f94ed1f3688a70816fea
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/09/2019
ms.locfileid: "65513592"
---
# <a name="dynamic-row-level-security-with-analysis-services-tabular-model"></a>通过 Analysis Services 表格模型实现动态行级别安全性
本教程演示在 Analysis Services 表格模型中实现“行级别安全性”的所需步骤，以及如何将其用于 Power BI 报表。 本教程中的步骤在示例数据集上完成，旨在让您了解必需的步骤。

在本教程中，详细描述了以下步骤，帮助您了解在Analysis Services 表格模型中实现动态行级别安全性而需执行的步骤︰

* 在 **AdventureworksDW2012** 数据库中创建一个新安全表
* 生成含有所需事实数据表和维度表的表格模型
* 定义用户的角色和权限
* 将模型部署到 **Analysis Services 表格**实例
* 使用 Power BI Desktop 生成报表以显示对应于正在访问此报表的用户的数据
* 将报表部署到 **Power BI** 服务。
* 最后，基于报表创建新仪表板
* 与您的同事共享仪表板

执行本教程中的步骤需要使用 AdventureworksDW2012 数据库（可以通过[存储库](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)下载）。

## <a name="task-1-create-the-user-security-table-and-define-data-relationship"></a>任务 1：创建用户安全表并定义数据关系
很多已发布的文章都介绍了如何通过 **SQL Server Analysis Services (SSAS) 表格**模型定义行级别动态安全。 我们的示例遵照文章[通过使用行筛选器实现动态安全性](https://msdn.microsoft.com/library/hh479759.aspx)中所述的内容。 以下步骤引导完成本教程的第一项任务：

1. 本示例中，我们采用 **AdventureworksDW2012** 关系数据库。 在该数据库中创建 **DimUserSecurity** 表，如下图所示。 本示例中，我们使用 SQL Server Management Studio (SSMS) 来创建表。
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/createusersecuritytable.png)
2. 一旦创建并保存表，我们需要创建 **DimUserSecurity** 表的 **SalesTerritoryID** 列和 **DimSalesTerritory** 表的 **SalesTerritoryKey** 列之间的关系，如下图所示。 这可以从 SSMS 中完成，方法是右键单击“DimUserSecurity”表，选择“设计”。 然后从菜单中选择“表设计器”->“关系...”。
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/createusersecuritytable_keys.png)
3. 保存表，然后向该表中添加几行用户信息，为此，可再次右键单击“DimUserSecurity”表然后选择“编辑前 200 行”。 在添加这些用户后，**DimUserSecurity** 表的行类似于下图中所示︰
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/createusersecuritytable_users.png)
   
   我们会在即将开始的任务中重新使用这些用户。
4. 接下来，我们在 **DimSalesTerritory** 表中执行*内部联接*，其中显示了与用户关联的区域详细信息。 下面的代码可执行*内部联接*，之后的图显示了在*内部联接*成功后的表显示方式。
   
       select b.SalesTerritoryCountry, b.SalesTerritoryRegion, a.EmployeeID, a.FirstName, a.LastName, a.UserName from [dbo].[DimUserSecurity] as a join  [dbo].[DimSalesTerritory] as b on a.[SalesTerritoryID] = b.[SalesTerritoryKey]
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/createusersecuritytable_join_users.png)
5. 请注意，上图显示了诸如销售区域的负责用户等信息。 由于我们已在**步骤 2** 中创建关系，所以会显示此数据。 另请注意，用户 **Jon Doe 属于澳大利亚销售区域**。 我们会在即将执行的步骤和任务中再度讨论 John Doe。

## <a name="task-2-create-the-tabular-model-with-facts-and-dimension-tables"></a>任务 2：创建含事实数据表和维度表的表格模型
1. 在准备好关系数据仓库后，即可定义您的表格模型。 可以使用 **SQL Server Data Tools (SSDT)** 创建该模型。 有关如何定义表格模型的详细信息，请参阅[创建新的表格模型项目](https://msdn.microsoft.com/library/hh231689.aspx)。
2. 将所有必需表导入模型，如下所示。
   
    ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/ssdt_model.png)
3. 在导入必需的表之后，您需要定义一个名为 **SalesTerritoryUsers**的具有**读取**权限的角色。 这可以通过在 SQL Server Data Tools 中单击**模型**菜单然后单击**角色**来实现。 在**角色管理器**对话框中，单击**新建**。
4. 在**角色管理器**中的**成员**选项卡下，添加我们已在**任务 1-第 3 步**中在 **DimUserSecurity** 表中定义的用户。
   
    ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/rolemanager.png)
5. 接下来，为 **DimSalesTerritory** 和 **DimUserSecurity** 表添加适当的函数，如下面的**行筛选器**选项卡下所示。
   
    ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/rolemanager_complete.png)
6. 在此步骤中，我们使用 **LOOKUPVALUE** 函数返回列的值，在其中 Windows 用户名与 **USERNAME** 函数所返回的用户名相同。 然后，可将查询限制为满足以下条件的情况：**LOOKUPVALUE** 返回的值与相同或相关表中的值相匹配。 在 **DAX 筛选器**列中，键入以下公式︰
   
       =DimSalesTerritory[SalesTerritoryKey]=LOOKUPVALUE(DimUserSecurity[SalesTerritoryID], DimUserSecurity[UserName], USERNAME(), DimUserSecurity[SalesTerritoryID], DimSalesTerritory[SalesTerritoryKey])
    在此公式中，**LOOKUPVALUE** 函数将返回 **DimUserSecurity[SalesTerritoryID]** 列的所有值，其中，**DimUserSecurity[UserName]** 与当前登录的 Windows 用户名相同，**DimUserSecurity[SalesTerritoryID]** 与 **DimSalesTerritory[SalesTerritoryKey]** 相同。
   
    > [!IMPORTANT]
    > 请注意，在使用行级别安全性时，不支持使用 DAX 函数 [USERELATIONSHIP](https://msdn.microsoft.com/query-bi/dax/userelationship-function-dax)。

   接着，**LOOKUPVALUE** 返回的 Sales SalesTerritoryKey 集将用于限制 **DimSalesTerritory** 中所示的行。 将仅显示 **SalesTerritoryKey** 属于 **LOOKUPVALUE** 函数所返回的 ID 集的行。
8. 对于“DimUserSecurity”表，在“DAX 筛选器”列中键入以下公式：
   
       =FALSE()

    此公式指定所有列均解析为 false 布尔条件；因此，**DimUserSecurity** 表没有可查询的列。
1. 现在，我们需要处理并部署该模型。 如需在部署该模型时获得帮助，可以参考[部署文章](https://msdn.microsoft.com/library/hh231693.aspx)。

## <a name="task-3-adding-data-sources-within-your-on-premises-data-gateway"></a>任务 3：在本地数据网关中添加数据源
1. 表格模型部署完毕，可供使用后，需要向 Power BI 门户中的本地 Analysis Services 表格服务器添加数据源连接。
2. 若要允许 Power BI 服务访问本地分析服务，需要在环境中安装并配置[本地数据网关](service-gateway-onprem.md)。
3. 正确配置本地数据网关后，需要为 **Analysis Services** 表格实例创建一个数据源连接。 本文将帮助你[在 Power BI 门户中添加数据源](service-gateway-enterprise-manage-ssas.md)。
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/pbi_gateway.png)
4. 完成上一个步骤后，网关便已配置完成，并且可与本地 Analysis Services 数据源交互。

## <a name="task-4-creating-report-based-on-analysis-services-tabular-model-using-power-bi-desktop"></a>任务 4：使用 Power BI Desktop 基于 Analysis Services 表格模型创建报表
1. 启动 **Power BI Desktop** 并选择“获取数据”>“数据库”。
2. 从数据源列表中选择“SQL Server Analysis Services 数据库”，然后选择“连接”。
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/getdata.png)
3. 填写 **Analysis Services** 表格实例详细信息，然后选择“实时连接”。 选择**确定**。 使用 **Power BI** 时，动态安全性仅适用于**实时连接**。
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/getdata_connectlive.png)
4. 你会发现模型已部署在 Analysis Services 实例中。 选择相应的模型并选择“确定”。
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/getdata_connectlive.png)
5. **Power BI Desktop** 现在在画布右侧的“字段”窗格中显示所有可用字段。
6. 在右侧的“字段”窗格中，从“FactInternetSales”表中选择“SalesAmount”度量值，从“SalesTerritory”表中选择“SalesTerritoryRegion”维度。
7. 我们将让此报表看上去简单明了，因此现在不会再添加任何列。 为了让数据的表示形式更有意义，我们将可视化效果更改为“环形图”。
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/donut_chart.png)
8. 等报表准备就绪后，你就可以将它直接发布到 Power BI 门户。 从 **Power BI Desktop** 的“主页”功能区中选择“发布”。

## <a name="task-5-creating-and-sharing-a-dashboard"></a>任务 5：创建和共享仪表板
1. 你已经在 **Power BI Desktop** 中创建了报表，并且单击了“发布”，因此，该报表将发布到 **Power BI** 服务中。 由于它已在该服务中，因此，可以使用在前述步骤中创建的示例来演示我们的模型安全性方案。
   
   在**销售经理 Sumit** 的角色中，他可以看到所有不同销售区域的数据。 因此，他创建此报表（在前面的任务步骤中创建的报表），并将其发布到 Power BI 服务。
   
   发布报表后，他便在 Power BI 服务中基于该报表创建一个名为 **TabularDynamicSec** 的仪表板。 在下图中，请注意销售经理 Sumit 可以看到所有销售区域的对应数据。
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/donut_chart_1.png)
2. 现在，Sumit 与他的同事 Jon Doe 共享此仪表板，Jon Doe 负责澳大利亚地区的销售。
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/user_jon_doe.png)
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/pbi_dashboard.png)
3. 当 Jon Doe 登录到 **Power BI** 服务并查看 Sumit 创建的共享仪表板时，他应该**只能**看到自己所负责的区域的销售额。 因此，当 Jon Doe 登录并访问 Sumit 共享给他的仪表板时，他**只能**看到澳大利亚地区的销售额。
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/dashboard_jon_doe.png)
4. 祝贺你！ **Power BI** 服务中已成功反映并显示本地 **Analysis Services** 表格模型中定义的动态行级别安全性。 Power BI 使用 **effectiveusername** 属性将当前 Power BI 用户凭据发送到本地数据源，以运行查询。

## <a name="task-6-understanding-what-happens-behind-the-scenes"></a>任务 6：了解幕后发生了什么
1. 此任务假定你熟悉 SQL 事件探查器，因为你需要捕获本地 SSAS 表格实例上的 SQL Server 事件探查器踪迹。
2. 只要用户（本例中为 Jon Doe）访问 Power BI 服务中的仪表板，会话就会初始化。 你会发现，**salesterritoryusers** 角色立即生效，有效用户名为 **<EffectiveUserName>jondoe@moonneo.com</EffectiveUserName>**
   
       <PropertyList><Catalog>DefinedSalesTabular</Catalog><Timeout>600</Timeout><Content>SchemaData</Content><Format>Tabular</Format><AxisFormat>TupleFormat</AxisFormat><BeginRange>-1</BeginRange><EndRange>-1</EndRange><ShowHiddenCubes>false</ShowHiddenCubes><VisualMode>0</VisualMode><DbpropMsmdFlattened2>true</DbpropMsmdFlattened2><SspropInitAppName>PowerBI</SspropInitAppName><SecuredCellValue>0</SecuredCellValue><ImpactAnalysis>false</ImpactAnalysis><SQLQueryMode>Calculated</SQLQueryMode><ClientProcessID>6408</ClientProcessID><Cube>Model</Cube><ReturnCellProperties>true</ReturnCellProperties><CommitTimeout>0</CommitTimeout><ForceCommitTimeout>0</ForceCommitTimeout><ExecutionMode>Execute</ExecutionMode><RealTimeOlap>false</RealTimeOlap><MdxMissingMemberMode>Default</MdxMissingMemberMode><DisablePrefetchFacts>false</DisablePrefetchFacts><UpdateIsolationLevel>2</UpdateIsolationLevel><DbpropMsmdOptimizeResponse>0</DbpropMsmdOptimizeResponse><ResponseEncoding>Default</ResponseEncoding><DirectQueryMode>Default</DirectQueryMode><DbpropMsmdActivityID>4ea2a372-dd2f-4edd-a8ca-1b909b4165b5</DbpropMsmdActivityID><DbpropMsmdRequestID>2313cf77-b881-015d-e6da-eda9846d42db</DbpropMsmdRequestID><LocaleIdentifier>1033</LocaleIdentifier><EffectiveUserName>jondoe@moonneo.com</EffectiveUserName></PropertyList>
3. 基于有效用户名请求，Analysis Services 在查询本地 Active Directory 后将请求转换为真实的 moonneo\jondoe 凭据。 Analysis Services 从 Active Directory 获取真实凭据后，就会基于用户对数据的访问权限和其他权限仅返回用户对其具有权限的数据。
4. 如果使用仪表板执行更多活动，例如，如果 Jon Doe 从仪表板转到基础报表，则可以在 SQL 事件探查器中看到作为 DAX 查询返回到 Analysis Services 表格模型的特定查询。
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/profiler1.png)
5. 你还可以从下面看到正在执行该 DAX 查询以填充报表数据。
   
   ```
   EVALUATE
     ROW(
       "SumEmployeeKey", CALCULATE(SUM(Employee[EmployeeKey]))
     )
   
   <PropertyList xmlns="urn:schemas-microsoft-com:xml-analysis">``
             <Catalog>DefinedSalesTabular</Catalog>
             <Cube>Model</Cube>
             <SspropInitAppName>PowerBI</SspropInitAppName>
             <EffectiveUserName>jondoe@moonneo.com</EffectiveUserName>
             <LocaleIdentifier>1033</LocaleIdentifier>
             <ClientProcessID>6408</ClientProcessID>
             <Format>Tabular</Format>
             <Content>SchemaData</Content>
             <Timeout>600</Timeout>
             <DbpropMsmdRequestID>8510d758-f07b-a025-8fb3-a0540189ff79</DbpropMsmdRequestID>
             <DbPropMsmdActivityID>f2dbe8a3-ef51-4d70-a879-5f02a502b2c3</DbPropMsmdActivityID>
             <ReturnCellProperties>true</ReturnCellProperties>
             <DbpropMsmdFlattened2>true</DbpropMsmdFlattened2>
             <DbpropMsmdActivityID>f2dbe8a3-ef51-4d70-a879-5f02a502b2c3</DbpropMsmdActivityID>
           </PropertyList>
   ```

## <a name="considerations"></a>注意事项
使用行级别安全性、SSAS 和 Power BI 时需要牢记几个注意事项：

1. Power BI 的本地行级别安全性只能用于实时连接。
2. 通过“实时连接”访问报表的用户可在 Power BI 服务中立即获得处理模型后的任何数据更改。

