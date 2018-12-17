---
title: 在 Power BI Desktop 中进行双向交叉筛选
description: 在 Power BI Desktop 中使用 DirectQuery 启用交叉筛选
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 12/06/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 89ee11efab495d55457e265e654972aac941d50c
ms.sourcegitcommit: 72c9d9ec26e17e94fccb9c5a24301028cebcdeb5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/07/2018
ms.locfileid: "53025318"
---
# <a name="bidirectional-cross-filtering-using-directquery-in-power-bi-desktop"></a>在 Power BI Desktop 中使用 DirectQuery 启用双向交叉筛选

筛选表创建相应数据视图时，报表创建者（和数据建模者）会在确定如何将筛选应用于报表时面临挑战；表的筛选上下文只处于关系的一方，另一方却没有，并且通常需要复杂的 DAX 公式来获取所需结果。

使用双向交叉筛选，报表创建者（和数据建模者）对于使用相关表时如何应用筛选有了更好的掌控，使这些筛选能够应用于表关系的两方。 此操作可通过让筛选上下文传播到表关系另一方的第二个相关表来完成。

## <a name="detailed-whitepaper-for-bidirectional-cross-filtering"></a>双向交叉筛选的详细白皮书
有关详细信息，请参阅此[白皮书](http://download.microsoft.com/download/2/7/8/2782DF95-3E0D-40CD-BFC8-749A2882E109/Bidirectional%20cross-filtering%20in%20Analysis%20Services%202016%20and%20Power%20BI.docx)，该白皮书对 Power BI Desktop 中的双向交叉筛选进行了详细说明（还介绍了 SQL Server Analysis Services 2016，两者都具有相同的行为）。

* 下载[ Power BI Desktop 的双向交叉筛选](http://download.microsoft.com/download/2/7/8/2782DF95-3E0D-40CD-BFC8-749A2882E109/Bidirectional%20cross-filtering%20in%20Analysis%20Services%202016%20and%20Power%20BI.docx)白皮书

## <a name="enabling-bidirectional-cross-filtering-for-directquery"></a>启用 DirectQuery 的双向交叉筛选

若要启用交叉筛选，在关系的“编辑关系”对话框中，必须选择以下项：

* “交叉筛选方向”必须设置为“双向”
* 还必须选择“应用双向安全筛选器”

  ![](media/desktop-bidirectional-filtering/bidirectional-filtering_2.png)

> [!NOTE]
> 在 Power BI Desktop 中创建交叉筛选 DAX 公式时，请使用 UserPrincipalName（通常与用户登录名相同，如 joe@contoso.com）而不是 UserName。 正因如此，你可能需要创建一个可将 *UserName* （或 EmployeeID）映射到 *UserPrincipalName* 的相关表。

有关详细信息以及双向交叉筛选工作方式的示例，请查看本文前面部分提及的[白皮书](http://download.microsoft.com/download/2/7/8/2782DF95-3E0D-40CD-BFC8-749A2882E109/Bidirectional%20cross-filtering%20in%20Analysis%20Services%202016%20and%20Power%20BI.docx)。

