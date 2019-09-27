---
title: 为自己和他人订阅报表和仪表板 - Power BI
description: 了解如何为自己和他人订阅 Power BI 报表页、仪表板或分页报表的快照。
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: maggies
LocalizationGroup: Common tasks
ms.openlocfilehash: 2c08736e23568675af87e7de63092fff3a6a86c5
ms.sourcegitcommit: a97c0c34f888e44abf4c9aa657ec9463a32be06f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2019
ms.locfileid: "71073423"
---
# <a name="subscribe-yourself-and-others-to-reports-and-dashboards-in-the-power-bi-service"></a>在 Power BI 服务中为自己和他人订阅报表和仪表板

你可以为自己和同事订阅对你来说最重要的报表页、仪表板和分页报表。 Power BI 以电子邮件形式将快照发送到你的收件箱。 告知 Power BI 所需的电子邮件接收频率：每天、每周、每小时、每月或是一天一次在初始数据刷新之后。  如果选择每天、每周、每小时或每月，则可以选择要使订阅运行的时间。  总共可以为每个报表页和仪表板每天设置最多 24 个不同的订阅。

![仪表板的电子邮件快照](media/service-report-subscribe/power-bi-dashboard-email-new.jpg) 

只能在 Power BI 服务中创建订阅。 收到的电子邮件包含报表页或仪表板的快照，以及用于打开报表或仪表板的链接。 在安装了 Power BI 应用的移动设备上，选择此链接将启动 Power BI 应用，而不是在 Power BI 网站中打开报表或仪表板。

## <a name="requirements"></a>要求

创建订阅可由以下人员完成：

- 有 Power BI Pro 许可证的用户
- 在 Premium 工作区或应用中查看内容的用户，即使没有 Power BI Pro 许可证，也可以订阅其中的内容。

无需内容（仪表板或报表）编辑权限即可为自己创建订阅，但必须拥有编辑权限才能为他人创建订阅。 

## <a name="subscribe-to-a-dashboard-report-page-or-paginated-report"></a>订阅仪表板、报表页或分页报表

无论是订阅仪表板、报表还是分页报表，订阅过程都类似。 使用同一按钮，即可订阅 Power BI 服务仪表板和报表。

订阅分页报表略有不同。 请参阅[在 Power BI 服务中为自己和他人订阅分页报表](paginated-reports-subscriptions.md)，获取详细信息。
 
![选择“订阅”图标](media/service-report-subscribe/power-bi-subscribe-orientation.png)。

1. 打开仪表板或报表。
2. 在顶部菜单栏中，选择“订阅”或信封图标 ![订阅图标](media/service-report-subscribe/power-bi-icon-envelope.png)。
   
   ![订阅图标](media/service-report-subscribe/power-bi-subscribe-icon.png)

3. 使用黄色滑块可启用和禁用订阅。  将滑块设置为“关”不会删除订阅。 若要删除订阅，请选择垃圾桶图标。

4. 电子邮件已存在于“订阅”框中。 还可以向订阅添加其他电子邮件地址，但是只能处于相同域中。 如果报表或仪表板托管在[高级容量](service-premium-what-is.md)中，则可为其他个人电子邮件地址和组别名订阅。 如果报表或仪表板未托管在高级容量中，则可为其他个人订阅，但他们必须具有 Power BI Pro 许可证。 有关详细信息，请参阅下面的[注意事项和疑难解答](#considerations-and-troubleshooting)。 

5. 填写电子邮件“主题”和“邮件”详细信息。 

5. 选择订阅的“频率”：“每天”、“每小时”、“每周”、“每月”或“数据刷新后(每天)”。  要仅在某些天接收订阅电子邮件，请选择“每小时”或“每周”，然后选择要在哪几天接收电子邮件。  例如，如果要仅在工作日收到订阅电子邮件，则选择“每周”，并清除“周六”和“周日”的对应框。  如果选择“每月”，请输入要接收订阅邮件的月份的日期。  

6. 如果选择“每天”、“每小时”、“每月”或“每周”，则还可以为订阅选择“计划时间”。  可使它按小时运行，或在过去 15、30 或 45 分钟时运行。  选择早上 (AM) 或下午/晚上 (PM)。 还可以指定时区。  如果选择“每小时”，选择你希望订阅开始的“计划时间”之后，将在该时间后每小时运行一次。

7. 默认情况下，订阅的开始日期是创建它的日期。 可以选择结束日期。 如果未设置结束日期，则结束日期自动是开始日期之后一年。 可以在订阅结束之前的任何时间将它更改为将来的任何日期（最多到 9999 年）。 当订阅达到结束日期时，它会停止，直到重新启用。 你会在计划结束日期之前收到通知，询问是否要延长它。    

    在以下屏幕截图中，请注意订阅报表实际上订阅的是报表页。  要订阅报表中的多个页，请选择“添加其他订阅”并选择另一页。 
      
   ![“订阅”窗格](media/service-report-subscribe/power-bi-subscribe-pane.png)  

7. 选择“保存并关闭”。 订阅者会按所选频率和时间收到仪表板或报表页的电子邮件和快照。 总共可以创建对每个报表或仪表板创建最多 24 个订阅，并可以为每个订阅提供独有的收件人、时间和频率。  对仪表板或报表设置为“数据刷新后”的所有订阅仍然只会在第一次计划刷新之后发送电子邮件。   
      
   > [!TIP]
   > 想立即通过订阅或随时按需发送电子邮件吗？ 选择“立即运行”以获取要发送的仪表板或报表的订阅。 你将看到一封电子邮件正发送给每个人的通知，通知内容是关于该特定订阅的。  执行此操作不计入每天每个报表或仪表板的 24 次预定订阅运行的限制。 这不会引起基础数据集的数据刷新。 
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

* 具有超过 25 个固定磁贴或 4 个固定活动报表页面的仪表板可能无法完全呈现在发送给用户的订阅电子邮件中。  不会阻止通过大量磁贴订阅仪表板。 但如果遇到问题，它们会视为不受支持。 考虑对其进行相应修改，使其处于受支持的范围内。
* 在极少数情况下，电子邮件订阅可能需要超过 15 分钟才能发送到收件人。 如果发生这种情况，请在不同时间运行数据刷新和电子邮件订阅，以确保及时交付。 如果问题仍然存在，请联系 Power BI 支持。
* 对于仪表板电子邮件说明，如果任何磁贴应用了行级别安全性 (RLS)，则不会显示这些磁贴。  
* 对于报表电子邮件说明，如果数据集使用 RLS，你可以为自己创建订阅。 不能将其他人订阅到应用了行级别安全性 (RLS) 的报表，除非你使用分页报表，分页报表允许你使用安全上下文将订阅发送给其他人。 
* 报表页订阅与报表页面的名称是相关联的。 如果你订阅一个报表页，随后将其重命名，则必须重新创建订阅。
* 组织可能在 Azure Active Directory 中配置的某些设置会限制 Power BI 中电子邮件订阅的使用。  这些限制包括但不限于针对资源访问设置多重身份验证或 IP 范围限制。
* 当前，在订阅自己以外的用户时，不支持对使用实时连接数据集的报表/仪表板进行电子邮件订阅，除非你使用的是分页报表，分页报表允许你使用安全性上下文将订阅发送给其他人。 
* 电子邮件订阅不支持大多数[自定义视觉对象](power-bi-custom-visuals.md)。  已经过[认证](power-bi-custom-visuals-certified.md)的自定义视觉对象除外。  
* 目前电子邮件订阅不支持 R 驱动的自定义视觉对象。  
* 电子邮件订阅与报表的默认筛选器和切片器状态一起发送。 在订阅后对默认设置所做的任何更改都不会显示在电子邮件中。  分页报表支持此功能，并允许你为每个订阅设置特定的参数值。   
* 对于仪表板订阅，具体来说，尚不支持某些类型的磁贴。  其中包括流磁贴、视频磁贴、自定义 Web 内容磁贴。     
* 如果与租户外的同事共享仪表板，则无法为该同事也创建订阅。 因此，如果你是 aaron@xyz.com，则可以与 anyone@ABC.com 共享，但目前无法为 anyone@ABC.com 订阅并且他们也无法订阅共享内容。      
* 如果超过两个月一直没有人访问仪表板和报表，那么 Power BI 会自动暂停刷新与它们关联的数据集。  不过，如果添加对仪表板或报表的订阅，即使无人访问，也不会暂停刷新。    
* 如果未收到订阅电子邮件，请确保用户主体名称 (UPN) 可以接收电子邮件。 
* 如果你的仪表板或报表位于高级容量中，则可使用组电子邮件别名进行订阅，而不用一次使用一个电子邮件地址为同事订阅。 根据当前的 Active Directory 确定别名。 

## <a name="next-steps"></a>后续步骤

- [在 Power BI 服务中为自己和他人订阅分页报表](paginated-reports-subscriptions.md)
- 更多问题？ [尝试咨询 Power BI 社区](http://community.powerbi.com/)    
- [阅读博客文章](https://powerbi.microsoft.com/blog/introducing-dashboard-email-subscriptions-a-360-degree-view-of-your-business-in-your-inbox-every-day/)
