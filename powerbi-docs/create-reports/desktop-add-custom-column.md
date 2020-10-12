---
title: 在 Power BI Desktop 中添加自定义列
description: 在 Power BI Desktop 中快速创建新自定义列
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 10/18/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 2074094f910efa36d449d8f54ada097d253bb2dd
ms.sourcegitcommit: 51b965954377884bef7af16ef3031bf10323845f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/30/2020
ms.locfileid: "91598912"
---
# <a name="add-a-custom-column-in-power-bi-desktop"></a>在 Power BI Desktop 中添加自定义列

在 Power BI Desktop 中，可以使用查询编辑器轻松地向模型添加新的自定义数据列。 利用查询编辑器，可以创建和重命名自定义列，从而创建 [PowerQuery M 公式查询](/powerquery-m/quick-tour-of-the-power-query-m-formula-language)，用于定义自定义列。 PowerQuery M 公式查询包含[全面的函数引用内容集](/powerquery-m/power-query-m-function-reference)。 

在查询编辑器中创建自定义列时，Power BI Desktop 会将其作为“应用的步骤”添加到查询的“查询设置”中   。 可随时对其进行更改、移动或修改。

![屏幕截图显示“添加自定义列”对话框。](media/desktop-add-custom-column/add-custom-column_01.png)

## <a name="use-query-editor-to-add-a-custom-column"></a>使用查询编辑器添加自定义列

若要开始创建自定义列，请执行以下步骤：

1. 启动 Power BI Desktop 并加载一些数据。

2. 从功能区上的“主页”选项卡中，选择“编辑查询”，然后从菜单中选择“编辑查询”    。

   ![选择“编辑查询”](media/desktop-add-custom-column/add-column-from-example_02.png)

   此时显示“查询编辑器”窗口  。 

2. 在功能区的“添加列”选项卡中，选择“自定义列”   。

   ![选择自定义列](media/desktop-add-custom-column/add-custom-column_02.png)

   此时显示“添加自定义列”窗口  。

## <a name="the-add-custom-column-window"></a>“添加自定义列”窗口

“添加自定义列”窗口具有以下功能  ： 
- 可用列的列表，位于右侧的“可用列”列表  。

- 自定义列的初始名称，位于“新列名”框中  。 可重命名此列。

- [PowerQuery M 公式查询](/powerquery-m/power-query-m-function-reference)，位于“自定义列公式”框中  。 可通过生成用于定义新自定义列的公式来创建这些查询。 

   ![屏幕截图显示“添加自定义列”对话框，其中包含可供选择的列。](media/desktop-add-custom-column/add-custom-column_03.png)

## <a name="create-formulas-for-your-custom-column"></a>创建自定义列的公式

1. 可以从右侧的“可用列”列表中选择一列，然后选择列表下方的“插入”，将其添加到自定义列公式中   。 还可以通过在列表中双击列来添加该列。

2. 输入公式并生成列后，请注意“添加自定义列”窗口底部的指示器  。 

   如果未发生错误，会显示绿色选中标记，并显示消息“未检测到语法错误”  。

   ![成功的“添加自定义列”页语法检查](media/desktop-add-custom-column/add-custom-column_04.png)

   如果出现语法错误，会显示黄色警告图标，及指向公式中错误位置的链接。

   ![“添加自定义列”页上的错误](media/desktop-add-custom-column/add-custom-column_05.png)

3. 选择“确定”。  

   Power BI Desktop 将自定义列添加到模型中，并将“已添加的自定义”步骤添加到“查询设置”中查询的“应用的步骤”列表中    。

   ![添加到查询设置的自定义列](media/desktop-add-custom-column/add-custom-column_06.png)

4. 若要修改自定义列，请在“应用的步骤”列表中双击“已添加的自定义”步骤   。 

   此时显示“添加自定义列”窗口，其中包含已创建的自定义列公式  。

## <a name="use-the-advanced-editor-for-custom-columns"></a>为自定义列使用高级编辑器

创建查询后，还可以使用“高级编辑器”修改查询的任何步骤  。 为此，请执行下列步骤：

1. 在“查询编辑器”窗口中，选择功能区上的“视图”选项卡   。 

2. 选择**高级编辑器**。

   此时显示“高级编辑器”页，可使你完全控制查询  。 

   ![“高级编辑器”页](media/desktop-add-custom-column/add-custom-column_07.png)

   
## <a name="next-steps"></a>后续步骤

- 还可以通过其他方法创建自定义列，例如根据你向查询编辑器提供的示例创建列。 有关详细信息，请参阅[在 Power BI Desktop 中通过示例添加列](desktop-add-column-from-example.md)。

- 有关 Power Query M 引用信息，请参阅 [Power Query M 函数引用](/powerquery-m/power-query-m-function-reference)。