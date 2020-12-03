---
title: 如何在 Power BI 中应用敏感度标签
description: 了解如何在 Power BI 中应用敏感度标签
author: paulinbar
ms.author: painbar
ms.service: powerbi
ms.subservice: powerbi-eim
ms.topic: how-to
ms.date: 08/16/2020
LocalizationGroup: Data from files
ms.openlocfilehash: 07b9ae9522437500da1386974548f420dc0cc1c5
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/01/2020
ms.locfileid: "96413371"
---
# <a name="how-to-apply-sensitivity-labels-in-power-bi"></a>如何在 Power BI 中应用敏感度标签

报表、仪表板、数据集和数据流的 Microsoft 信息保护敏感度标签可以保护敏感内容免遭未经授权的数据访问和泄露。 使用敏感度标签正确标记数据，可确保只有经过授权的用户才能访问数据。 本文介绍如何向你的内容应用敏感度标签。

要能够在 Power BI 中应用敏感度标签，你需要满足以下条件：
* 必须具有 Power BI Pro 许可证，并对要应用标签的内容拥有编辑权限。
* 必须在具有应用敏感度标签权限的安全组内，如标题为[在 Power BI 中启用敏感度标签](./service-security-enable-data-sensitivity-labels.md)的文章中所述。
* 必须满足所有[授权和其他要求](./service-security-enable-data-sensitivity-labels.md#licensing-and-requirements)。

有关 Power BI 中敏感度标签的详细信息，请参阅 [Power BI 中的敏感度标签](service-security-sensitivity-label-overview.md)。

## <a name="applying-sensitivity-labels"></a>应用敏感度标签

在租户上启用数据保护后，将在仪表板、报表、数据集和数据流列表视图中的敏感度列显示敏感度标签。

![启用敏感度标签](media/service-security-apply-data-sensitivity-labels/apply-data-sensitivity-labels-01.png)

**在报表或仪表板上应用或更改敏感度标签**
1. 单击“其他选项(…)”。
1. 选择“设置”。
1. 在“设置”侧窗格中，选择相应的敏感度标签。
1. 保存设置。

下图演示了在报表上执行这些操作的步骤

![设置敏感度标签](media/service-security-apply-data-sensitivity-labels/apply-data-sensitivity-labels-02.png)

**在数据集或数据流上应用或更改敏感度标签**

1. 单击“其他选项(…)”。
1. 选择“设置”。
1. 在“设置”侧窗格中，选择相应的敏感度标签。
1. 应用设置。

以下两张图片演示了在数据集上执行这些操作的步骤。

依次选择“其他选项(…)”和“设置” 。

![打开数据集设置](media/service-security-apply-data-sensitivity-labels/apply-data-sensitivity-labels-05.png)

在“设置”页面上，打开“敏感度标签”部分，选择所需的敏感度标签，然后单击“应用”。

![选择敏感度标签](media/service-security-apply-data-sensitivity-labels/apply-data-sensitivity-labels-06.png)

## <a name="removing-sensitivity-labels"></a>删除敏感度标签
若要从报表、仪表板、数据集或数据流中删除敏感度标签，请按照[用于应用标签的相同过程](#applying-sensitivity-labels)操作，但在系统提示对数据的敏感度进行分类时，请选择“(无)”。 

## <a name="considerations-and-limitations"></a>注意事项和限制

有关 Power BI 中的敏感度标签限制的列表，请参阅 [Power BI 中的敏感度标签](service-security-sensitivity-label-overview.md#limitations)。

## <a name="next-steps"></a>后续步骤

本文介绍如何在 Power BI 中应用敏感度标签。 以下文章提供了有关 Power BI 中的数据保护的进一步详细信息。 

* [Power BI 中的敏感度标签概述](./service-security-sensitivity-label-overview.md)
* [在 Power BI 中启用敏感度标签](./service-security-enable-data-sensitivity-labels.md)
* [在 Power BI 中使用 Microsoft Cloud App Security 控件](./service-security-using-microsoft-cloud-app-security-controls.md)