---
title: 合并 Power BI Desktop 中的文件（二进制文件）
description: 轻松合并 Power BI Desktop 中的文件（二进制文件）数据源
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/13/2020
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 07381461375ea7b9707b91c807e92cdb85c1d440
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "76161059"
---
# <a name="combine-files-binaries-in-power-bi-desktop"></a>合并 Power BI Desktop 中的文件（二进制文件）

下面是将数据导入 Power BI Desktop  的强大方法：如果有多个具有相同架构的文件，请将它们合并到单个逻辑表中。 这种常用的技术已变得更加方便和广泛。

若要从同一文件夹中启动合并文件的过程，请选择“获取数据”  、“文件”   > “文件夹”  ，然后选择“连接”  。

![连接到文件夹文件、“获取数据”对话框、Power BI Desktop](media/desktop-combine-binaries/combine-binaries_1.png)

输入文件夹路径，选择“确定”  ，然后选择“转换数据”  以在 Power Query 编辑器中查看该文件夹的文件。

## <a name="combine-files-behavior"></a>合并文件行为

若要在 Power Query 编辑器中合并二进制文件，请选择“内容”  （第一个列标签），然后选择“主页”   > “合并文件”  。 或者，只需选择“内容”  旁边的“合并文件”  图标。

![“合并文件”命令、Power Query 编辑器、Power BI Desktop](media/desktop-combine-binaries/combine-binaries_2a.png)

*合并文件*转换执行如下操作：

* 合并文件转换分析每个输入文件，以确定要使用的正确文件格式，如文本  、Excel 工作簿  或 JSON 文件  。
* 借助转换，可以从第一个文件选择特定对象，比如要提取的 Excel 工作簿。
  
  ![“合并文件”对话框、Power Query 编辑器、Power BI Desktop](media/desktop-combine-binaries/combine-binaries_3.png)
* 合并文件转换后，会自动执行以下操作：
  
  * 创建在单个文件中执行所有所需提取步骤的示例查询。
  * 创建功能查询，该功能查询将参数化示例查询的文件/二进制文件输入。   将示例查询和功能查询进行链接，以在功能查询中反映对示例查询所做的更改。
  * 将函数查询  应用于包含输入二进制文件的原始查询，如文件夹  查询。 它将函数查询应用于每一行的二进制输入，然后将生成的数据提取作为顶级列展开。

    ![合并文件转换结果、Power Query 编辑器、Power BI Desktop](media/desktop-combine-binaries/combine-binaries_4.png)

> [!NOTE]
> Excel 工作簿中的选择范围将影响合并二进制文件的行为。 例如，可以选择特定的工作表来合并该工作表，或者选择根目录来合并整个文件。 选择文件夹将合并该文件夹中找到的文件。 

借助合并文件行为，可以轻松合并给定文件夹内的所有文件，前提是它们具有相同的文件类型和结构（如同一列）。

此外，还可以通过修改自动创建的示例查询轻松应用其他转换或提取步骤，而无需担心修改或创建其他功能查询步骤。 对示例查询所做的任何更改都会在链接的功能查询中自动生成。

## <a name="next-steps"></a>后续步骤

可以使用 Power BI Desktop 连接到各种数据。 有关数据源的详细信息，请参阅下列资源：

* [什么是 Power BI Desktop？](desktop-what-is-desktop.md)
* [Power BI Desktop 中的数据源](desktop-data-sources.md)
* [使用 Power BI Desktop 成型和合并数据](desktop-shape-and-combine-data.md)
* [通过 Power BI Desktop 连接到 CSV 文件](desktop-connect-csv.md)
* [直接将数据输入到 Power BI Desktop 中](desktop-enter-data-directly-into-desktop.md)
