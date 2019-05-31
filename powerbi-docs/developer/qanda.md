---
title: Power BI Embedded 中的问答
description: Power BI Embedded 提供了一种将问答融入应用的方法，使用户能够使用自然语言提问。
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 11/20/2017
ms.openlocfilehash: afe53e7b24328612bd7858abe263e4365f1c891d
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "61268710"
---
# <a name="qa-in-power-bi-embedded"></a>Power BI Embedded 中的问答

Power BI Embedded 提供了一种将问答融入应用的方法，使用户能够使用自然语言提问并收到视觉对象（例如图表和图形）形式的即时答复。

![嵌入框架中的问答交互式问题](media/qanda/embedded-qanda.gif)

将问答功能嵌入应用的模式有两种，即“交互式”  和“仅结果”  模式。 借助“交互式”  模式，可以键入问题，并让它们显示在视觉对象中。 如果有已保存的问题或要显示的已设置问题，可以在嵌入配置中填充问题，从而使用“仅结果”  模式。

下面是 JavaScript 代码的示例。

```javascript
// Embed configuration used to describe the what and how to embed.
// This object is used when calling powerbi.embed within the JavaScript API.
// You can find more information at https://github.com/Microsoft/PowerBI-JavaScript/wiki/Embed-Configuration-Details.
var config= {
    type: 'qna',
    tokenType:   models.TokenType.Embed | models.TokenType.Aad,
    accessToken: access token value,
    embedUrl:    https://app.powerbi.com/qnaEmbed (groupId to be appended as query parameter if required),
    datasetIds:  array of requested data set ids (at the moment we support only one dataset),
    viewMode:    models.QnAMode.Interactive | models.QnAMode.ResultOnly,
    question:    optional parameter for Explore mode (QnAMode.Interactive) and mandatory for Render Result mode (QnAMode.ResultOnly)
};

// Get a reference to the embedded QNA HTML element
var qnaContainer = $('#qnaContainer')[0];

// Embed the QNA and display it within the div container.
var qna = powerbi.embed(qnaContainer, config);
```

## <a name="set-question"></a>已设置问题

如果将“结果模式”  与已设置问题结合使用，可以将其他问题注入框架，并立即显示这些问题的解答，从而替换之前的结果。 与新问题匹配的新视觉对象将呈现。

此用法的一个示例是常见问题列表。 用户可以浏览这些问题并在同一个嵌入部分中进行回答。

JS SDK 用法的代码片段：   

```javascript
// Get a reference to the embedded Q&A HTML element
var qnaContainer = $('#qnaContainer')[0];

// Get a reference to the embedded Q&A.
qna = powerbi.get(qnaContainer);

qna.setQuestion("This year sales")
    .then(function (result) {
        …….
    })
    .catch(function (errors) {
        …….
    });
```

## <a name="visual-rendered-event"></a>视觉对象呈现的事件

对于“交互式”  模式，每当呈现的视觉对象发生更改以在键入更新的输入查询时针对该更新查询，则会通过数据更改事件通知应用。

通过侦听 visualRendered  事件，可以保存问题，以供日后使用。 

JS SDK 用法的代码片段：   

```javascript
// Get a reference to the embedded Q&A HTML element
var qnaContainer = $('#qnaContainer')[0];

// Get a reference to the embedded Q&A.
qna = powerbi.get(qnaContainer);

// qna.off removes a given event listener if it exists.
qna.off("visualRendered");

// qna.on will add an event listener.
qna.on("visualRendered", function(event) {
     …….
});
```

## <a name="embed-token"></a>嵌入令牌

创建数据集的嵌入令牌以启动问答部分。 有关详细信息，请参阅[生成令牌](https://docs.microsoft.com/rest/api/power-bi/embedtoken)。

## <a name="next-steps"></a>后续步骤

若要尝试问答嵌入，请查看 [JavaScript 嵌入示例](https://microsoft.github.io/PowerBI-JavaScript/demo/)。

更多问题？ [尝试咨询 Power BI 社区](http://community.powerbi.com/)
