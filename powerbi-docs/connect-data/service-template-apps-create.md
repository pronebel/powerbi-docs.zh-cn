---
title: 在 Power BI 中创建模板应用
description: 如何在 Power BI 中创建可以分发给任何 Power BI 客户的模板应用。
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: how-to
ms.date: 09/15/2020
ms.author: painbar
ms.openlocfilehash: e3b6ada10138e6964240c5eb5c53399507170b79
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90860661"
---
# <a name="create-a-template-app-in-power-bi"></a>在 Power BI 中创建模板应用

Power BI 模板应用使 Power BI 合作伙伴能够在极少编码或没有编码的情况下生成 Power BI 应用，并将它们部署到任何 Power BI 客户。  本文包含创建 Power BI 模板应用的分步说明。

如果可以创建 Power BI 报表和仪表板，那么你可成为模板应用构建者，可以生成分析内容并将其打包到“应用”中 。 可以通过任何可用平台（例如 AppSource）或者通过在自己的 Web 服务中使用应用，将应用部署其他 Power BI 租户。 作为构建者，可以创建受保护的分析包以进行分发。

Power BI 租户管理员管理和控制组织中谁可以创建模板应用，以及谁可以安装它们。 获得授权的这些用户可以安装模板应用，然后对其进行修改并将其分发给组织中的 Power BI 使用者。

## <a name="prerequisites"></a>先决条件

下面是生成模板应用的要求：  

- 一个 [Power BI Pro 许可证](../fundamentals/service-self-service-signup-for-power-bi.md)
- [安装 Power BI Desktop](../fundamentals/desktop-get-the-desktop.md)（可选）
- 熟悉 [Power BI 的基本概念](../fundamentals/service-basic-concepts.md)
- 公开共享模板应用的权限（有关详细信息，请参阅 Power BI [管理门户的模板应用设置](../admin/service-admin-portal.md#template-apps-settings)）

## <a name="create-the-template-workspace"></a>创建模板工作区

若要创建可以分发给其他 Power BI 租户的模板应用，需要在一个新的工作区中创建它。

1. 在 Power BI 服务中，选择“工作区” > “创建工作区” 。

    ![创建工作区](media/service-template-apps-create/power-bi-new-workspace.png)

2. 在“创建工作区”中，为工作区输入名称、说明（可选）和徽标图像（可选）。

    ![请试用新的工作区](media/service-template-apps-create/power-bi-upgrade-new.png)

4. 展开“高级”部分，然后选择“开发模板应用”********。

    ![开发模板应用](media/service-template-apps-create/power-bi-template-app-develop.png)

5. 选择“保存”。
>[!NOTE]
>需要 Power BI 管理员授权才能提升模板应用。

## <a name="add-content-to-the-template-app-workspace"></a>向模板应用工作区添加内容

与常规 Power BI 工作区一样，下一步是向工作区添加内容。  

- 在工作区中[创建 Power BI 内容](index.yml)。

如果在 Power Query 中使用参数，请确保这些参数具有明确定义的类型（例如 Text）。 不支持 Any 和 Binary 类型。

在[有关在 Power BI 中创作模板应用的提示](service-template-apps-tips.md)中，可找到为模板应用创建报表和仪表板时要考虑的一些建议。

## <a name="define-the-properties-of-the-template-app"></a>定义模板应用的属性

现在工作区中已有内容，即可将其打包到模板应用中。 第一步是创建一个测试模板应用，只能从租户的组织内部访问。

1. 在模板应用工作区中，选择“创建应用”****。

    ![创建应用](media/service-template-apps-create/power-bi-create-app.png)

    此处，可以在六个选项卡中为模板应用填写其他构建选项：

    **品牌打造**

    ![品牌打造](media/service-template-apps-create/power-bi-create-branding.png)
    - 应用程序名称
    - 说明
    - 支持网站（将模板应用重新分发为组织应用后，应用信息下会显示链接）
    - 应用徽标（文件大小限不超过 45K，1:1 纵横比，.png、.jpg、.jpeg 格式）
    - 应用主题颜色

    **导航**

    激活“新导航生成器”，可在其中定义应用的导航窗格（有关详细信息，请参阅本文中的[设计导航体验](../collaborate-share/service-create-distribute-apps.md#design-the-navigation-experience)）。

   ![设置应用登陆页面](media/service-template-apps-create/power-bi-install-app-content.png)
    
    应用登陆页面：如果决定选择退出导航生成器，则可以选择应用登陆页面。 将报表或仪表板定义为应用的登陆页面。 使用可以给人留下正确印象的登陆页面。

    **控制**

    对应用的用户设置有关应用内容的限制。 可以使用此控件来保护应用中的知识产权。

    ![控制](media/service-template-apps-create/power-bi-create-control.png)

    >[!NOTE]
    >安装应用的用户始终无法导出为 .pbix 格式。

    **参数**

    在原始 pbix 文件中创建参数（了解有关[创建查询参数](https://powerbi.microsoft.com/blog/deep-dive-into-query-parameters-and-power-bi-templates/)的详细信息）。 可使用此选项卡上的功能帮助应用安装程序在应用安装后并且连接到其数据时对应用进行配置。

    此选项卡中还提供了指向应用文档的链接。

    ![参数](media/service-template-apps-create/power-bi-create-parameters.png)

    每个参数都有一个名称和说明（来自查询），以及一个值字段。 可通过三种方式在安装期间获取参数的值。

    * 可以要求安装程序输入值。 在这种情况下，你将提供一个它们将替换的示例。 若要以这种方式配置参数，请选中“必需”复选框，然后在文本框中提供一个向用户显示所需值类型的示例。 例如：

       ![需要用户提供的参数值的屏幕截图。](media/service-template-apps-create/power-bi-create-parameters-require-user.png)

    * 可以提供一个安装应用的用户无法更改的预填充值。 通过此方式配置的参数对安装应用的用户隐藏。 仅当确定预填充的值对所有用户均有效时，才应使用此方法；否则，请使用上面提到的第一种需要用户输入的方法。

       若要以这种方式配置参数，请在“值”文本框中输入值，然后单击锁定图标。 这样便无法更改值。 例如：

       ![绝对参数值的屏幕截图。](media/service-template-apps-create/power-bi-create-parameters-absolute.png)

    * 可以提供用户在安装期间可更改的默认值。 若要以这种方式配置参数，请在“值”文本框中输入所需的默认值，并解锁锁定图标。 例如：

      ![可更改默认参数值的屏幕截图。](media/service-template-apps-create/power-bi-create-parameters-default.png)

    **身份验证**
    
    在此选项卡中，可以选择将使用的身份验证方法。 可用选项取决于所使用的数据源类型。

    ![身份验证方法选择的屏幕截图。](media/service-template-apps-create/power-bi-create-authentication.png)

    系统会自动配置隐私级别：
   * 单个数据源：自动配置为专用。
   * 多个匿名数据源：自动配置为公共。

    **访问**
    
    在测试阶段，确定组织中的其他人可以安装和测试应用。 别担心，可以随时返回并在稍后更改这些设置。 该设置不影响分布式模板应用的访问权限。

    ![“访问”选项卡的屏幕截图。](media/service-template-apps-create/power-bi-create-access.png)

2. 选择“创建应用”。

    你会看到测试应用已就绪的消息，其中包含可复制并与应用测试人员共享的链接。

    ![测试应用已就绪](media/service-template-apps-create/power-bi-template-app-test-ready.png)

    你还完成了发布管理过程的第一步，这也是接下来要完成的步骤。

## <a name="manage-the-template-app-release"></a>管理模板应用版本

在公开发布此模板应用之前，需要确保它已准备就绪。 Power BI 已创建发布管理窗格，可在其中关注并检查完整的应用发布路径。 还可以触发阶段间的转换。 常见的阶段包括：

- 生成测试应用：仅在组织中进行测试。
- 将测试包提升到预生产阶段：在组织外进行测试。
- 将预生产包提升到生产：生产版本。
- 删除任何包或从上一阶段重新开始。

在发布阶段之间转移时，URL 不会更改。 提升不影响 URL 本身。

让我们来了解各个阶段：

1. 在模板工作区中，选择“发布管理”****。

    ![发布管理图标](media/service-template-apps-create/power-bi-release-management-icon.png)

2. 如果在上面的“创建测试模板应用”部分中创建了测试应用（结果是，“测试”旁边的黄色圆点已经填充），请选择“获取链接”  。

    如果尚未创建应用，请选择“创建应用”。 这将使你返回到模板应用创建过程。

    ![创建应用，获取链接](media/service-template-apps-create/power-bi-dev-template-create-app-get-link.png)

4. 若要测试应用安装体验，请复制通知窗口中的链接并将其粘贴到新的浏览器窗口中。

    从这里开始，需要按照客户所遵循的相同过程进行操作。 请参阅[在组织中安装和分发模板应用](service-template-apps-install-distribute.md)。

5. 在对话框中，选择“安装”****。

    安装成功后，会看到新应用已就绪的通知。

6. 选择“转到应用”。
7. 在“开始使用新应用”中，看到的应用与客户将看到的应用相同****。

    ![开始使用应用](media/service-template-apps-create/power-bi-template-app-get-started.png)
8. 选择“浏览应用”以使用示例数据验证测试应用****。
9. 若要进行任何更改，请返回到原始工作区中的应用。 更新测试应用，直到满意为止。
10. 准备好将应用提升到预生产以在租户之外进行进一步测试时，请返回“发布管理”窗格，然后选择“提升应用”********。

    ![将应用提升到预生产](media/service-template-apps-create/power-bi-template-app-promote.png)
    >[!NOTE]
    > 应用提升后，将在组织外部变得公开可用。

    如果没有看到该选项，请与你的 Power BI 管理员联系，以向你授予管理门户中[模板应用开发权限](../admin/service-admin-portal.md#template-apps-settings)。
11. 选择“提升”以确认选择****。
12. 复制此新 URL 以在租户外共享以供测试。 通过提交此链接，你还可以开启通过创建[新的合作伙伴中心产品/服务](/azure/marketplace/partner-center-portal/create-power-bi-app-offer)在 AppSource 上分发应用的流程。 仅向合作伙伴中心提交预生产链接。 只有在应用获得批准且你收到应用已在 AppSource 中发布的通知后，才能在 Power BI 中将此包提升到生产。
13. 当应用准备好通过 AppSource 进行生产或共享时，请返回“发布管理”窗格，然后选择“预生产”旁边的“提升应用”************。
14. 选择“提升”以确认选择****。

    现在应用已投入生产，并已准备好分发。

    ![生产中的应用](media/service-template-apps-create/power-bi-template-app-production.png)

为了让应用广泛适用于全球数千名 Power BI 用户，我们建议将该应用提交到 AppSource。 有关详细信息，请参阅 [Power BI 应用程序产品/服务](/azure/marketplace/partner-center-portal/create-power-bi-app-offer)。

## <a name="next-steps"></a>后续步骤

通过[在组织中安装、自定义和分发模板应用](service-template-apps-install-distribute.md)，了解客户与模板应用的互动方式。

有关分发应用的详细信息，请参阅 [Power BI 应用程序产品/服务](/azure/marketplace/partner-center-portal/create-power-bi-app-offer)。