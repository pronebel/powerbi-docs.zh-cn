---
title: Power BI 分页报表中的子报表
description: 本文将介绍 Power BI 服务中分页报表支持的数据源，以及如何连接到 Azure SQL 数据库数据源。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 04/29/2020
ms.openlocfilehash: 784e3fd3883adb9fc5b773cc730b992135d7ef8b
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/13/2020
ms.locfileid: "83272801"
---
# <a name="subreports-in-power-bi-paginated-reports"></a>Power BI 分页报表中的子报表

子报表是在主分页报表的表体中显示其他分页报表的分页报表项  。 从概念上说，报表中的子报表类似于网页中的框架。 子报表用于在报表中嵌入另一个报表。 你可以使用任何报表作为子报表。 可以将显示为子报表的报表存储在与父报表相同的 Premium 工作区中。 您可以设计父报表，以便向子报表传递参数。 可以在数据区域中重复子报表，并使用参数在子报表的每个实例中筛选数据。  
  
 ![分页报表中的子报表](media/subreports/paginated-report-subreport.png "分页报表子报表")  
  
 在此图中，显示在 Sales Order 主报表中的联系人信息实际上来自于 Contacts 子报表。  
  
你可以在 Power BI Report Builder 中创建和修改分页报表定义 (.rdl) 文件。 可以将 SQL Server Reporting Services 中存储的子报表上传到 Power BI 服务中的 Premium 工作区。 需要将主报表和子报表发布到同一个工作区。 安装 [Power BI Report Builder](https://go.microsoft.com/fwlink/?linkid=2086513)。
  
## <a name="work-with-report-builder-and-the-power-bi-service"></a>结合使用 Report Builder 和 Power BI 服务

Power BI Report Builder 可以与计算机上的分页报表（称为本地报表）结合使用，也可以与 Power BI 服务上的报表结合使用。  首次打开 Report Builder 时，系统将要求你登录到 Power BI 帐户。 如果没有，请在右上角选择“登录”  。

:::image type="content" source="media/subreports/report-builder-sign-in.png" alt-text="登录 Power BI":::

登录后，你将在 Power BI Report Builder 中看到“Power BI 服务”选项，此选项代表“文件”菜单上的“打开”和“另存为”选项     。 选择“Power BI 服务”选项保存报表时，将在 Power BI Report Builder 和 Power BI 服务之间创建实时连接  。 

:::image type="content" source="media/subreports/report-builder-subreport-open-service.png" alt-text="从 Power BI 服务打开":::

## <a name="save-a-local-report-to-the-power-bi-service"></a>将本地报表保存到 Power BI 服务

在你可以将子报表添加到主报表之前，你需先创建这两个报表并将其保存到同一个 Power BI Premium 工作区。 

1. 要打开现有的本地报表，请在“文件”菜单中，选择“打开” > “此电脑”，然后选择 .rdl 文件    。  

2. 在“文件”菜单上，选择“另存为” > “Power BI 服务”    。  有关详细信息，请参阅[将分页报表发布到 Power BI 服务](paginated-reports-save-to-power-bi-service.md)。

    > [!NOTE]
    > 还可以从 Power BI 服务开始上传报表。 有关详细信息，也请参阅[将分页报表发布到 Power BI 服务](paginated-reports-save-to-power-bi-service.md)。

3. 在“另存为”对话框中，选择可用于存储分页报表的 Power BI Premium 工作区  。  Premium 工作区在其名称旁边有一个菱形图标 ![Premium 菱形图标](media/subreports/report-builder-premium-diamond.png)。

    :::image type="content" source="media/subreports/report-builder-subreport-save-as-service.png" alt-text="Power BI 服务的“另存为”":::

4. 选择“保存”。 

## <a name="add-a-subreport-to-a-report"></a>将子报表添加到报表

将两个报表保存到 Premium 工作区之后，接下来即可将其中一个报表作为子报表添加到另一个报表中。 可通过两种方法添加子报表。 

1. 在“插入”功能区中，选择“子报表”按钮，或右键单击报表画布，然后选择“插入” > “子报表”     。

    :::image type="content" source="media/subreports/report-builder-insert-subreport.png" alt-text="在报表中插入子报表":::

    随即将打开“子报表属性”对话框  。  

2. 选择“浏览”按钮，导航到要用作子报表的报表，然后在“名称”文本框中指定子报表的名称   。

3. 根据需要配置其他属性，包括[参数](#use-parameters-in-subreports)。

## <a name="use-parameters-in-subreports"></a>在子报表中使用参数  
 若要将参数从父报表传递给子报表，请在用作子报表的报表中定义报表参数。 在父报表中放入子报表时，您可以选择报表参数以及要从父报表传递给子报表中的报表参数的值。  
  
> [!NOTE]  
> 从子报表中选择的参数是报表参数，而不是查询参数   。  
  
 可以将子报表放入报表的表体或数据区域中。 如果将子报表放在数据区域中，则子报表将重复数据区域中的组或行的每个实例。 可以将组或行中的值传递到子报表。 在子报表值属性中，对于包含要传递给子报表参数的值的字段，请使用字段表达式。  
  
 如需详细了解如何使用参数和子报表，请参阅 SQL Server Reporting Services 文档中的 [添加子报表和参数](https://docs.microsoft.com/sql/reporting-services/report-design/add-a-subreport-and-parameters-report-builder-and-ssrs)。  

## <a name="preview-paginated-reports-in-report-builder"></a>在 Report Builder 中预览分页报表

可在 Report Builder 中预览报表。

- 从“开始”功能区选择“运行”   。 

由于 Report Builder 是一种设计工具，因此，在其中预览报表看上去可能与在 Power BI 服务中呈现报表有所不同。

### <a name="notes-about-previewing"></a>有关预览的说明

- Report Builder 不会存储报表中使用的数据源的凭据。  Report Builder 在预览期间要求提供每组凭据。  
- 如果报表数据源位于本地，则需要在将报表保存到 Power BI 工作区后配置网关。
- 如果 Report Builder 在预览过程中遇到错误，它将返回一般消息。  如果错误很难调试，请考虑在 Power BI 服务中呈现报表。  

## <a name="considerations"></a>注意事项

### <a name="maintaining-the-connection"></a>保持连接

关闭文件时，Report Builder 不会保持与 Power BI 的连接。  可以处理本地主报表，它的子报表存储在 Power BI 工作区中。 请确保先将主报表保存到 Power BI 工作区之后，再关闭该报表。  否则，可能会在预览期间收到“找不到”消息，因为未与 Power BI 服务保持实时连接。  在这种情况下，请前往子报表并选择其属性。  从 Power BI 服务再次打开子报表。  这将重新建立连接，并且所有其他子报表都应正常运行。

### <a name="renaming-a-subreport"></a>重命名子报表

如果在工作区中重命名子报表，则需要修复主报表中的名称引用。 否则，子报表将不会呈现。 主报表仍将呈现，并且在子报表项内显示错误消息。

## <a name="migrate-large-reports"></a>迁移大型报表

如果要将大型报表迁移到 Power BI，请考虑使用 [RdlMigration 工具](../guidance/migrate-ssrs-reports-to-power-bi.md)。  RdlMigration 工具已更新，可处理重复的子报表名。  如果两个或多个报表具有相同的名称，但位于不同的子目录中，则可能会出现重复的子报表名。  如果这些名称未解析为唯一名称，则仅识别第一个子报表。

如果要使用 Report Builder 迁移大型报表，建议先处理子报表。 将每个子报表保存到 Power BI 工作区，防止出现任何重复的报表名。

## <a name="share-reports-with-subreports"></a>与子报表共享报表

我们已提到过，主报表和子报表必须位于同一个工作区中。 否则，子报表将不会呈现。 共享主报表时，还需要共享子报表。 如果在应用中共享主报表，请确保在该应用中还包含子报表。 如果你将主报表直接与用户或用户组共享，请确保还与该用户或用户组共享每个子报表。
  
## <a name="next-steps"></a>后续步骤

[排除 Power BI 分页报表中的子报表故障](subreports-troubleshoot.md)

[在 Power BI 服务中查看分页报表](../consumer/paginated-reports-view-power-bi-service.md)

更多问题？ [尝试参与 Power BI 社区](https://community.powerbi.com/)
