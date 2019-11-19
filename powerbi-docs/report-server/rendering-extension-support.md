---
title: 符合 ISO 14289-1 标准的 PDF 呈现扩展插件 — Power BI 报表服务器
description: 本文档介绍符合 ISO 14289-1 (PDF/UA) 规范的 Power BI 报表服务器和 SQL Reporting Services PDF 呈现扩展插件。
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 11/04/2019
ms.author: maggies
ms.openlocfilehash: c800ee995bc3c03b3cbcda91503e6dea9495f6b5
ms.sourcegitcommit: 721cf375627b010e8ad12c4c668295f38d450a17
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/06/2019
ms.locfileid: "73638071"
---
# <a name="pdf-rendering-extension-conformance-to-iso-14289-1---power-bi-report-server"></a>符合 ISO 14289-1 标准的 PDF 呈现扩展插件 — Power BI 报表服务器 

适用于：Power BI 报表服务器和 SQL Reporting Services

本文档介绍符合 [ISO 14289-1 (PDF/UA)](https://www.pdfa.org/publication/pdfua-in-a-nutshell/) 规范的 Power BI 报表服务器和 SQL Reporting Services PDF 呈现扩展插件。

> [!NOTE]
> 可以从浏览器中选择“打印”，然后选择“另存为 PDF”，以保存或打印此白皮书   。

## <a name="1--scope"></a>1.范围

不适用

## <a name="2--normative-references"></a>2.参考标准

不适用

## <a name="3--terms-and-definitions"></a>3.术语和定义

不适用

## <a name="4--notation"></a>4.图解

不适用

## <a name="5-version-identification"></a>5.版本标识

如本文档所述，PDF 呈现扩展插件支持 PDF/UA。 在如下所述的某些情况下，用户需要采取措施来确保 PDF 完全符合 PDF/UA 标准。  我们希望用户在此过程的最后一步添加适当的 PDF/UA 版本和一致性标识符，表明已完成必要的工作使 PDF 完全符合 PDF/UA 标准。

本文档中列出的所有内容均基于以下前提：通过将设备信息设置 AccessiblePdf 设为 `true` 来呈现 PDF 文档。 在某些情况下，符合性限制是由于报表定义语言 (RDL) 中的限制所致。

## <a name="6--conformance-requirements"></a>6.一致性要求

|     标准     |     支持功能     |     备注      |
|----|--------|--------|
|    6.1 常规    |                 支持    |    PDF 呈现扩展插件创建 PDF 版本 1.7。    |
|    6.2 符合文件要求    |                 支持但有例外    |    请参阅第 7 节“文件格式要求”中的备注。    |
|    6.3 符合读者要求    |     不适用     |         |
|    6.4 符合辅助技术的要求    |     不适用     |         |

## <a name="7--file-format-requirements"></a>7.文件格式要求

|     标准     |     支持功能     |     备注      |
|-----|-------|------------------------|
|    7.1 常规    |                 支持但有例外    |    所有真实内容都应按照 ISO 32000-1:2008, 14.8 中的定义进行标记。 不应在结构树中标记工件 (ISO 32000-1:2008, 14.8.2.2.2)。 <li> PDF 呈现扩展插件不能灵活地将单个项目显式标记为工件，因此它会将与 ISO 32000-1:2008, 14.8.2.2.2 中的标准对应的所有内容都工件化。<br>内容应按逻辑阅读顺序在结构树中用符合语义的标记进行标记。 <br> **注释** 4 WCAG 2.0 准则 1.4 解释了有关辅助功能的对比度、颜色和其他格式设置的问题。 <br><li> 用户需要确保其文档不受这些问题的影响。 <br>ISO 32000-1:2008, 14.8.4 中定义的标准标记不得重新映射。 <li> PDF 呈现扩展插件不会重新映射标准标记。 文档以 Document 根元素开头。 <br>声称符合此国际标准的文件的 Suspects 值应为 false（ISO 32000-1:2008 表 321）。 <li> PDF 呈现扩展插件没有 Suspects 条目。 此属性是可选的。    |
|    7.2 文本    |                 支持但有例外    |    内容应按逻辑阅读顺序进行标记。 对于文档内容中的每个逻辑元素，应使用最符合语义的标记。 <br><li> PDF 呈现扩展插件尽可能按逻辑阅读顺序对内容进行标记。<br>如 ISO 32000-1:2008, 14.8.2.4.2 中所述，字符代码应映射到 Unicode。 Unicode 规范中未包含的字符可以使用 Unicode 专用区或声明其他字符编码。 <br>自然语言应按 ISO 32000-1:2008, 14.9.2 和/或 ISO 32000-1:2008, 7.9.2 中所述进行声明。 应声明自然语言中的更改。 如 ISO 32000-1:2008, 14.9.2.2 中所述，文本字符串内（例如，替代说明内）自然语言的更改应使用语言标识符进行声明。 <br><li> PDF 呈现扩展插件仅在文档级别声明自然语言    |
|    7.3 图形    |                 支持但有例外    |    如 ISO 32000-1:2008, 14.8.4.5, 表 340 中所述，除文本对象以外的图形对象应使用 Figure 标记进行标记。 如果存在以下任何例外，则应将图形标记为工件： <br><li> 图形不代表有意义的内容，或者 <li>  图形显示为链接批注的背景，在这种情况下，链接上的替代文本应同时描述图形和链接。 <li> PDF 呈现扩展插件使用 Figure 标记来标记图形对象。 <br>图形附带的描述文字应加上 Caption 标记。 <li> PDF 呈现扩展插件当前不使用 Caption 标记来标记图形上的描述文字。 <br>如 ISO 32000-1:2008, 14.7.2, 表 323 中所述，Figure 标记应包含替代表示形式或替换文本，以表示带有 Figure 标记的内容。 <br>**注释** 1 另请参阅 WCAG 2.0 准则 1.1。 <br>如果用图形表示的文本不是供人类阅读的自然语言文本，则应提供描述图形性质或用途的替代文本。 <br>**注释** 2 作为键入示例或某种语言所用的书写系统示例​​的文本是非自然语言的文本示例。   PDF 呈现扩展插件支持图形上的替换文本，但用户可以添加替换文本。 <br>有关 BBox 属性的其他说明： <br><li> PDF 呈现扩展插件当前不写入 BBox 属性。 <li> 一种解决方法是将插图手动重新标记为新图形或工件。    |
|    7.4 标题    |                 不适用    |    RDL 不支持以任何方式标记标题。 用户可以根据需要对其进行标记。    |
|    7.5 表    |                 支持但有例外    |    表应包含标头。 表头应根据 ISO 32000-1:2008 表 337 和表 349 进行标记。 <br>**注释** 1 表可以包含列标头和/或行标头。 <br>**注释** 2 当依赖辅助技术时，需要提供尽可能多的有关表结构的信息。 标头在提供结构信息方面起着重要作用。 <br><li> 用户可以在表中包含标头。 RDL 和 PDF 呈现扩展插件支持行标头。 <br>  TH 类型的结构元素应具有 Scope 属性。   <li> 对于列成员和行成员，PDF 呈现扩展插件在 TH 元素上包含 Scope 属性，但对于角落单元格，则不包含。<br>表标记结构只能用于标记逻辑行和/或列关系中显示的内容。   <li> 这取决于用户选择如何在其 RDL 中使用表。    |
|    7.6 列表    |                 不适用    |    RDL 不支持标记列表。 在 RDL 中，它们在结构上是只包含一个表格单元格的表。 <br>用户可以根据需要重新对其进行标记。    |
|    7.7 数学表达式    |                 支持但有例外    |    所有数学表达式均应包含在 Formula 标记内（如 ISO 32000-1:2008, 14.8.4.5 中详述的那样），并且应具有 Alt 属性。 <br><li> PDF 呈现扩展插件当前不将数学表达式包含在 Formula 标记内。 <br>按照 ISO 32000-1:2008, 9.10.2 和 14.8.2.4 中的规定，有关将字符映射到 Unicode 的要求应适用于数学表达式。 <br><li> PDF 呈现扩展插件对此提供支持。    |
|    7.8 页眉和页脚    |                 支持    |    如 ISO 32000-1:2008, 14.8.2.2.2, 表 330 中所述，每页页眉和页脚应标识为分页工件，并应分类为页眉或页脚子类型。 <br><li> 页眉或页脚被视为并标记为工件。    |
|    7.9 注释和引用    |                 不适用    |    PDF 呈现扩展插件不支持标记注释和引用。 <br>用户可以根据需要对其进行标记。    |
|    7.10 可选内容    |                 不适用    |         |
|    7.11 嵌入式文件    |                 不适用    |         |
|    7.12 文章主线    |                 不适用    |         |
|    7.13 数字签名    |                 不适用    |         |
|    7.14 非交互式窗体    |                 不适用    |         |
|    7.15 XFA    |                 不适用    |         |
|    7.16 安全性    |                 不适用    |         |
|    7.17 导航    |                 支持    |    文档应包含与导航目标的阅读顺序和级别相匹配的文档大纲 (ISO 32000-1:2008, 12.3.3)。 <br><li> RDL 支持报表项的书签，但用户必须选择此选项。 然后，PDF 呈现扩展插件会将这些书签呈现为文档大纲。 <br>如果存在 PageLabels 编号树（ISO 32000-1:2008, 7.7.2, 表 28），其中的条目应符合语义。 <br><li> PDF 呈现扩展插件不包含 PageLabels 编号树。    |
|    7.18 批注    |                 不适用    |    RDL 不支持批注    |
|    7.21 字体    |                 支持    |         |
|    7.21.1 常规    |                 支持    |         |
|    7.21.2 字体类型    |                 支持    |         |
|    7.21.3 复合字体    |                 支持    |         |
|    7.21.3.1 常规    |                 支持    |         |
|    7.21 3.2 CIDFonts    |                 支持    |         |
|    7.21.3.3 CMaps    |                 支持    |         |
|    7.21.4 嵌入    |                 支持    |         |
|    7.21.4.1 常规    |                 支持    |         |
|    7.21.4.2 子集嵌入    |                 支持    |         |
|    7.21.5 字体指标    |                 支持    |         |
|    7.21.6 字符编码    |                 支持    |         |
|    7.21.7 Unicode 字符映射    |                 支持    |         |
|    7.21.8 .notdef 字形的使用    |                 支持    |         |

## <a name="8--conforming-reader-requirements"></a>8.符合读者要求

不适用

## <a name="9--at-requirements"></a>9.AT 要求

不适用

## <a name="disclaimer"></a>Disclaimer

© 2017 Microsoft Corporation. All rights reserved. The names of actual companies and products mentioned herein may be the trademarks of their respective owners. The information contained in this document represents the current view of Microsoft Corporation on the issues discussed as of the date of publication. Microsoft cannot guarantee the accuracy of any information presented after the date of publication. Microsoft regularly updates its websites with new information about the accessibility of products as that information becomes available.

Customization of the product voids this conformance statement from Microsoft. Please consult with Assistive Technology (AT) vendors for compatibility specifications of specific AT products.

This document is for informational purposes only. MICROSOFT MAKES NO WARRANTIES, EXPRESS OR IMPLIED, IN THIS DOCUMENT.


## <a name="next-steps"></a>后续步骤
[管理员概述](admin-handbook-overview.md)  

更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)

