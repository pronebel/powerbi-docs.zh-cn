---
title: 第三方服务：Google Analytics 连接器
description: 第三方服务：适用于 Power BI Desktop 的 Google Analytics 连接器
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 05/08/2019
LocalizationGroup: Connect to data
ms.openlocfilehash: 383f69bd371e4b0f635ff2b64c7fae0523c360e4
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/01/2020
ms.locfileid: "96392257"
---
# <a name="use-the-google-analytics-connector-for-power-bi-desktop"></a>使用适用于 Power BI Desktop 的 Google Analytics 连接器
> [!NOTE]
> Power BI Desktop 中的 Google Analytics 内容包和连接器依赖于 Google Analytics Core Reporting API。 同样，功能和可用性可能会随着时间推移有所不同。

可以使用 **Google Analytics（分析）** 连接器连接 Google Analytics（分析）数据。 若要连接，请执行以下步骤：

1. 在 **Power BI Desktop** 中，选择“**主页**”功能区选项卡中的“**获取数据**”。
2. 在“获取数据”窗口中，从左侧窗格的类别中选择“联机服务”。
3. 从右侧窗格中的选择中选择 **Google Analytics**。
4. 在窗口底部，选择 **连接**。  
   ![“开始”选项卡的屏幕截图，其中显示了已选中“Google Analytics”的“获取数据”功能区和“连接”按钮。](media/service-google-analytics-connector/tps_googleanalytics_1.png)

你将看到一个提示对话框，说明连接器是一种第三方服务，并警告功能和可用性可能会随着时间推移有所不同，以及其他说明。  
![“连接”对话框的屏幕截图，其中显示了连接器依赖于第三方服务的警告。](media/service-google-analytics-connector/tps_googleanalytics_2.png)

选择“**继续**”后，系统会提示你登录 Google Analytics（分析）。  
![Google Analytics 提示的屏幕截图，其中显示了你需要登录才能进行连接。](media/service-google-analytics-connector/tps_googleanalytics_3.png)

当你输入凭据时，系统会提示你希望你脱机访问 Power BI。 这便是如何使用 **Power BI Desktop** 访问 Google Analytics（分析）数据。  

接受后，**Power BI Desktop** 会立即显示你当前已登录。  
![Google Analytics 提示的屏幕截图，其中显示了你已登录。](media/service-google-analytics-connector/tps_googleanalytics_5.png)

选择“**连接**”后，你的 Google Analytics（分析）数据会与 **Power BI Desktop** 连接并加载。  
![“加载”对话框的屏幕截图，其中显示了 Google Analytics 数据已连接并正在加载。](media/service-google-analytics-connector/tps_googleanalytics_6.png)

## <a name="changes-to-the-api"></a>API 的更改
尽管我们尝试依照任何更改发布更新，API 可能会以影响我们生成的查询的结果的方式进行更改。 在某些情况下，某些查询可能不再受支持。 由于此依赖关系，使用此连接器时，我们无法保证你的查询的结果。

有关 Google Analytics API 的更改的详细信息可在[更改日志](https://developers.google.com/analytics/devguides/changelog)中找到。

