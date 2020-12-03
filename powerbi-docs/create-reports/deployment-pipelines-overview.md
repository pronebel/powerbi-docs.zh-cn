---
title: 部署管道概述
description: 了解什么是 Power BI 中的部署管道
author: KesemSharabi
ms.author: kesharab
ms.topic: conceptual
ms.service: powerbi
ms.subservice: pbi-deployment
ms.custom: contperfq1
ms.date: 10/21/2020
ms.openlocfilehash: 1f094f762c87f9b35433a5572f2b30e7f020fbe4
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/01/2020
ms.locfileid: "96414981"
---
# <a name="introduction-to-deployment-pipelines"></a>部署管道简介

在当今世界，分析是在几乎每个组织中做出决策的重要部分。 随着 Power BI 作为分析工具的不断使用，它需要使用更多的数据，从而看上去具有吸引力并且具备用户友好性。 尽管如此，Power BI 都需要始终可用且可靠。 为了满足这些要求，BI 创建者必须有效地协作。

借助部署管道工具，BI 创建者能够管理组织内容的生命周期。 对于具有高级容量的企业的创建者，此工具非常高效并且可以重复使用。 借助部署管道，创建者可以在用户使用 Power BI 内容之前开发和测试此内容。 内容类型包括报表、仪表板和数据集。

该工具设计为具有三个阶段的管道：

* <a name="development"></a>开发
    
    此阶段用于与其他创作者一起设计、生成和上传新内容。 这是部署管道中的第一个阶段。

* <a name="test"></a>测试

    在对内容进行所需的所有更改之后，即可进入测试阶段。 上传修改后的内容，以便系统可以将其移动到此测试阶段。 以下三个示例说明了在测试环境中可以执行的操作：

    * 与测试人员和审阅者共享内容

    * 加载和运行包含大量数据的测试

    * 测试应用以查看其向最终用户呈现的外观

* <a name="production"></a>生产

    在测试内容后，使用生产阶段与组织内的业务用户共享内容的最终版本。

![已填充所有三个阶段（开发、测试和生产）的工作部署管道的屏幕截图。](media/deployment-pipelines-overview/deployment-pipelines.png)

## <a name="next-steps"></a>后续步骤

>[!div class="nextstepaction"]
>[开始使用部署管道](deployment-pipelines-get-started.md)

>[!div class="nextstepaction"]
>[了解部署管道过程](deployment-pipelines-process.md)

>[!div class="nextstepaction"]
>[解决部署管道问题](deployment-pipelines-troubleshooting.md)

>[!div class="nextstepaction"]
>[部署管道最佳实践](deployment-pipelines-best-practices.md)
