---
title: 在报表中的表或矩阵中显示图像
description: 在 Power BI Desktop 中，创建包含指向图像的超链接的列。 然后，在 Power BI Desktop 或 Power BI 服务中，将这些超链接添加到报告表、矩阵、切片器或多行卡片，以显示图像。
author: maggiesMSFT
ms.reviewer: ''
ms.custom: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 09/11/2019
ms.author: maggies
LocalizationGroup: Visualizations
ms.openlocfilehash: 098bb6cc8df59dea38bb63f38c724e362c7219e5
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85228974"
---
# <a name="display-images-in-a-table-matrix-or-slicer-in-a-report"></a>在报表中的表、矩阵或切片器中显示图像

改进报表的一个好方法是向报表添加图像。 页面上的静态图像适用于某些用途。 但有时你想要与报表中数据相关的图像。 本主题将介绍如何在标、矩阵、切片器或多行卡片中显示图像。 

![表中的 URL 图像](media/power-bi-images-tables/power-bi-url-images-table.png)

## <a name="add-images-to-your-report"></a>将图像添加到报表

1. 创建包含图像 URL 的列。 有关要求的信息，请参阅本文后面的[注意事项](#considerations)。

1. 选择此列。 在“建模”功能区上，为“数据类别”选择“图像 URL”。   

    ![将“数据类别”设置为“图像 URL”](media/power-bi-images-tables/power-bi-set-url-image.png)

1. 将此列添加到表、矩阵、切片器或多行卡片。

    ![包含图像的切片器](media/power-bi-images-tables/power-bi-url-images-slicer.png)

## <a name="considerations"></a>注意事项

- 图像必须是以下文件格式之一：.bmp、.jpg、.jpeg、.gif、.png 或 .svg
- URL 必须可以匿名访问，未位于需要登录的站点上，如 SharePoint。 但是，如果图像托管在 SharePoint 或 OneDrive 上，你能够获取直接指向它们的嵌入代码。 


## <a name="next-steps"></a>后续步骤

[页面布局和格式设置](/learn/modules/visuals-in-power-bi/12-formatting)

[Power BI 服务中设计器的基本概念](../fundamentals/service-basic-concepts.md)

更多问题？ [尝试参与 Power BI 社区](https://community.powerbi.com/)
