---
title: Power BI Desktop 中的关系视图
description: Power BI Desktop 中的关系视图
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 6f855ff38d7c3f82fe4fa0456deb8a22ce6379e0
ms.sourcegitcommit: 2ae660a7b70fce23eb58b159d049eca44a664f2c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/30/2018
ms.locfileid: "52669902"
---
# <a name="relationship-view-in-power-bi-desktop"></a>Power BI Desktop 中的关系视图
**关系视图**显示模型中的所有表、列和关系。 当模型中包含许多关系十分复杂的表时尤其有用。

让我们来看一下。

![](media/desktop-relationship-view/relationshipview_fullscreen.png)

**A.**  关系视图图标 – 单击可显示关系视图中的模型

**B.** 关系 – 可以将光标悬停在关系上方以显示所用列。 双击关系以在“编辑关系”对话框中将其打开。 

在上图中，你可以看到 *商店* 表中有一个与 *销售额* 表（其中同样含有 *StoreKey* 列）相关的 *StoreKey* 列。 我们可以看到这是*多对一* (\*:1) 关系，线中间的图标指出交叉筛选器方向设置为*两者*。 图标上的箭头表示筛选上下文流的方向。

有关关系的详细信息，请参阅[在 Power BI Desktop 中创建和管理关系](desktop-create-and-manage-relationships.md)。

