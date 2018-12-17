---
title: 磁贴错误故障排除
description: 磁贴尝试在 Power BI 中刷新时可能遇到的常见错误
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 12/06/2018
ms.author: davidi
LocalizationGroup: Troubleshooting
ms.openlocfilehash: d03bf92331d1536337cfb8279c182822630c6c80
ms.sourcegitcommit: 72c9d9ec26e17e94fccb9c5a24301028cebcdeb5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/07/2018
ms.locfileid: "53025023"
---
# <a name="troubleshooting-tile-errors"></a>磁贴错误故障排除
下面是使用磁贴可能会遇到的常见错误以及错误说明。

> [!NOTE]
> 如果遇到上文未列出的错误，且产生了相应的问题，可通过[社区网站](http://community.powerbi.com/)寻求进一步的支持，或者可以创建[支持票证](https://powerbi.microsoft.com/support/)。
> 
> 

## <a name="errors"></a>错误
**Power BI 加载模型时遇到意外错误。请稍后再试。**
或**无法检索数据模型。请联系仪表板所有者，确保数据源和模型存在并且可访问。**

我们无法访问你的数据，因为数据源不可访问。 如果数据源已删除、重命名、移动、脱机或权限已更改，则可能会发生这种情况。 确认源是否仍处于我们指向的位置，你是否仍有权访问该源。 如果这不是问题，可能是源速度比较慢。 请稍后在源上的负载较小时重试。 如果是本地源，数据源所有者可以提供详细信息。

**你没有权限查看此磁贴或打开该工作簿。**

请联系仪表板所有者，确保数据源和模型存在并且你的帐户可以访问。

**数据形状必须至少包含一个输出数据的组或计算。请联系仪表板所有者。**

我们没有任何数据要显示，因为查询为空。 请尝试将字段列表中的某些字段添加到你的可视化对象中并重新固定。

**无法显示数据，因为 Power BI 无法确定两个或多个字段之间的关系。**

正在尝试使用不相关的表中的两个或多个字段。 你需要从可视化对象中删除不相关的字段，然后创建表之间的关系。 完成此操作后，你可以将字段添加回可视化对象。 这可在 Power BI Desktop 或 Power Pivot for Excel 中完成。 [了解详细信息](desktop-create-and-manage-relationships.md)

**主坐标轴和辅助坐标轴中的组重叠。主坐标轴中的组拥有的密钥不能与辅助坐标轴中的组拥有的相同。**

这通常是暂时性问题。 当将组从行中移动到列中时，通常会发生这种情况。 在这种情况下，移动完所有组后，该错误应该会消失。 如果你仍看到此消息，请尝试在行和列或者轴图例之间切换字段或者从可视化对象中删除字段。  

**此可视化对象已超出可用资源。请尝试进行筛选以减少显示的数据量。**

你的可视化对象尝试查询的数据太多，无法通过可用资源完成结果。 请尝试筛选可视化对象以减少结果中的数据量。

**我们无法识别以下字段：{0}。请使用数据集中存在的字段更新可视化对象。**

该字段可能已删除或被重命名。 可以从可视化对象中删除中断的字段，添加不同的字段，并重新固定该字段。

**无法检索该可视化对象的数据。请稍后再试。**

这通常是暂时性问题。 如果你稍后再试，仍看到此消息，请与支持部门联系。

## <a name="contact-support"></a>与支持部门联系
如果你仍然有问题，请[与支持部门联系](https://support.powerbi.com)做进一步调查。

## <a name="next-steps"></a>后续步骤
[本地数据网关故障排除](service-gateway-onprem-tshoot.md)  
[Power BI Personal Gateway 故障排除](service-admin-troubleshooting-power-bi-personal-gateway.md)  
更多问题？ [尝试参与 Power BI 社区](http://community.powerbi.com/)

