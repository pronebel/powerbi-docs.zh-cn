---
ms.openlocfilehash: cd6ea6fd52f929e2cd254214cf0e8c96e858f6c2
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "61273188"
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

> 视频内容由 [Alberto Ferrari, SQLBI](http://www.sqlbi.com/learning-dax) 提供
> 
> 

