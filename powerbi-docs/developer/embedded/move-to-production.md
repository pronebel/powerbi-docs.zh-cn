---
title: 将 Power BI 嵌入式分析应用程序移动到生产环境以增强嵌入式 BI 见解
description: 了解将 Power BI 应用程序移动到生产环境所需的步骤。 使用 Power BI 嵌入式分析改进嵌入式 BI 见解。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
ms.topic: tutorial
ms.service: powerbi
ms.subservice: powerbi-developer
ms.custom: seodec18
ms.date: 06/02/2020
ms.openlocfilehash: 71eff0f09c0e34ffd8789f1b56347d754b6589bc
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/05/2021
ms.locfileid: "97886663"
---
# <a name="move-your-embedded-app-to-production"></a>将嵌入式应用移动到生产环境

完成应用程序的开发之后，接下来请回到工作区了解容量。

> [!Important]
> 必须向所有工作区（包含报表或仪表板的工作区以及包含数据集的工作区）分配容量。

## <a name="create-a-capacity"></a>创建容量

通过创建容量，可以利用好客户的资源。 有两种类型的容量可供选择：

* **Power BI Premium** - 租户级别的 Microsoft 356 订阅，可在两个 SKU 系列（EM 和 P）中使用 。嵌入 Power BI 内容时，此解决方案称为“Power BI 嵌入”。 有关此订阅的详细信息，请参阅[什么是 Power BI Premium？](../../admin/service-premium-what-is.md)

* **Azure Power BI Embedded** - 可以从 [Microsoft Azure 门户](https://portal.azure.com)购买容量。 此订阅使用 A SKU。 有关如何创建 Power BI Embedded 容量的详细信息，请参阅[在 Azure 门户中创建 Power BI Embedded 容量](azure-pbie-create-capacity.md)。

    > [!NOTE]
    > 使用 A SKU 时，无法使用免费的 Power BI 许可证访问 Power BI 内容。

### <a name="capacity-specifications"></a>容量规范

下表介绍每个 SKU 的资源和限制。 若要确定最能满足你需求的容量，请参阅[应该为我的方案购买哪一个 SKU](./embedded-faq.md#which-solution-should-i-choose) 表。

| 容量节点 | 总虚拟核心 | 后端 V 核心 | RAM (GB) | 前端 V 核心 | DirectQuery/Live Connection（每秒） | 模型刷新并行度 |
| --- | --- | --- | --- | --- | --- | --- |
| EM1/A1 | 1 | 0.5 | 2.5 | 0.5 | 3.75 | 1 |
| EM2/A2 | 2 | 1 | 5 | 1 | 7.5 | 2 |
| EM3/A3 | 4 | 2 | 10 | 2 | 15 | 3 |
| P1/A4 | 8 | 4 | 25 | 4 | 30 | 6 |
| P2/A5 | 16 | 8 | 50 | 8 | 60 | 12 |
| P3/A6 | 32 | 16 | 100 | 16 | 120 | 24 |
| | | | | | | |

## <a name="development-testing"></a>开发测试

对于开发测试，你可将嵌入试用令牌用于 Pro 许可证。 若要嵌入到生产环境，请使用容量。

Power BI 服务主体或主用户（主帐户）可以生成的嵌入试用令牌的数量是有限的 。 使用 [Available Features](/rest/api/power-bi/availablefeatures/getavailablefeatures) API 来检查当前嵌入使用情况的百分比。 显示了每个服务主体或主帐户的使用量。

如果测试时用完了嵌入令牌，则需要购买 Power BI Embedded 或高级[容量](embedded-capacity.md)。 为容量生成嵌入令牌时，可生成的数量不受限制。

## <a name="assign-a-workspace-to-a-capacity"></a>将工作区分配到容量

创建容量后，可将工作区分配给该容量。

所有包含与嵌入内容（包括数据集、报表和仪表板）相关的 Power BI 资源的工作区都必须分配给容量。 例如，如果嵌入的报表以及与其绑定的数据集位于不同工作区中，则必须将这两个工作区分配给容量。

### <a name="assign-a-workspace-to-a-capacity-using-a-service-principal"></a>使用服务主体为工作区分配容量

若要使用[服务主体](embed-service-principal.md)将容量分配给工作区，请使用 [Power BI REST API](/rest/api/power-bi/capacities/groups_assigntocapacity)。 使用 Power BI REST API 时，请务必使用[服务主体对象 ID](embed-service-principal.md)。

### <a name="assign-a-workspace-to-a-capacity-using-a-master-user"></a>使用主用户为工作区分配容量

请按照以下步骤，使用主用户将容量分配给工作区。

1. 在 Power BI 服务中打开工作区，选择 

1. 在“Power BI 服务”中，展开工作区并针对要嵌入内容的工作区选择相应省略号。 然后选择“编辑工作区”。

    >[!div class="mx-imgBorder"]
    >:::image type="content" source="media/move-to-production/workspace-settings.png" alt-text="显示 Power B I 服务门户中的工作区设置菜单的屏幕截图。":::

2. 选择“高级”选项卡，然后执行以下操作：

    * 启用“容量”。

    * 选择你创建的容量。

    * 选择“保存”。

    >[!div class="mx-imgBorder"]
    >:::image type="content" source="media/move-to-production/premium-tab.png" alt-text="显示 Power B I 服务门户中的工作区“高级设置”选项卡的屏幕截图。":::

    为工作区分配容量后，它旁边会出现一个菱形 

    >[!div class="mx-imgBorder"]
    >:::image type="content" source="media/move-to-production/premium-workspace.png" alt-text="显示 Power B I 服务门户中具有高级容量的屏幕截图。":::

## <a name="next-steps"></a>后续步骤

>[!div class="nextstepaction"]
>[Power BI 嵌入式分析中的容量和 SKU](embedded-capacity.md)

>[!div class="nextstepaction"]
>[Power BI 嵌入式分析中的容量计划](embedded-capacity-planning.md)

>[!div class="nextstepaction"]
>[生成嵌入令牌的注意事项](generate-embed-token.md)