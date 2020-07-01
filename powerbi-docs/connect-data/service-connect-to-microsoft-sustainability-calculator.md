---
title: 连接 Microsoft Sustainability Calculator
description: 适用于 Power BI 的 Microsoft Sustainability Calculator
author: joshthor3222
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: how-to
ms.date: 01/06/2020
ms.author: v-tikid
LocalizationGroup: Connect to services
ms.openlocfilehash: cffb7ecc195f5ce803ec2dfc81c794bac75c9448
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85230013"
---
# <a name="connect-the-microsoft-sustainability-calculator"></a>连接 Microsoft Sustainability Calculator
深入了解 IT 基础结构的碳排放量，以做出更可持续的计算决策

Microsoft Sustainability Calculator 提供有关与 Azure 服务关联的碳排放量数据的新见解。 负责在组织内进行报告和推动可持续发展的人员现在可以量化每个 Azure 订阅的碳排放量，还可以查看在 Azure 与本地数据中心中运行这些工作负荷所带来的估计碳减量。 此数据可用于作用域 3 排放量的温室气体报告。 访问 Microsoft Sustainability Calculator 将需要你的租户 ID 和访问密钥，通常可通过组织的 Azure 管理员获得。

若要使用此应用，你将需要 Azure Enterprise 门户中的信息。 你企业的系统管理员可以帮助你获取此信息。 安装应用之前，请查看这些说明并获取所需的信息。 

此版本的连接器仅支持来自 [https://ea.azure.com](https://ea.azure.com/) 的企业合约。 目前尚不支持中国合约。

## <a name="how-to-connect"></a>如何连接
[!INCLUDE [powerbi-service-apps-get-more-apps](../includes/powerbi-service-apps-get-more-apps.md)]

1. 选择“Microsoft Sustainability Calculator”\>“立即获取”。
1. 在“安装此 Power BI 应用?”中，选择“安装” 。
1. 在“应用”窗格中，选择“Microsoft Sustainability Calculator”磁贴 。
1. 在“开始使用新应用”中，选择“连接” 。

    ![开始使用新应用](media/service-connect-to-zendesk/power-bi-new-app-connect-get-started.png)

1. 输入“公司名称”、“用户注册编号”和“月数” **\>“登录”。** 请参阅下面有关[查找这些参数](#finding-parameters)的详细信息。

    ![公司注册](media/service-connect-to-microsoft-sustainability-calculator/company-enrollment.png)

1. 对于“身份验证方法”，选择“密钥”，对于“隐私级别”，选择“组织”   。
1. 对于“密钥”，输入“访问密钥”\>“登录” 。

    ![访问密钥条目](media/service-connect-to-microsoft-sustainability-calculator/access-key-entry.png)

1. 导入过程会自动开始。 导入完成后，在导航窗格中将会出现新的仪表板、报表和模型。 选择报表，查看已导入的数据。

## <a name="finding-parameters"></a>查找参数

若要查找公司“注册 ID”和“访问密钥”，请与 Azure 管理员联系以获取所需的信息 。 你的管理员将

1. 登录到 [Azure Enterprise 门户](https://ea.azure.com)，然后单击左侧功能区上的“管理”，并按如下所示获取“注册编号” 
2. 在 [Azure Enterprise 门户](https://ea.azure.com)上，依次单击“报表”和“API 访问密钥”，并按如下所示获取主注册帐户密钥

## <a name="using-the-app"></a>使用应用

若要随时更新参数，请导航到“数据集”设置，访问与应用工作区关联的数据，并更新租户 ID、公司名称或月份数据。 应用参数后，单击“刷新”以通过应用新参数重新加载数据。