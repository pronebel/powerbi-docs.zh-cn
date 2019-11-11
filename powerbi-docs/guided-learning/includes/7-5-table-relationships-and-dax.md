---
ms.openlocfilehash: 679c3e8c3d94c93899e9dcfae1e57f4b678fb218
ms.sourcegitcommit: a5853ef44ed52e80eabee3757bb6887fa400b75b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2019
ms.locfileid: "73799697"
---
Power BI 可以让你在多个表（包括来自完全不同数据源的表）之间建立关系。 你可以在 Power BI Desktop 的“关系”  视图中看到任何数据模型的关系。

![](media/7-5-table-relationships-and-dax/dax-relationships_1.png)

## <a name="dax-relational-functions"></a>DAX 关系函数
DAX 具有让你可以与建立了关系的表进行互动的**关系函数**。

你可以返回列值，或者使用 DAX 函数返回某一关系中的所有行。

例如，RELATED 函数依照关系返回列值，而 RELATEDTABLE 依照关系返回经过筛选的只包含相关行的整个表   。

![](media/7-5-table-relationships-and-dax/dax-relationships_2.png)

**RELATED** 函数处理多对一  的关系，而 **RELATEDTABLE** 函数处理 *一对多* 的关系。

你可以使用关系函数生成包含跨多个表的值的表达式。 DAX 将返回这些函数的一个结果，而不会考虑关系链的长度。

> 视频内容由 [Alberto Ferrari, SQLBI](https://www.sqlbi.com/learning-dax) 提供
> 
> 

