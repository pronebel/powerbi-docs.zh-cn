---
title: 磁贴错误故障排除
description: 磁贴尝试在 Power BI 中刷新时可能遇到的常见错误
author: mgblythe
ms.reviewer: kayu
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: troubleshooting
ms.date: 12/06/2018
ms.author: mblythe
LocalizationGroup: Troubleshooting
ms.openlocfilehash: dbae4c82fb350242ed0fefadeeec217666fc3005
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2019
ms.locfileid: "73877504"
---
# <a name="troubleshooting-tile-errors"></a>磁贴错误故障排除
下面是使用磁贴可能会遇到的常见错误以及错误说明。

> [!NOTE]
> 如果遇到上文未列出的错误，且产生了相应的问题，可通过[社区网站](https://community.powerbi.com/)寻求进一步的支持，或者可以创建[支持票证](https://powerbi.microsoft.com/support/)。
> 
> 

## <a name="errors"></a>错误
**Power BI 加载模型时遇到意外错误。请稍后再试。**
或**无法检索数据模型。请联系仪表板所有者，确保数据源和模型存在并且可访问。**

我们无法访问你的数据，因为数据源不可访问。 如果数据源已删除、重命名、移动、脱机或权限已更改，则可能出现此问题。 确认源是否仍处于我们指向的位置，你是否仍有权访问该源。 如果这不是问题，可能是源速度比较慢。 请稍后在源上的负载较小时重试。 如果是本地源，数据源所有者可以提供详细信息。

**你没有权限查看此磁贴或打开该工作簿。**

联系仪表板所有者，确保数据源和模型存在并且你的帐户可以访问。

自定义视觉对象已由管理员禁用  。

Power BI 管理员已禁用组织或安全组的自定义视觉对象。 将无法从 [Microsoft 市场](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals)使用自定义视觉对象或从文件导入专用视觉对象。 将仅能够使用预先打包的一组视觉对象。


**数据形状必须至少包含一个输出数据的组或计算。请联系仪表板所有者。**

我们没有任何数据要显示，因为查询为空。 请尝试将字段列表中的某些字段添加到你的可视化对象中并重新固定。

**无法显示数据，因为 Power BI 无法确定两个或多个字段之间的关系。**

正在尝试使用不相关的表中的两个或多个字段。 你需要从可视化对象中删除不相关的字段，然后创建表之间的关系。 完成此更改后，可以将字段添加回视觉对象。 这可在 Power BI Desktop 或 Power Pivot for Excel 中完成。 [了解详细信息](desktop-create-and-manage-relationships.md)

**主坐标轴和辅助坐标轴中的组重叠。主坐标轴中的组拥有的密钥不能与辅助坐标轴中的组拥有的相同。**

这通常是暂时性问题。 当将组从行中移动到列中时，通常会发生这种情况。 在这种情况下，移动完所有组后，该错误应该会消失。 如果你仍看到此消息，请尝试在行和列或者轴图例之间切换字段或者从可视化对象中删除字段。  

**此可视化对象已超出可用资源。请尝试进行筛选以减少显示的数据量。**

你的可视化对象尝试查询的数据太多，无法通过可用资源完成结果。 请尝试筛选可视化对象以减少结果中的数据量。

**我们无法识别以下字段：{0}。请使用数据集中存在的字段更新可视化对象。**

该字段可能已删除或被重命名。 可以从可视化对象中删除中断的字段，添加不同的字段，并重新固定该字段。

**无法检索该可视化对象的数据。请稍后再试。**

这通常是暂时性问题。 如果稍后再试，仍看到此消息，请与支持部门联系。

**启用单一登录 (SSO) 后，磁贴将继续显示未筛选的数据。**

如果将基础数据集配置为使用 DirectQuery 模式，或通过本地数据网关实时连接到分析服务，则可能会发生这种情况。 在这种情况下，在为数据源启用 SSO 后，磁贴将继续显示未筛选的数据，直到应发生下次磁贴刷新。 进行下次磁贴刷新时，Power BI 根据配置使用 SSO，磁贴显示根据用户标识筛选的数据。 

如果要立即看到筛选后的数据，可以通过选择仪表板右上角的“更多选择”(...) 并选择“刷新仪表板磁贴”来强制进行磁贴刷新   。

作为数据集所有者，还可以更改磁贴刷新频率，将其设置为 15 分钟以加速磁贴刷新。 选择 Power BI 服务右上角的“齿轮”  图标，然后选择“设置”。 在“设置”页上，选择“数据集”选项卡   。展开“计划的缓存刷新”  并更改“刷新频率”  。 在 Power BI 执行下次磁贴刷新后，请务必将配置重置为原始刷新频率。

> [!NOTE]
> “计划的缓存刷新”  部分仅适用于 DirectQuery/LiveConnection 模式下的数据集。 导入模式下的数据集不需要单独的磁贴刷新，因为磁贴会在下一次计划的数据刷新过程中自动刷新。

## <a name="contact-support"></a>与支持部门联系
如果仍有问题，请[与支持部门联系](https://support.powerbi.com)做进一步调查。

## <a name="next-steps"></a>后续步骤
[本地数据网关故障排除](service-gateway-onprem-tshoot.md)  
[Power BI Personal Gateway 故障排除](service-admin-troubleshooting-power-bi-personal-gateway.md)  
更多问题？ [尝试参与 Power BI 社区](https://community.powerbi.com/)

