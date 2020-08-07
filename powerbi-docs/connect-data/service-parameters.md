---
title: 在 Power BI 服务中编辑参数设置
description: 查询参数需使用 Power BI Desktop 创建，但可在 Power BI 服务中进行查看和更新
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 08/04/2020
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: 3b64c1dd502fd16199fbff9f64cd2c017006d1f1
ms.sourcegitcommit: a7227f6d3236e6e0a7bc1f83ff6099b5cd58bff3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2020
ms.locfileid: "87768465"
---
# <a name="edit-parameter-settings-in-the-power-bi-service"></a>在 Power BI 服务中编辑参数设置
报表创建者将查询参数添加到 Power BI Desktop 中的报表。 报表创建者可使用参数根据一个或多个参数“值”将报表组成多个部分  。 例如，报表创建者可创建参数，将数据限制到单个国家/地区，或使用参数来限制字段（例如日期、时间和文本）可接受的格式。

![Desktop 中显示“管理参数”选项的“开始”选项卡](media/service-parameters/power-bi-manage-parameters.png)

## <a name="review-and-edit-parameters-in-power-bi-service"></a>使用 Power BI 服务查看和编辑参数

报表创建者可在 Power BI Desktop 中定义参数。 [将该报表发布到 Power BI 服务](../create-reports/desktop-upload-desktop-files.md)时，参数设置和选择会随其移动。 可以在 Power BI 服务中查看和编辑参数设置，但不能创建参数设置。

1. 在 Power BI 服务中，选择齿轮图标 ![齿轮图标](media/service-parameters/power-bi-cog.png) 打开“设置”。

2. 选择“数据集”  选项卡并突出显示列表中的数据集。 
    
    ![选中了“数据集”选项卡的“设置”窗口](media/service-parameters/power-bi-select-dataset2.png)

3. 展开参数  。  如果所选数据集没有参数，则将看到一条消息，其中带有指向“了解有关查询参数的详细信息”的链接。 如果数据集具有参数，则展开“参数”标题会显示这些参数。 

    ![参数已展开的“设置”窗口](media/service-parameters/power-bi-settings.png)

    查看参数设置，并根据需要进行更改。 灰显字段是不可编辑的内容。 


## <a name="next-steps"></a>后续步骤
添加简单参数的一个特别方法是[修改 URL](../collaborate-share/service-url-filters.md)。
