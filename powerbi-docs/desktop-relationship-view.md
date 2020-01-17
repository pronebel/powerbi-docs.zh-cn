---
title: Power BI Desktop 中的关系视图
description: Power BI Desktop 中的关系视图
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: cd9671b8c38cb2aa1502c3aa00a871d125f819b1
ms.sourcegitcommit: 97597ff7d9ac2c08c364ecf0c729eab5d59850ce
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/09/2020
ms.locfileid: "75760471"
---
# <a name="work-with-relationship-view-in-power-bi-desktop"></a>使用 Power BI Desktop 中的关系视图
**关系视图**显示模型中的所有表、列和关系。 这在模型包含许多表且其关系十分复杂时尤其有用。

让我们来看一下。

![](media/desktop-relationship-view/relationshipview_fullscreen.png)

**A.**  关系视图图标 – 单击可显示关系视图中的模型

**B.** 关系 – 可以将光标悬停在关系上方以显示所用列。 双击关系以在“编辑关系”  对话框中将其打开。 

在上图中，你可以看到 *商店* 表中有一个*StoreKey* 列与 *销售额* 表中的 *StoreKey* 列相关。 我们可以看到这是*多对一* (\*:1) 关系，线中间的图标指出交叉筛选器方向设置为*两者*。 图标上的箭头表示筛选上下文流的方向。

有关关系的详细信息，请参阅[在 Power BI Desktop 中创建和管理关系](desktop-create-and-manage-relationships.md)。

