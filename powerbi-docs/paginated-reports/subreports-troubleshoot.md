---
title: 排除 Power BI 分页报表中的子报表故障
description: 了解使用子报表（分页报表内的报表项）时的常见问题解决方案。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: troubleshooting
ms.date: 04/29/2020
ms.openlocfilehash: 6a0e90036b759c409a9f5b3e994571c2a0eb510c
ms.sourcegitcommit: 6bc66f9c0fac132e004d096cfdcc191a04549683
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/06/2020
ms.locfileid: "91747496"
---
# <a name="troubleshoot-subreports-in-power-bi-paginated-reports"></a>排除 Power BI 分页报表中的子报表故障

有时，使用分页报表中的子报表时可能会出现非预期结果，或子报表功能不按预期工作。 本文针对使用子报表时遇到的常见问题提供解决方案。 子报表是在主分页报表的表体中显示其他报表的报表项  。 如需了解更多背景信息，请参阅[排除 Power BI 分页报表中的子报表故障](subreports.md)。

## <a name="subreport-couldnt-be-found"></a>找不到子报表

**说明：** 子报表未呈现。 而是显示一条错误消息。

### <a name="message"></a>消息

“在指定位置 CustomerDetails 处找不到子报表 Subreport1。 请验证子报表是否已发布且名称是否正确。”

### <a name="possible-reasons"></a>可能的原因

- 具有指定名称的子报表在与主报表相同的工作区或应用中不存在。
- 用户无权访问这个子报表。
- 主报表中的子报表数已达到子报表限额（50 个子报表）。

### <a name="troubleshooting-steps"></a>疑难解答步骤

**在工作区中**

- 请验证是否存在错误消息所述名称的报表。 此名称不区分大小写。

**在应用中**

- 请验证应用中是否存在错误消息所述名称的报表。 请与应用作者联系，寻求进一步的帮助。

**如果已共享报表**

1. 请验证错误消息所述名称的报表是否已与你共享。
2. 如果报表存在，请验证主报表和子报表的所有者姓名是否相同。 了解这些信息之后，请与主报表的所有者联系。

## <a name="subreport-renders-with-unexpected-content"></a>子报表已呈现，但出现意外的内容

### <a name="possible-reason"></a>可能的原因

Power BI 允许用户在同一工作区中使用具有相同名称的多个报表

### <a name="troubleshooting-steps-for-report-authors"></a>故障排除步骤（对于报表作者）

1. 在 Power BI Report Builder 中打开主报表并确定子报表的名称。
2. 在工作区中查找具有相同名称的报表。
3. 找到所需的报表并重命名其余报表。

**对于非作者：** 请联系作者。

## <a name="data-retrieval-fails"></a>数据检索失败

**说明：** 显示子报表时，数据检索失败。 子报表未呈现。 而是显示一条错误消息。

### <a name="message"></a>消息

“对 InvoiceDetails 处的子报表 Subreport1 的数据检索失败。 请查看日志文件了解详细信。”

### <a name="troubleshooting-steps"></a>疑难解答步骤

此类问题的故障排除步骤与具有数据访问问题的报表的常规故障排除步骤相同。

## <a name="rendering-fails-unspecified-parameters"></a>呈现失败：未指定参数

**说明：** 由于未指定参数，子报表呈现失败。 子报表具有必选参数，但主报表未设置所有参数。

### <a name="message"></a>消息 
“位于‘SubreportAWithDS’的子报表‘Subreport1’有一个或多个参数没有指定。”

### <a name="troubleshooting-steps-for-the-report-author"></a>故障排除步骤（对于报表作者）

1. 在 Power BI Report Builder 中打开主报表
2. 在 Power BI Report Builder 中打开子报表
3. 验证在主报表中的子报表项内传递的参数集是否与子报表中的参数集匹配。

**对于非作者：** 请联系作者。

## <a name="rendering-fails-recursion-limit"></a>呈现失败：递归限制

**说明：** 由于递归限制，子报表呈现失败。 子报表的嵌套深度不能超过 20 层。

### <a name="message"></a>消息

“报表或子报表有一个递归子报表‘Subreport1’超过了所允许的递归限制最大值。”

### <a name="troubleshooting-steps-for-report-authors"></a>故障排除步骤（对于报表作者）

- 减少嵌套。
- 重新设计报表结构。

## <a name="other-errors"></a>其他错误

**说明：** 不属于前面任何类别的错误。

### <a name="message"></a>消息

“错误:无法显示子报表。”

### <a name="possible-reasons"></a>可能的原因

- 呈现子报表时出现多个错误，例如，参数与数据检索问题不匹配。
- 意外错误。

### <a name="troubleshooting-steps-for-report-authors"></a>故障排除步骤（对于报表作者）

1. 请验证子报表是否可以直接呈现。
2. 如果子报表可以呈现，请检查子报表和主报表中的参数。
3. 请确保主报表包含的独特子报表不超过 50 个，并且子报表的嵌套深度不超过 20 层。
4. 如果无法解决该问题，请与 Power BI 支持人员联系。

**对于非作者：** 请联系作者。

## <a name="next-steps"></a>后续步骤

[Power BI 分页报表中的子报表](subreports.md)

[在 Power BI 服务中查看分页报表](../consumer/paginated-reports-view-power-bi-service.md)

更多问题？ [尝试参与 Power BI 社区](https://community.powerbi.com/)
