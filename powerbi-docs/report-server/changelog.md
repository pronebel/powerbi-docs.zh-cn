---
title: Power BI 报表服务器的更改日志
description: 此更改日志适用于 Power BI 报表服务器，并列出了新项和每次发布版本的 bug 修复。
author: jtarquino
manager: kfile
ms.reviewer: maggies
ms.service: powerbi
ms.component: powerbi-report-server
ms.topic: conceptual
ms.date: 03/31/2018
ms.author: jtarquino
ms.openlocfilehash: c80ded7a21eb8110467a2335253fa1a68942cc2c
ms.sourcegitcommit: 60fb46b61ac73806987847d9c606993c0e14fb30
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50101522"
---
# <a name="changelog-for-power-bi-report-server"></a>Power BI 报表服务器的更改日志

此更改日志适用于 Power BI 报表服务器，并列出了新项和每次发布版本的 bug 修复。

有关新功能的详细信息，请参阅[Power BI 报表服务器中的新增功能](whats-new.md)。 

## <a name="august-2018"></a>2018 年 8 月
- **Power BI 报表服务器**
    - 版本 1.3.6816.37243（内部版本 15.0.2.557），发布日期：2018 年 8 月 30 日
        - Bug 修复
            - 修复了以下问题：服务器已从早期版本的 PBI Report Server 升级，但未更新绑定重定向，此时客户看到以下信息：      
            *`
            Failed to load expression host assembly. Details: Could not load file or assembly 'Microsoft.ReportingServices.ProcessingObjectModel, Version=2018.7.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040) (rsErrorLoadingExprHostAssembly)
             `*
             
            - 数据标签透明度的 bug 现已修复。
            
    - 版本 1.3.6801.38816（内部版本 15.0.2.540），发布日期：2018 年 8 月 15 日
        - 功能
            - Power BI 报表现在提供使用 Kerberos 的 SAP HANA SSO 直接查询支持
            - 发布版附带的自定义视觉对象 API - 版本 1.13.0
            - 自定义视觉对象回退到与当前版本的服务器 API 兼容的先前版本（如果可用）

- Power BI Desktop（已针对 Power BI 报表服务器进行优化）
    - 版本：2.61.5192.641（2018 年 8 月），发布日期：2018 年 8 月15 日
        - 包含与 Power BI 报表服务器连接所需的更改（2018 年 8 月）         
        
## <a name="march-2018"></a>2018 年 3 月
- **Power BI 报表服务器**
    - 版本 1.2.6690.34729（内部版本 15.0.2.402），发布日期：2018 年 4 月 27 日
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

    - 版本 1.2.6660.39920（内部版本 15.0.2.389），发布日期：2018 年 3 月 28 日
        - Bug 修复
            - 对于 Power BI 报表 (PBIX)，修复在 Power BI 视觉对象中无法正常工作的导出数据
            - 对于 Power BI 报表 (PBIX)，修复无法正常工作的 URL 筛选器
            - 对于分页报表 (RDL)，修复在升级到 Power BI 报表服务器 3 月发行版后在 IE11 中未正确显示的映像

    - 版本 1.2.6648.38132（内部版本 15.0.2.378），发布日期：2018 年 3 月 19 日
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
    - 版本：2.56.5023.1043（2018 年 3 月），发布日期：2018 年 3 月 19 日
        - 包含与 Power BI 报表服务器连接所需的更改（2018 年 3 月）

## <a name="october-2017"></a>2017 年 10 月

- **Power BI 报表服务器**
    - 版本 1.1.6582.41691（内部版本 14.0.600.442），发布日期：2018 年 1 月 10 日
        - 安全更新
        - Bug 修复
            - 修复了 Model.GetParameters 返回 400 的问题
            - 修复了将共享数据集设置为现有分页报表 (RDL) 的问题
            - 修复了将使用不同参数值的报表导出到 PDF 时出现的 ExecutionNotFoundException

    - 版本 1.1.6551.5155（内部版本 14.0.600.438），发布日期：2017 年 12 月 11 日
        - Bug 修复
            - 某些 Power BI Desktop 报表刷新之后无法保存数据。

    - 2017 年 11 月 17 日发布的版本 1.1.6530.30789（生成号 14.0.600.437）
        - Bug 修复
            - 针对基本身份验证方案进行了修复 
            - 修复了以下问题：无法在门户上“订阅”、“缓存刷新计划”和“历史记录快照”的计划页上选择工作日
            - 对于分页报表 (RDL)，修复了以下问题：如果文本框中的表达式将 CanGrow 属性设为 False，则会导致值不显示颜色且字体不正确
            - 对于 Power BI 报表 (PBIX)，修复了以下问题：向折线图添加图例会导致呈现的视觉对象为空

    - 版本 1.1.6514.9163（内部版本 14.0.600.434），发布日期：2017 年 11 月 1 日
        - Bug 修复
            - 对超过 500MB 的 PBIX 报表的上传可靠性问题的修复
            - 对超过 1GB 的 PBIX 报表的数据上传问题的修复

    - 版本 1.1.6513.3500（内部版本 14.0.600.433），发布日期：2017 年 10 月 31 日
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
    - 版本：2.51.4885.3981（2017 年 10 月），发布日期：2018 年 4 月 10 日
        - 安全更新

    - 版本：2.51.4885.2501（2017 年 10 月），发布日期：2018 年 1 月 10 日
        - 安全更新

    - 2017 年 11 月 17 日发布的版本 2.51.4885.1423（2017 年 10 月）
        - Bug 修复
            - 修复了以下问题：32 位 Power BI Desktop 无法在 x86 OS 上运行
            - 对于 Power BI 报表 (PBIX)，修复了 X 轴网格线的显示问题
            - 其他次要缺陷修复

    - 版本：2.51.4885.1041（2017 年 10 月），发布时间：2017 年 10 月 31 日
        - 功能
            - 包含与 Power BI 报表服务器连接所需的更改（2017 年 10 月）

## <a name="june-2017"></a>2017 年 6 月

- **Power BI 报表服务器**
    - 内部版本 14.0.600.309，发布日期：2018 年 1 月 10 日
        - 安全更新

    - 内部版本 14.0.600.305，发布日期：2017 年 9 月 19 日  
        - Bug 修复
            - 更新到最新的[必应地图 Web 控件](https://msdn.microsoft.com/library/mt712542.aspx)

    - 内部版本 14.0.600.301，发布日期：2017 年 7 月 11 日
        - Bug 修复
            - `{{UserId}}` 标记解析为存储的凭据，而不是在 Power BI 报表中执行报表的用户
            - 某些图像无法在 Power BI 报表服务器报表中呈现
            - 无法在 Power BI 报表服务器中更改 Power BI 报表的名称
            - 无法在 Power BI 移动应用程序中加载自定义视觉对象（需要重新安装移动应用以清除本地缓存）

    - 内部版本 14.0.600.271，发布日期：2017 年 6 月 12 日
        - Power BI 报表服务器初始版本

- Power BI Desktop（已针对 Power BI 报表服务器进行优化）
    - 版本：2.47.4766.4901（2017 年 6 月），发布日期：2018 年 1 月 10 日
        - 安全更新

## <a name="next-steps"></a>后续步骤

[什么是 Power BI 报表服务器？](get-started.md)
[管理员概述](admin-handbook-overview.md)  
[安装 Power BI 报表服务器](install-report-server.md)  
[下载报表生成器](https://www.microsoft.com/download/details.aspx?id=53613)  
[下载 SQL Server Data Tools (SSDT)](http://go.microsoft.com/fwlink/?LinkID=616714)

更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)
