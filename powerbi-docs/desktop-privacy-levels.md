---
title: 了解 Power BI Desktop 隐私级别
description: Power BI Desktop 隐私级别
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: reference
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 4c522a9e6c40f4164ee82675c40c3110b174d017
ms.sourcegitcommit: 10a87c016f497dbeba32f94ed1f3688a70816fea
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/09/2019
ms.locfileid: "65513944"
---
# <a name="power-bi-desktop-privacy-levels"></a>Power BI Desktop 隐私级别
在 **Power BI Desktop** 中，隐私级别指定隔离级别，该隔离级别定义一个数据源与其他数据源的隔离程度。 尽管严格的隔离级别能阻止数据源之间的信息交换，但也可能降低功能和影响性能。

可通过选择“**文件 > 选项和设置 > 选项**”，然后选择“**当前文件 > 隐私**”找到“**隐私级别**”设置。该设置确定 Power BI Desktop 合并数据时是否使用你的隐私级别设置。 此对话框包含指向 Power BI Desktop 有关隐私级别和隐私级别（本文）的文档的链接。

![](media/desktop-privacy-levels/desktop_privacylevels1.png)

## <a name="configure-a-privacy-level"></a>配置隐私级别
使用隐私级别设置，你可以指定隔离级别，该隔离级别定义一个数据源必须与其他数据源隔离的程度。

| 设置 | 说明 | 示例数据源 |
| --- | --- | --- |
| **私有数据源** |**隐私**数据源包含敏感或机密信息，并且数据源的查看权限可能仅限于授权用户。 隐私数据源与其他数据源完全隔离。 |Facebook 数据、包含股票奖励的文本文件或包含员工查看信息的工作簿。 |
| **组织数据源** |**组织**数据源将数据源的可见性限制为仅受信任的人员组。 **组织**数据源与所有**公共**数据源隔离，但对于其他**组织**数据源可见。 |位于受信任的 intranet SharePoint 站点，向受信任的组启用了权限的 **Microsoft Word** 文档。 |
| **公共数据源** |**公共**数据源给予每个人对数据源中包含的数据的查看权限。 只有文件、Internet 数据源或工作簿数据可以标记为“公共”。 |来自 Microsoft Azure 市场的免费数据、来自维基百科页的数据或包含从公共网页复制的数据的本地文件。 |

## <a name="configure-privacy-level-settings"></a>配置隐私级别设置
每个数据源的“隐私”设置对话框可在“文件”>“选项和设置”>“数据源设置”中找到。

若要配置数据源的隐私级别，请选择数据源，然后选择**编辑**。 **数据源设置**对话框出现时，你可以从对话框底部的下拉菜单中选择适当的隐私级别，如下图所示。

![](media/desktop-privacy-levels/desktop_privacylevels2.png)

> [!CAUTION]
> 应将包含高度敏感或机密数据的数据源配置为“隐私”。
> 

## <a name="configure-privacy-levels"></a>配置隐私级别
**隐私级别**是一种设置，默认情况下它被设置为**根据每个源的隐私级别设置合并数据**，这表示**隐私级别**未启用。

| 设置 | 说明 |
| --- | --- |
| **根据每个源的隐私级别设置合并数据**（处于打开状态且为默认设置） |隐私级别设置用于确定合并数据时数据源的隔离级别。 |
| **忽略隐私级别并潜在地提高性能**（处于关闭状态） |合并数据时不考虑隐私级别，可能会提高数据的性能和功能。 |

> **安全说明：** 通过选择“隐私级别”对话框中的“忽略隐私级别并潜在地提高性能”来启用“隐私级别”，可能会向未经授权的人员泄露敏感或机密数据。 除非确信数据源不包含敏感或机密数据，否则请不要启用**隐私级别**。
> 
> 

> [!CAUTION]
> Power BI 服务不支持“忽略隐私级别并可能会提升性能”。 因此，如果将启用此设置的 Power BI Desktop 报表发布到 Power BI 服务，不要在服务中使用它时反映这种行为。
> 

**配置隐私级别**

在 Power BI Desktop 或在查询编辑器中，选择**文件 > 选项和设置 > 选项**然后选择**当前文件 > 隐私**。

a. 当选择**根据每个源的隐私级别设置合并数据**时，数据将根据你的隐私级别设置进行合并。 跨隐私隔离区域合并数据会导致某些数据缓冲。

b. 当选择**忽略隐私级别并潜在地提高性能**时，数据合并时将忽略隐私级别，这可能会向未经授权的用户泄漏敏感或机密数据。 该设置可能会提高性能和功能。

> **安全说明：** 选择“忽略隐私级别并潜在地提高性能”可能会提高性能；不过，Power BI Desktop 不能保证合并到 Power BI Desktop 文件中的数据的隐私。
> 
> 

