---
title: 服务主体创建应用
description: 服务主体创建应用
services: powerbi
author: KesemSharabi
ms.author: kesharab
ms.topic: include
ms.date: 10/15/2020
ms.custom: include file
ms.openlocfilehash: 0f6c74ddc5a7decc8c1a6444568de44d3adbbc68
ms.sourcegitcommit: 8561902ef0ad63b0881187a22f25d1aa1ec3bcbc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/20/2020
ms.locfileid: "92210915"
---
## <a name="step-2---create-an-azure-ad-security-group"></a>第 2 步 - 创建 Azure AD 安全组

服务主体无权访问你的任何 Power BI 内容和 API。 若要向服务主体授予访问权限，请在 Azure AD 中创建安全组，并将创建的服务主体添加到此安全组中。

创建 Azure AD 安全组有以下两种方法：
* 手动（在 Azure 中）
* 使用 PowerShell

### <a name="create-a-security-group-manually"></a>手动创建安全组

若要手动创建 Azure 安全组，请按照[使用 Azure Active Directory 创建基本组并添加成员](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal)一文中的说明操作。 

### <a name="create-a-security-group-using-powershell"></a>使用 PowerShell 创建安全组

下面的示例脚本用于新建安全组，并向此安全组中添加应用程序。

>[!NOTE]
>若要为整个组织启用服务主体访问权限，请跳过这一步。

```powershell
# Required to sign in as admin
Connect-AzureAD

# Create an Azure AD security group
$group = New-AzureADGroup -DisplayName <Group display name> -SecurityEnabled $true -MailEnabled $false -MailNickName notSet

# Add the service principal to the group
Add-AzureADGroupMember -ObjectId $($group.ObjectId) -RefObjectId $($sp.ObjectId)
```

## <a name="step-3---enable-the-power-bi-service-admin-settings"></a>第 3 步 - 启用 Power BI 服务管理设置

为了让 Azure AD 应用程序能够访问 Power BI 内容和 API，Power BI 管理员必须在 Power BI 管理门户中启用服务主体访问权限。

在“开发人员设置”中，将你在 Azure AD 中创建的安全组添加到特定安全组部分。

>[!IMPORTANT]
>服务主体有权访问为其启用的任何租户设置。 这包括特定安全组或整个组织，具体视管理设置而定。
>
>若要限制服务主体只能访问特定租户设置，请只允许访问特定安全组。 也可以为服务主体创建专用安全组，并将它排除在相应租户设置之外。

>[!div class="mx-imgBorder"]
>:::image type="content" source="../developer/embedded/media/embed-service-principal/admin-portal.png" alt-text="显示 Power BI 门户的“管理”选项中的开发人员设置的屏幕截图。":::

## <a name="step-4---add-the-service-principal-to-your-workspace"></a>第 4 步 - 将服务主体添加到工作区

若要让 Azure AD 应用程序能够访问 Power BI 服务中的项目（如报表、仪表板和数据集），请以成员或管理员身份将服务主体实体添加到工作区。

>[!NOTE]
>此部分提供了 UI 说明。 也可以使用[“组 - 添加组用户”API](/rest/api/power-bi/groups/addgroupuser) 将服务主体添加到工作区。

1. 滚动到要能够访问的工作区，然后选择“更多”菜单中的“工作区访问”。

    :::image type="content" source="../developer/embedded/media/embed-service-principal/workspace-access.png" alt-text="显示 Power BI 门户的“管理”选项中的开发人员设置的屏幕截图。":::

2. 以管理员或成员身份将服务主体添加到工作区。

    :::image type="content" source="../developer/embedded/media/embed-service-principal/add-service-principal-in-the-UI.png" alt-text="显示 Power BI 门户的“管理”选项中的开发人员设置的屏幕截图。":::