---
title: 在报表中的表或矩阵中显示图像
description: 在 Power BI Desktop 中，创建包含指向图像的超链接的列。 然后，在 Power BI Desktop 或 Power BI 服务中，将这些超链接添加到报告表、矩阵、切片器或多行卡片，以显示图像。
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.custom: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/11/2019
ms.author: maggies
LocalizationGroup: Visualizations
ms.openlocfilehash: 2ebbc277f2a269ebaf2d1bdb99f1aa800576b466
ms.sourcegitcommit: ba085b248c54e8fb1fd8eb2bb23a814e3fdd7ff6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70936484"
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

[将静态形状、文本框和图像添加到报表](https://docs.microsoft.com/power-bi/guided-learning/visualizations?tutorial-step=11)

[Power BI 服务中设计器的基本概念](service-basic-concepts.md)

更多问题？ [尝试参与 Power BI 社区](http://community.powerbi.com/)

