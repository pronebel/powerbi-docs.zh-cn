---
title: 如何开发 Power BI 自定义视觉对象的疑难解答
description: 本文介绍了开发或创建自定义 Power BI 视觉对象时可能会遇到的一些常见问题。
author: sranins
ms.author: rasala
manager: kfile
ms.reviewer: maghan
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 11/06/2018
ms.openlocfilehash: cbda8cca80c32056f06788e53540d7f2d6ed972d
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "61421762"
---
# <a name="troubleshoot-power-bi-custom-visuals"></a>Power BI 自定义视觉对象疑难解答

## <a name="debug"></a>调试

**找不到 Pbiviz 命令（或类似错误）**

在终端的命令行运行 `pbiviz` 时，可以看到帮助屏幕。 如果未看到，则未正确安装。 请确保至少安装了 NodeJS 4.0。

在“可视化效果”选项卡中找不到调试视觉对象 

在“可视化效果”  选项卡中“调试视觉对象”看上去像一个提示图标。

![视觉对象选项](media/power-bi-custom-visuals-troubleshoot/powerbi-developer-visual-selection.png)

如果看不到它，请确保已经在 Power BI 设置中启用了它。

> [!NOTE]
> 目前，调试视觉对象仅可用于 Power BI 服务，不可用于 Power BI Desktop 或移动应用。 打包后的视觉对象仍可用于任何地方。

**无法联系视觉对象服务器**

在终端的命令行中从视觉对象项目的根目录使用命令 `pbiviz start` 运行视觉对象服务器。 如果服务器未运行，则可能是未正确安装 SSL 证书。

请随时联系自定义视觉对象支持团队： *pbicvsupport@microsoft.com*  可咨询任何相关问题或提供反馈意见。

## <a name="next-steps"></a>后续步骤

有关详细信息，请访问[关于 Power BI 自定义视觉对象的常见问题解答](power-bi-custom-visuals-faq.md#organizational-custom-visuals)。
