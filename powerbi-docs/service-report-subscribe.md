---
title: 在 Power BI 服务中为自己和他人订阅报表和仪表板
description: 了解如何为自己和他人订阅 Power BI 报表或仪表板快照。
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 01/29/2019
ms.author: maggies
LocalizationGroup: Common tasks
ms.openlocfilehash: 09539bfd26685ffdd9866810b566699e5cdb4a41
ms.sourcegitcommit: a2f274cfb392fe3b1b466a39ec7eaf58a7c5ce00
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/19/2019
ms.locfileid: "56408106"
---
# <a name="subscribe-yourself-and-others-to-a-report-or-dashboard-in-the-power-bi-service"></a>在 Power BI 服务中为自己和他人订阅报表或仪表板

可以为自己和同事订阅最重要的报表页和仪表板，Power BI 会通过电子邮件将快照发送到收件箱。 告知 Power BI 所需的电子邮件接收频率：每天、每周或是一天一次在初始数据刷新之后。  如果选择每天或每周，则可以选择要使订阅运行的时间。  总共可以为每个报表页和仪表板每天设置最多 24 个不同的订阅。

![仪表板的电子邮件快照](media/service-report-subscribe/power-bi-dashboard-email-new.jpg) 

只能在 Power BI 服务中创建订阅。 收到的电子邮件包含报表页或仪表板的快照，以及用于打开报表或仪表板的链接。 在安装了 Power BI 应用的移动设备上，选择此链接将启动 Power BI 应用，而不是在 Power BI 网站中打开报表或仪表板。

## <a name="requirements"></a>要求
- 创建订阅是一项 Power BI Pro 功能。
- 无需内容（仪表板或报表）编辑权限即可为自己创建订阅，但必须拥有编辑权限才能为他人创建订阅。 
- 自 2019 年 1 月起，不再必须设置数据集刷新才能运行订阅。  它会独立于设置的任何计划刷新而运行。  

## <a name="subscribe-to-a-dashboard-or-a-report-page"></a>订阅仪表板或报表页
无论是订阅仪表板还是报表页，订阅过程都类似。 使用同一按钮，即可订阅 Power BI 服务仪表板和报表。
 
![选择“订阅”图标](media/service-report-subscribe/power-bi-subscribe-orientation.png)。

1. 打开仪表板或报表。
2. 在顶部菜单栏中，选择“订阅”或信封图标 ![订阅图标](media/service-report-subscribe/power-bi-icon-envelope.png)。
   
   ![订阅图标](media/service-report-subscribe/power-bi-subscribe-icon.png)

3. 使用黄色滑块可启用和禁用订阅。  将滑块设置为“关”不会删除订阅。 若要删除订阅，请选择垃圾桶图标。

4. 电子邮件已存在于“订阅”框中。 还可以向订阅添加其他电子邮件地址，但是只能处于相同域中。 如果报表或仪表板托管在[高级容量](service-premium.md)中，则可为其他个人电子邮件地址和组别名订阅。 如果报表或仪表板未托管在高级容量中，则可为其他个人订阅，但他们必须具有 Power BI Pro 许可证。 有关详细信息，请参阅下面的[注意事项和疑难解答](#considerations-and-troubleshooting)。 

5. 填写电子邮件“主题”和“邮件”详细信息。 

5. 选择订阅的“频率”：“每天”、“每周”或“数据刷新后(每天)”。  若要仅在某些天接收订阅电子邮件，请选择“每周”，然后选择要在哪几天接收电子邮件。  例如，如果要仅在工作日收到订阅电子邮件，则选择“每周”，并取消选中“周六”和“周日”的对应框。  

6. 如果选择“每天”或“每周”，则还可以为订阅选择“计划时间”。  可使它按小时运行，或在过去 15、30 或 45 分钟时运行。  选择早上 (AM) 或下午/晚上 (PM)。 还可以指定时区。

7. 默认情况下，订阅的开始日期是创建它的日期。 可以选择结束日期。 如果未设置结束日期，则结束日期自动是开始日期之后一年。 可以在订阅结束之前的任何时间将它更改为将来的任何日期（最多到 9999 年）。 当订阅达到结束日期时，它会停止，直到重新启用。 你会在计划结束日期之前收到通知，询问是否要延长它。    

    在以下屏幕截图中，请注意订阅报表实际上订阅的是报表页。  要订阅报表中的多个页，请选择“添加其他订阅”并选择另一页。 
      
   ![“订阅”窗格](media/service-report-subscribe/power-bi-subscribe-pane.png)  

7. 选择“保存并关闭”。 订阅者会按所选频率和时间收到仪表板或报表页的电子邮件和快照。 总共可以创建对每个报表或仪表板创建最多 24 个订阅，并可以为每个订阅提供独有的收件人、时间和频率。  对仪表板或报表设置为“数据刷新后”的所有订阅仍然只会在第一次计划刷新之后发送电子邮件。   
      
   > [!TIP]
   > 想立即通过订阅或随时按需发送电子邮件吗？ 选择“立即运行”以获取要发送的仪表板或报表的订阅。 你将看到一封电子邮件正发送给每个人的通知，通知内容是关于该特定订阅的。  可以根据需要随时执行此操作。 它不计入每天每个报表或仪表板的 24 次预定订阅运行的限制。 请注意，这不会引起基础数据集的数据刷新。 
   > 
   > 
   
## <a name="email-languages"></a>电子邮件语言

电子邮件和快照将使用在 Power BI 设置中设置的语言（请参阅 [Power BI 的支持语言和国家/地区](supported-languages-countries-regions.md)）。 如果未定义任何语言，Power BI 会根据当前浏览器中的区域设置使用语言。 要查看或设置语言首选项，请选择齿轮图标 ![齿轮图标](media/service-report-subscribe/power-bi-settings-icon.png) > “设置”>“常规”>“语言”。 

![语言下拉列表](media/service-report-subscribe/power-bi-language.png)

## <a name="manage-your-subscriptions"></a>管理订阅
仅订阅创建者可管理该订阅。  订阅管理屏幕的路径有两个。  第一个是选择“订阅电子邮件”对话框中的“管理所有订阅”（请参阅上述第 4 步下方的屏幕快照）。 第二个是选择顶部菜单栏中的 Power BI 齿轮图标 ![齿轮图标](media/service-report-subscribe/power-bi-settings-icon.png)，然后选择“设置”。

![选择“设置”](media/service-report-subscribe/power-bi-subscribe-settings.png)

具体显示哪些订阅视当前处于活动状态的工作区而定。  若要一次性查看所有工作区的全部订阅，请确保“**我的工作区**”处于活动状态。 若要了解工作区，请参阅 [Power BI 中的工作区](service-create-workspaces.md)。

![请参阅我的工作区中的所有订阅](media/service-report-subscribe/power-bi-subscriptions.png)

如果 Pro 许可证已到期、所有者删除仪表板或报表或用于创建订阅的用户帐户被删除，那么订阅会结束。

## <a name="considerations-and-troubleshooting"></a>注意事项和疑难解答
* 具有超过 25 个固定磁贴或 4 个固定活动报表页面的仪表板可能无法完全呈现在发送给用户的订阅电子邮件中。  将不会阻止对超过这些磁贴数量的仪表板订阅，但是，如果遇到问题，将认为它们不受支持，应相应地进行修改以使其处于受支持的范围内。
* 对于仪表板电子邮件说明，如果任何磁贴应用了行级别安全性 (RLS)，则不会显示这些磁贴。  对于报表电子邮件说明，如果数据集使用 RLS，则无法创建订阅。
* 报表页订阅与报表页面的名称是相关联的。 如果你订阅一个报表页，随后将其重命名，则必须重新创建订阅。
* 组织可能在 Azure Active Directory 中配置的某些设置会限制 Power BI 中电子邮件订阅的使用。  这些限制包括但不限于针对资源访问设置多重身份验证或 IP 范围限制。
* 为其他用户订阅时，当前不支持使用实时连接数据集的报表和仪表板的电子邮件订阅。
* 电子邮件订阅不支持大多数[自定义视觉对象](power-bi-custom-visuals.md)。  已经过[认证](power-bi-custom-visuals-certified.md)的自定义视觉对象除外。  
* 目前电子邮件订阅不支持 R 驱动的自定义视觉对象。  
* 如果任何仪表板磁贴应用了行级别安全性 (RLS)，则不会显示这些磁贴。
* 如果报表应用了行级别安全性 (RLS)，则无法为其他用户创建订阅。
* 电子邮件订阅与报表的默认筛选器和切片器状态一起发送。 在订阅后对默认设置所做的任何更改都不会显示在电子邮件中。    
* 对于仪表板订阅，具体来说，尚不支持某些类型的磁贴。  其中包括流磁贴、视频磁贴、自定义 Web 内容磁贴。     
* 如果与租户外的同事共享仪表板，则无法为该同事也创建订阅。 因此，如果你是 aaron@xyz.com，则可以与 anyone@ABC.com 共享，但目前无法为 anyone@ABC.com 订阅并且他们也无法订阅共享内容。      
* 由于电子邮件大小限制，可能无法订阅包含极大图像的仪表板或报表。    
* 如果超过两个月一直没有人访问仪表板和报表，那么 Power BI 会自动暂停刷新与它们关联的数据集。  不过，如果添加对仪表板或报表的订阅，即使无人访问，也不会暂停刷新。    
* 如果未收到订阅电子邮件，请确保用户主体名称 (UPN) 可以接收电子邮件。 [Power BI 团队正在努力放宽此要求](https://community.powerbi.com/t5/Issues/No-Mail-from-Cloud-Service/idc-p/205918#M10163)，敬请关注。 
* 如果你的仪表板或报表位于高级容量中，则可使用组电子邮件别名进行订阅，而不用一次使用一个电子邮件地址为同事订阅。 根据当前的 Active Directory 确定别名。 

## <a name="next-steps"></a>后续步骤
* 更多问题？ [尝试咨询 Power BI 社区](http://community.powerbi.com/)    
* [阅读博客文章](https://powerbi.microsoft.com/blog/introducing-dashboard-email-subscriptions-a-360-degree-view-of-your-business-in-your-inbox-every-day/)

