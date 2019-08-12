---
title: Power BI 报表服务器的更改日志
description: 此更改日志适用于 Power BI 报表服务器，并列出了新项和每次发布版本的 bug 修复。
ms.author: jaimeta
author: jtarquino
manager: kfile
ms.reviewer: maggies
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 03/31/2018
ms.openlocfilehash: 031274f4f35ef1e36ec17648c2cbf967f5436020
ms.sourcegitcommit: 73228d0a9038b8369369c059ad06168d2c5ff062
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/02/2019
ms.locfileid: "68729793"
---
# <a name="changelog-for-power-bi-report-server"></a>Power BI 报表服务器的更改日志

此更改日志适用于 Power BI 报表服务器，并列出了新项和每次发布版本的 bug 修复。

有关新功能的详细信息，请参阅[Power BI 报表服务器中的新增功能](whats-new.md)。 

## <a name="may-2019"></a>2019 年 5 月

- **Power BI 报表服务器**          
    - *版本 1.5.7074.36177（内部版本 15.0.1102.371），发布日期：2019 年 5 月 21 日*
        - Bug 修复
            - 分页报表
                - 修复了问题：始终启用 pdf 字体嵌入。
                - 修复了问题：通过 https 发送的 cookie 设置为“安全”
                - 修复了问题：脚本错误导致弹出窗口
                - 修复了 Android 手机上移动应用的显示问题
                - 修复了移动报表时间导航器的问题，使其能够显示正确的周数，而不考虑会计年度的开始日期
                - 为管理员添加了可配置属性“RestrictedResourceMimeTypeForUpload”，用于指定禁止的 mime 类型
         - 功能
            - 向 PBIRS 添加了对信任视觉对象的支持

- Power BI Desktop（已针对 Power BI 报表服务器进行优化） 
    - *版本：2.69.5467.1801（2019 年 5 月），发布日期：2019 年 5 月 21 日*
        - Bug 修复
            - 修复了问题：在 PBIX 上传到 PBIRS 期间重新输入凭据
            - 修复了问题：打开文件名中带 # 的文档
            - 添加了用于在 PBIRS 选择窗口上执行后退导航操作的更便捷的链接
            - 修复了 PBIRS 中的高对比度模式问题：显示后退按钮，显示视觉警告消息。
            - 修复了“选择”窗格和画布缩放的 UI 问题。

    - *版本：2.69.5467.5201（2019 年 5 月），发布日期：2019 年 7 月 30 日*
        - Bug 修复
            - 针对错误遥测日志记录的修复

## <a name="january-2019"></a>2019 年 1 月

- **Power BI 报表服务器**          
    - *版本 1.4.7024.16477（内部版本 15.0.1102.299），发布日期：2019 年 3 月 28 日*
        - Bug 修复
            - Power BI 报表
                - 修复了对 SAP Hana 和 SAP BW 使用直接查询时基本凭据方面出现的问题
                - 修复了显示“无法加载文件或程序集 Microsoft.OData.Core.NetFX35.V7”错误的 OData 源数据刷新失败问题

- **Power BI 报表服务器**            
    - *版本 1.4.6969.7395（内部版本 15.0.1102.235），发布日期：2019 年 1 月 30 日*
        - Bug 修复
            - Power BI 报表
                - 修复了使用直接查询时基本凭证的问题
                - 修复了应用行级别安全筛选器的双向关系
                - 修复了在扩展环境中刷新模型后的过时数据
                - 修复了 Firefox 63 + 上用于表/矩阵的双滚动条
                - 修复了 Internet Explorer 中的 +/- 图标大小
            - 分页报表
                - 修复了更新报表共享数据源使用的问题

    - 版本 1.4.6960.38798（内部版本 15.0.1102.222），发布日期：  2019 年 1 月 22日
        - 功能
            - Power BI 报表 
                - 支持行级别安全性
                - 展开和折叠矩阵行标题
                - 在 .pbix 文件之间复制和粘贴
                - 智能对齐参考线
                - 对 SAP BW 2.0 连接器的支持
            - 管理员
                - 限制可上传到报表服务器的资源扩展的功能
                - 限制受支持超链接方案的功能
            - 可编程性
                - 新 Web API：/PowerBIReports({Id})/DataModelRoles (GET)
                - 新 Web API：/PowerBIReports({Id})/DataModelRoleAssignments (GET & PUT)
                - 有关更多详细信息，请参阅 [Power BI 报表服务器 REST API](https://app.swaggerhub.com/apis/microsoft-rs/PBIRS/2.0)
        - Bug 修复
            - HTML 注入漏洞
            - “导出为 PDF”未显示欧元符号
            - 在 Power BI 报表中保存具有多个数据源的密码会使未更改的密码失效
            - 在 Power BI 移动应用中，视觉对象空闲时会显示问题

- Power BI Desktop（已针对 Power BI 报表服务器进行优化） 
    - *版本：2.65.5313.1562（2019 年 1 月），发布日期：2019 年 1 月 30 日*
        - 卸载 Power BI 报表服务器后快捷方式和固定图标仍保留
        - 修复了将 Power BI 报表服务器固定到开始菜单的问题 - 在黑色图标上显示黑色文本

    - *版本：2.65.5313.1421（2019 年 1 月），发布日期：2019 年 1 月 22 日*（新内部版本和新版本）
        - 包含与 Power BI 报表服务器连接所需的更改（2019 年 1 月） 
    - *版本：2.65.5313.5141（2019 年 1 月），发布日期：2019 年 1 月 31 日*（新内部版本和新版本）
        - Bug 修复
            - 针对错误遥测日志记录的修复

## <a name="august-2018"></a>2018 年 8 月

- **Power BI 报表服务器**
    - *版本 1.3.6816.37243（内部版本 15.0.2.557），发布日期：2018 年 8 月 30 日*
        - Bug 修复
            - 修复了以下问题：服务器已从早期版本的 PBI Report Server 升级，但未更新绑定重定向，此时客户看到以下信息：      
            *`
            Failed to load expression host assembly. Details: Could not load file or assembly 'Microsoft.ReportingServices.ProcessingObjectModel, Version=2018.7.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040) (rsErrorLoadingExprHostAssembly)
             `*
             
            - 数据标签透明度的 bug 现已修复。
            
    - *版本 1.3.6801.38816（内部版本 15.0.2.540），发布日期：2018 年 8 月 15 日*
        - 功能
            - Power BI 报表现在提供使用 Kerberos 的 SAP HANA SSO 直接查询支持
            - 发布版附带的自定义视觉对象 API - 版本 1.13.0
            - 自定义视觉对象回退到与当前版本的服务器 API 兼容的先前版本（如果可用）

- Power BI Desktop（已针对 Power BI 报表服务器进行优化） 
    - *版本：2.61.5192.641（2018 年 8 月），发布日期：2018 年 8 月 15 日*
        - 包含与 Power BI 报表服务器连接所需的更改（2018 年 8 月）         
        
## <a name="march-2018"></a>2018 年 3 月

- **Power BI 报表服务器**
    - *版本 1.2.6690.34729（内部版本 15.0.2.402），发布日期：2018 年 4 月 27 日*
        - Bug 修复
            - 启用 SQL Server Reporting Services 2017 目录迁移
            - Power BI 报表 (PBIX)
                - 服务器配置为使用自定义身份验证时，可以刷新报表
                - 修改报表属性不会重置数据源凭据
            - 分页报表 (RDL)
                - `Lookup()` 的使用情况或派生功能（如 RDL 表达式中的 `LookupSet()` 和 `MultiLookup()`）不再导致 `#Error`
                - 链接报表在打印时接受目标报表页大小
                - 可以为使用级联参数的链接报表创建订阅
                - 在使用 IE11 时，可以修改多值参数默认值
                - 数据驱动订阅传递选项可编辑
                - 可以在订阅执行期间查看和编辑订阅
                - 设置数据源凭据不会删除基于表达式的连接字符串
            - 对于 KPI
                - 更新数据时会刷新趋势线
            - 总体稳定性改进

    - *版本 1.2.6660.39920（内部版本 15.0.2.389），发布日期：2018 年 3 月 28 日*
        - Bug 修复
            - 对于 Power BI 报表 (PBIX)，修复在 Power BI 视觉对象中无法正常工作的导出数据
            - 对于 Power BI 报表 (PBIX)，修复无法正常工作的 URL 筛选器
            - 对于分页报表 (RDL)，修复在升级到 Power BI 报表服务器 3 月发行版后在 IE11 中未正确显示的映像

    - *版本 1.2.6648.38132（内部版本 15.0.2.378），发布日期：2018 年 3 月 19 日*
        - 安全更新
        - 辅助功能改进
        - Bug 修复
            - 针对分页报表 (RDL)，修复链接报表中的参数可见性在编辑属性后被还原的问题
            - 修复采用自定义窗体身份验证的 Web 门户忽略滑动期限 cookie
            - 修复导出到 Word 时，因行内容为空导致行高不一致的问题
            - 针对分页报表 (RDL)，修复在更改数据源凭据时基于表达式的连接字符串被删除的问题
            - 修复将 KPI 与文本值一起使用的能力
            - 针对分页报表 (RDL)，修复将新数据集分配到现有分页报表 (RDL) 的能力
            - 其他稳定性和可用性的修复内容

- Power BI Desktop（已针对 Power BI 报表服务器进行优化） 
    - 版本:2.56.5023.1043（2018 年 3 月），发布日期：2018 年 3 月 19 日
        - 包含与 Power BI 报表服务器连接所需的更改（2018 年 3 月）

## <a name="october-2017"></a>2017 年 10 月

- **Power BI 报表服务器**
    - *版本 1.1.6582.41691（内部版本 14.0.600.442），发布日期：2018 年 1 月 10 日*
        - 安全更新
        - Bug 修复
            - 修复了 Model.GetParameters 返回 400 的问题
            - 修复了将共享数据集设置为现有分页报表 (RDL) 的问题
            - 修复了将使用不同参数值的报表导出到 PDF 时出现的 ExecutionNotFoundException

    - *版本 1.1.6551.5155（内部版本 14.0.600.438），发布日期：2017 年 12 月 11 日*
        - Bug 修复
            - 某些 Power BI Desktop 报表刷新之后无法保存数据。

    - *版本 1.1.6530.30789（内部版本 14.0.600.437），发布日期：2017 年 11 月 17 日*
        - Bug 修复
            - 针对基本身份验证方案进行了修复 
            - 修复了以下问题：无法在门户上“订阅”、“缓存刷新计划”和“历史记录快照”的计划页上选择工作日
            - 对于分页报表 (RDL)，修复了以下问题：如果文本框中的表达式将 CanGrow 属性设为 False，则会导致值不显示颜色且字体不正确
            - 对于 Power BI 报表 (PBIX)，修复了以下问题：向折线图添加图例会导致呈现的视觉对象为空

    - *版本 1.1.6514.9163（内部版本 14.0.600.434），发布日期：2017 年 11 月 1 日*
        - Bug 修复
            - 对超过 500MB 的 PBIX 报表的上传可靠性问题的修复
            - 对超过 1GB 的 PBIX 报表的数据上传问题的修复

    - *版本 1.1.6513.3500（内部版本 14.0.600.433），发布日期：2017 年 10 月 31 日*
        - 功能
            - 嵌入数据模型支持
            - Excel 工作簿查看（已启用 Office Online Server 集成）
            - 计划的数据刷新 (PBIX)
            - 直接查询支持
            - 大文件支持（最大 2 GB）
            - 公用 REST API
            - Power BI Desktop 中的共享数据集支持（通过 oData）
            - URL 参数 支持 PBIX 文件
            - 辅助功能改进

- Power BI Desktop（已针对 Power BI 报表服务器进行优化） 
    - *版本：2.51.4885.3981（2017 年 10 月），发布日期：2018 年 4 月 10 日*
        - 安全更新

    - *版本：2.51.4885.2501（2017 年 10 月），发布日期：2018 年 1 月 10 日*
        - 安全更新

    - *版本：2.51.4885.1423（2017 年 10 月），发布日期：2017 年 11 月 17 日*
        - Bug 修复
            - 修复了以下问题：32 位 Power BI Desktop 无法在 x86 OS 上运行
            - 对于 Power BI 报表 (PBIX)，修复了 X 轴网格线的显示问题
            - 其他次要缺陷修复

    - *版本：2.51.4885.1041（2017 年 10 月），发布日期：2017 年 10 月 31 日*
        - 功能
            - 包含与 Power BI 报表服务器连接所需的更改（2017 年 10 月）

## <a name="june-2017"></a>2017 年 6 月

- **Power BI 报表服务器**
    - *内部版本 14.0.600.309，发布日期：2018 年 1 月 10 日*
        - 安全更新

    - *内部版本 14.0.600.305，发布日期：2017 年 9 月 19 日*  
        - Bug 修复
            - 更新到最新的[必应地图 Web 控件](https://msdn.microsoft.com/library/mt712542.aspx)

    - *内部版本 14.0.600.301，发布日期：2017 年 7 月 11 日*
        - Bug 修复
            - `{{UserId}}` 标记解析为存储的凭据，而不是在 Power BI 报表中执行报表的用户
            - 某些图像无法在 Power BI 报表服务器报表中呈现
            - 无法在 Power BI 报表服务器中更改 Power BI 报表的名称
            - 无法在 Power BI 移动应用程序中加载自定义视觉对象（需要重新安装移动应用以清除本地缓存）

    - *内部版本 14.0.600.271，发布日期：2017 年 6 月 12 日*
        - Power BI 报表服务器初始版本

- Power BI Desktop（已针对 Power BI 报表服务器进行优化） 
    - *版本：2.47.4766.4901（2017 年 6 月），发布日期：2018 年 1 月 10 日*
        - 安全更新

## <a name="next-steps"></a>后续步骤

[什么是 Power BI 报表服务器？](get-started.md)
[管理员概述](admin-handbook-overview.md)  
[安装 Power BI 报表服务器](install-report-server.md)  
[下载报表生成器](https://www.microsoft.com/download/details.aspx?id=53613)  
[下载 SQL Server Data Tools (SSDT)](http://go.microsoft.com/fwlink/?LinkID=616714)

更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)
