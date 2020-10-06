---
title: 使用 Microsoft Intune 配置移动应用
description: 如何使用 Microsoft Intune 配置 Power BI 移动应用。 这包括如何添加和部署应用程序。 以及如何创建移动应用程序策略以控制安全性。
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 09/25/2020
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: 214ef5072808decc4c153a28cf231e070c20508d
ms.sourcegitcommit: d153cfc0ce559480c53ec48153a7e131b7a31542
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/29/2020
ms.locfileid: "91524710"
---
# <a name="configure-mobile-apps-with-microsoft-intune"></a>使用 Microsoft Intune 配置移动应用

Microsoft Intune 使组织可以管理设备和应用程序。 iOS 版和 Android 版 Power BI 移动应用与 Intune 集成。 借助此集成，用户可以管理设备上的应用，并控制安全性。 通过配置策略，可以控制各项配置，如要求提供访问 PIN、应用如何处理数据，甚至包括在无法使用应用时加密应用数据。

Microsoft Power BI 移动应用允许你访问重要的业务信息。 你可以查看你的组织的所有托管设备和应用业务数据的仪表板和报表并与之交互。 有关支持的 Intune 应用的详细信息，请参阅 [Microsoft Intune 保护的应用](/intune/apps/apps-supported-intune-apps)。

## <a name="general-mobile-device-management-configuration"></a>常规移动设备管理配置

本文假定 Intune 配置正确，并且你向 Intune 注册了设备。 本文并是完整的 Microsoft Intune 配置指南。 若要详细了解 Intune，请参阅[什么是 Intune？](/intune/introduction-intune/)。

Microsoft Intune 可以在 Microsoft 365 中与移动设备管理 (MDM) 共存。 如果使用的是 MDM，则设备将显示为已在 MDM 中注册，但可供在 Intune 中管理。

Intune 管理员必须将 Power BI 应用添加到 Intune，同时将应用分配给最终用户，然后，最终用户才能在其设备上使用应用。

> [!NOTE]
> 当你配置 Intune 后，iOS 或 Android 设备上的 Power BI 移动应用便会禁用后台数据刷新。 Power BI 在你进入应用时刷新 Power BI 服务网页版中的数据。

## <a name="step-1-add-the-power-bi-app-to-intune"></a>步骤 1：将 Power BI 应用添加到 Intune

若要将 Power BI 应用添加到 Intune，请使用以下主题中提供的步骤：
- [将 iOS 应用商店应用添加到 Microsoft Intune](/intune/apps/store-apps-ios)
- [将 Android 应用商店应用添加到 Microsoft Intune](/intune/apps/store-apps-android)

## <a name="step-2-assign-the-app-to-your-end-users"></a>步骤 2：将应用分配给最终用户

将 Power BI 应用添加到 Microsoft Intune 后，可以将应用分配给用户和设备。 请务必注意，无论设备是否由 Intune 管理，你都可以将应用分配给设备。

若要将 Power BI 应用分配给用户和设备，请按照[使用 Microsoft Intune 将应用分配给组](/intune/apps/apps-deploy)中提供的步骤进行操作。

## <a name="step-3-create-and-assign-app-protection-policies"></a>步骤 3：创建和分配应用保护策略

应用保护策略 (APP) 是可确保组织数据在托管应用中保持安全或受到控制的规则。 策略可以是在用户尝试访问或移动“公司”数据时强制执行的规则，或在用户位于应用内时受到禁止或监视的一组操作。 受管理应用是一种自身执行应用保护策略的应用，可由 Intune 管理。

借助移动应用管理 (MAM) 应用保护策略，可以管理和保护应用程序内的组织数据。 通过无需注册的 MAM (MAM-WE)，可以在几乎任何设备上管理包含敏感数据的工作或学校相关应用，包括自带设备办公 (BYOD) 场景下的个人设备。 有关详细信息，请参阅[应用保护策略概述](/intune/apps/app-protection-policy)。

若要为 Power BI 应用创建和分配应用保护策略，请使用[如何创建和分配应用保护策略](/intune/apps/app-protection-policies)中提供的步骤。

## <a name="step-4-use-the-application-on-a-device"></a>步骤 4：在设备上使用应用程序

公司支持人员可对托管应用进行配置，以帮助保护在该应用中可访问的公司数据。 当你在设备上的托管应用中访问公司数据时，你可能会注意到应用的工作方式与你的预期稍有不同。 例如，你可能无法复制和粘贴受保护的公司数据，或者你可能无法将该数据保存到特定位置。

若要了解最终用户可以如何在其设备上使用 Power BI 应用，请查看以下文章中提供的步骤：
- [在 iOS 设备上使用托管应用](https://docs.microsoft.com/intune-user-help/use-managed-apps-on-your-device-ios#how-do-i-get-managed-apps)
- [在 Android 设备上使用托管应用](https://docs.microsoft.com/intune-user-help/use-managed-apps-on-your-device-android)

## <a name="next-steps"></a>后续步骤

[如何创建和分配应用保护策略](/intune/app-protection-policies) 

[适用于移动设备的 Power BI 应用](../consumer/mobile/mobile-apps-for-mobile-devices.md)  

更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)  
