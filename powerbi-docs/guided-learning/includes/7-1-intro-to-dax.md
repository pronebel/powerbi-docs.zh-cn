---
ms.openlocfilehash: 6366dbe4d7c58b49b4085d80aa690fd6c64fee59
ms.sourcegitcommit: 226b47f64e6749061cd54bf8d4436f7deaed7691
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/09/2019
ms.locfileid: "70847657"
---
欢迎使用 Power BI **指导学习**部分，它旨在为你介绍 **DAX**。

DAX 代表数据分析表达式，它是在整个 Power BI 中使用（它也由 Power BI 在后台使用）的公式语言。   在 Microsoft 的其他产品也能找到 DAX，如 Power Pivot 和 SSAS 表格，但这些指导学习主题重点介绍如何在 Power BI 中使用 DAX - 你将如何使用它。

## <a name="dax-and-this-guided-learning-video-series"></a>DAX 以及此指导学习视频系列
此指导学习部分的目标是教授 DAX 基础知识和基本原理 - 如何看待 DAX，它的工作原理，以及如一位知名的 DAX 专家 [Alberto Ferrari](http://www.sqlbi.com/learning-dax) 所解释（且凭借大量经验而学得）的那些最有用的功能。 

![Alberto Ferrari 的画像](media/7-1-intro-to-dax/intro_dax_6_alberto_ferrari.png)

在此指导学习部分中的关于 DAX 的视频将从 DAX 公式语言如何工作的视角来讲解 DAX 基础知识。   如果是从零开始创建 DAX 公式时，这就很有用，而且这对于理解当你在**查询编辑器**中创建查询时 Power BI 如何创建这些 DAX 公式也非常有用。

## <a name="in-this-video---introduction-to-dax"></a>在本视频中 - DAX 简介
DAX 概念简单明了，但其功能强大。 DAX 使用一些独特的编程概念和模式，使其难以被充分利用和理解。 传统的学习语言的方法对于 DAX 来说可能不是最好的方法，因此本视频旨在向你讲解有关概念和理论，以便在你以后的 Power BI 工作中提供帮助。

DAX 是一种 *函数语言* ，这意味着完整的执行代码包含在一个函数中。

在 DAX 中，函数可以包含其他内容，例如嵌套函数、条件语句和值引用。 DAX 中的执行从最内部函数或参数开始，逐步向外计算。 在 Power BI 中，DAX 公式在单个行中编写，因此函数的正确格式设置对于可读性很重要。

DAX 的设计用于处理表格，因此它只有两个主要的数据类型：数字和其他。   **数字**可以包括整数  、小数  和货币  。 **其他**可以包括字符串  和二进制对象  。 这意味着如果构建 DAX 函数来处理一种类型的数字，那么可以确定该函数可以处理任何其他数字数据。

DAX 使用运算符重载，这表示可以在计算中混合使用各种数据类型，其结果将根据输入中使用的数据类型进行更改。 转换自动进行，这意味着你无需知道在 Power BI 中使用的列的数据类型，但它还意味着有时转换是以意想不到的方式进行的。 了解你使用的数据是一个不错的做法，这样可以确保运算符按照预期进行工作。

Power BI 中可能经常使用的一种数据类型是：**DateTime**。 **DateTime** 存储为浮点值，包括整数和小数部分。 DateTime 可以用来精确计算 1900 年 3 月 1 日以后的任意时间段。

> 视频内容由 [Alberto Ferrari, SQLBI](http://www.sqlbi.com/learning-dax/?utm_source=powerbi&utm_medium=marketing&utm_campaign=after-summit) 提供
> 
> 

