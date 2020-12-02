---
title: 了解支持哪些 Python 包
description: Power BI 中支持的和不支持的 Python 包
author: otarb
ms.author: otarb
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: conceptual
ms.date: 06/26/2020
LocalizationGroup: Connect to data
ms.openlocfilehash: 07b16bb90b548f071472f9f7d22095ccdff78f56
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/01/2020
ms.locfileid: "96401710"
---
# <a name="create-visuals-by-using-python-packages-in-the-power-bi-service"></a>在 Power BI 服务中使用 Python 包创建视觉对象
可以使用功能强大的 [Python 编程语言](https://www.python.org/)在 Power BI 服务中创建视觉对象。 许多 Python 包在 Power BI 服务中受支持，并且更多包始终受支持。

以下各部分提供一个按字母顺序排列的表，介绍在 Power BI 中受支持的 Python 包。 

## <a name="request-support-for-a-new-python-package"></a>请求获取新的 Python 包的支持
可以在下一节中找到“Power BI 服务”支持的 Python 包，标题为“支持的包”。 如果想要请求未在该列表中找到的 Python 包的支持，请将你的请求提交至 [Power BI 意见](https://ideas.powerbi.com)。

## <a name="requirements-and-limitations-of-python-packages"></a>Python 包的要求和限制
Python 包具有大量要求和限制：

* 当前 Python 运行时：Python 3.7.7。
* Power BI 服务主要支持带有免费和开源软件许可证（例如 GPL-2、GPL-3、MIT+R 等）的 Python 包。
* Power BI 服务支持已在 PyPI 发布的包。 此服务不支持专用或自定义 Python 包。 建议用户在请求使用 Power BI 服务中提供的包之前，先在 PyPI 上公布其私有包。
* 对于 Power BI Desktop 中的 Python 视觉对象，可以安装任意包，包括自定义 Python 包。
* 出于安全和隐私考虑，该服务不支持通过万维网提供客户端到服务器查询的 Python 包。 系统会阻止联网进行此类尝试。
* 纳入新的 Python 包的审核流程具有一系列的依赖项；需要在服务中安装的某些依赖项不受支持。

## <a name="python-packages-that-are-supported-in-power-bi"></a>在 Power BI 中受支持的 Python 包
下表显示 Power BI 服务中 **受支持** 的程序包。


|        程序包        |   版本   |                                   链接                                   |
|-----------------------|-------------|--------------------------------------------------------------------------|
|matplotlib|3.2.1|https://pypi.org/project/matplotlib|
|numpy|1.18.4|https://pypi.org/project/numpy|
|pandas|1.0.1|https://pypi.org/project/pandas|
|scikit-learn|0.23.0|https://pypi.org/project/scikit-learn|
|scipy|1.4.1|https://pypi.org/project/scipy|
|s  eaborn|0.10.1|https://pypi.org/project/seaborn|
|statsmodels|0.11.1|https://pypi.org/project/statsmodels|
|xgboost|1.1.0|https://pypi.org/project/xgboost|

## <a name="next-steps"></a>后续步骤
查看以下文章，了解有关 Power BI 中的 Python 的详细信息：

* [使用 Python 创建 Power BI 视觉对象](desktop-python-visuals.md)
* [在 Power BI Desktop 中运行 Python 脚本](desktop-python-scripts.md)
* [在查询编辑器中使用 Python](desktop-python-in-query-editor.md)
