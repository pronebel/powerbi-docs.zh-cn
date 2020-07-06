---
title: 为自己订阅报表和仪表板
description: 了解如何为你自己订阅 Power BI 报表或仪表板的电子邮件快照。
author: mihart
ms.author: mihart
ms.reviewer: cmfinlan
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: how-to
ms.date: 05/11/2020
LocalizationGroup: Common tasks
ms.openlocfilehash: e82dde5022bf0ad28d37e0ed9a8ac9553fbbd75d
ms.sourcegitcommit: a453ba52aafa012896f665660df7df7bc117ade5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2020
ms.locfileid: "85485889"
---
# <a name="subscribe-to-a-report-or-dashboard-in-the-power-bi-service"></a>在 Power BI 服务中订阅报表或仪表板 

[!INCLUDE[consumer-appliesto-ynny](../includes/consumer-appliesto-ynny.md)]

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

现在，及时更新最重要的仪表板和报表，比以前更加轻松。 订阅最重要的报表页和仪表板，Power BI 将会通过电子邮件将快照发送到收件箱。 告知 Power BI 所需的电子邮件接收频率：每天、每周或是在数据刷新时。 甚至可以为 Power BI 发送电子邮件设置特定时间或立即运行此操作。  总共可以为每个报表或仪表板设置最多 24 个不同的订阅。

电子邮件和快照将使用在 Power BI 设置中设置的语言（请参阅 [Power BI 的支持语言和国家/地区](../fundamentals/supported-languages-countries-regions.md)）。 如果未定义任何语言，Power BI 会根据当前浏览器中的区域设置使用语言。 要查看或设置语言首选项，请选择齿轮图标 ![齿轮图标](./media/end-user-subscribe/power-bi-settings-icon.png) > “设置”>“常规”>“语言”。 

![语言下拉列表](./media/end-user-subscribe/power-bi-language.png)

收到的电子邮件中包含“转到报表或仪表板”链接。 在安装了 Power BI 应用的移动设备上，选择此链接将启动应用（而不是执行在 Power BI 网站上打开报表或仪表板这样的默认操作）。


## <a name="requirements"></a>要求
必须有特定类型的[许可证](end-user-license.md)，才能为你自己创建订阅。 如果无法创建订阅，请联系 Power BI 管理员。 “订阅其他内容”仅适用于仪表板或报表所有者。 订阅分页报表略有不同。 请参阅[在 Power BI 服务中为自己和他人订阅分页报表](paginated-reports-subscriptions.md)，获取详细信息。 

## <a name="subscribe-to-a-dashboard-or-a-report-page"></a>订阅仪表板或报表页
无论是要订阅仪表板还是报表，过程都类似。 使用同一按钮，即可订阅 Power BI 服务仪表板和报表。
 
![选择“订阅”图标](./media/end-user-subscribe/power-bi-subscribe.png)。

1. 打开仪表板或报表。
2. 在顶部菜单栏中，选择“订阅”或信封图标 ![订阅图标](./media/end-user-subscribe/power-bi-icon-envelope.png)。
   


   ![订阅窗口](./media/end-user-subscribe/power-bi-emails-numbered.png)
    
    在处于某个仪表板上并选择“订阅”时，左侧屏幕会出现。 在处于某个报表页上并选择“订阅”时，右侧屏幕会出现。 
    
    a. 要订阅报表中的多个页，请从顶部附近的下拉列表选择“添加其他订阅”并选择另一页。

    b. 使用黄色滑块可启用和禁用订阅。  将滑块设置为“关”不会删除订阅。 若要删除订阅，请选择垃圾桶图标。

    c. （可选）添加主题和电子邮件详细信息。 

    d. 选择订阅的“频率”。  可以选择“每天”、“每周”或“数据刷新后(每天)”。  若要仅在某些天接收订阅电子邮件，请选择“每周”，然后选择要在哪几天接收电子邮件。  例如，若要仅在工作日收到订阅电子邮件，请选择“每周一次”作为频率，并取消选中“周六”和“周日”对应的框。 如果选择“每月”，请输入要接收订阅邮件的月份的日期。   

    e. 如果选择“每天”、“每小时”、“每月”或“每周”，还可以为订阅选择“计划时间”。 可使它按小时运行，或在过去 15、30 或 45 分钟时运行。 选择早上 (AM) 或下午/晚上 (PM)。 还可以指定时区。 如果选择“每小时”，请选择你希望订阅开始的“计划时间”，之后它将每小时运行一次。  

    f. 通过在日期字段中输入日期来计划开始和结束日期。 默认情况下，订阅的开始时间会是创建它的日期，而结束日期会是一年后。 可以在订阅结束之前的任何时间将它更改为将来的任何日期（最多到 9999 年）。 当订阅达到结束日期时，它会停止，直到重新启用。  你会在计划结束日期之前收到通知，询问是否要延长它。     

    如， 若要查看你的订阅并进行测试，请选择“立即运行”。  它将立即向你发送电子邮件。 

3. 如果看起来一切正常，请选择“保存并关闭”，保存订阅。 你会按照所设置的计划收到仪表板或报表的电子邮件和快照。 频率设置为“数据刷新后”的所有订阅都只会在该天的第一次计划刷新之后发送电子邮件。
   
   ![仪表板的电子邮件快照](media/end-user-subscribe/power-bi-email-old.png)
   
    刷新报表页不会刷新数据集。 只有数据集所有者能够手动刷新数据集。 若要查找基础数据集的所有者名称，请从菜单栏中选择下拉列表或查看原始订阅电子邮件。
   
    ![查找所有者](./media/end-user-subscribe/power-bi-owner.png)


## <a name="manage-your-subscriptions"></a>管理订阅
只有你可以管理你所创建的订阅。 再次选择“订阅”，然后选择左下角的“管理所有订阅”（见上面的屏幕截图）。 具体显示哪些订阅视当前处于活动状态的工作区而定。 若要一次性查看所有工作区的全部订阅，请确保“**我的工作区**”处于活动状态。 若要了解工作区，请参阅 [Power BI 中的工作区](end-user-workspaces.md)。 

![请参阅我的工作区中的所有订阅](./media/end-user-subscribe/power-bi-manage-subscriptions.png)

如果 Pro 许可证到期、所有者删除仪表板或报表，或用于创建订阅的用户帐户被删除，那么订阅将结束。

## <a name="considerations-and-troubleshooting"></a>注意事项和疑难解答
* 为了避免订阅电子邮件转到垃圾邮件文件夹，请将 Power BI 电子邮件别名 (no-reply-powerbi@microsoft.com) 添加到联系人中。 如果使用的是 Microsoft Outlook，请右键单击别名，然后选择“添加到 Outlook 联系人”。 
* 具有超过 25 个固定磁贴或 4 个固定活动报表页的仪表板可能无法完全呈现在发送给用户的订阅电子邮件中。 我们建议你联系并要求磁贴设计者将固定磁贴减少到 25 个以下，并将固定活动报表固定为少于 4 个，以确保电子邮件正确呈现。  
* 对于仪表板电子邮件说明，如果任何磁贴应用了行级别安全性 (RLS)，则不会显示这些磁贴。  
* 如果电子邮件中的链接（指向内容）停止工作，则可能是该内容已被删除。 在电子邮件的屏幕截图下方，你可以查看自己或其他人是否订阅了你的邮件。 如果是其他人，请让该同事取消电子邮件或重新订阅。
* 对于仪表板订阅，尚不支持某些类型的磁贴。 其中包括流磁贴、视频磁贴、自定义 Web 内容磁贴。 
* 报表页订阅与报表页面的名称是相关联的。 如果你订阅一个报表页，而后将其重命名，则必须重新创建订阅。
* 如果无法使用订阅功能，请与系统管理员联系。 你的组织可能禁用了此功能。  
* 电子邮件订阅不支持大多数[自定义视觉对象](../developer/visuals/power-bi-custom-visuals.md)。  已经过[认证](../developer/visuals/power-bi-custom-visuals-certified.md)的 Power BI 自定义视觉对象除外。    
* 电子邮件订阅与报表的默认筛选器和切片器状态一起发送。 在订阅后对默认设置所做的任何更改都不会显示在电子邮件中。 分页报表支持此功能，并允许你为每个订阅设置特定的参数值。  
* 目前，电子邮件订阅不支持 R 驱动的 Power BI 视觉对象。  
* 对于仪表板订阅，具体来说，尚不支持某些类型的磁贴。  其中包括流磁贴、视频磁贴、自定义 Web 内容磁贴。     
* 由于电子邮件大小限制，可能无法订阅包含极大图像的仪表板或报表。    
* 如果超过两个月一直没有人访问仪表板和报表，那么 Power BI 会自动暂停刷新与它们关联的数据集。  不过，如果添加对仪表板或报表的订阅，即使无人访问，也不会暂停刷新。
* 请记住，与其他 BI 产品一样，设置订阅的时间是开始处理订阅的时间。  报表处理完成后，订阅将排队并发送给电子邮件收件人。  虽然我们努力尽可能快地处理和交付所有订阅，但在需求高峰期，由于一次可发送的订阅数量有限，因而可能会出现较长的延迟。  对于大多数客户而言，处理和发送报告的延迟不会超过 15 分钟，不过对于特定时间和使用量大的租户，延迟可能会长达 30 分钟。  我们从不希望从计划订阅时间起的任何交付延迟超过 60 分钟。  如果任何客户遇到此等长时间延迟，则应首先确保地址 no-reply-powerbi@microsoft.com 位于安全发件人列表中，且未被电子邮件提供商阻止。  如果电子邮件未被阻止，他们应联系 Power BI 支持人员以寻求帮助。

## <a name="next-steps"></a>后续步骤

[对内容进行搜索和排序](end-user-search-sort.md)
