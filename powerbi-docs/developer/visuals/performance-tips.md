---
title: 性能提示
description: 如何生成高性能 Power BI 视觉对象
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 04/20/2020
ms.openlocfilehash: 7ebc02b2c459517957425e78438e12e89dc2e1bb
ms.sourcegitcommit: 1059c6222458f189fb5301dcb689dad2b2c00bc1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2020
ms.locfileid: "82196551"
---
# <a name="how-to-build-a-high-performance-power-bi-visual"></a>如何生成高性能 Power BI 视觉对象
本文将介绍有关开发人员在呈现视觉对象时如何实现高性能的技术。 

任何人都不希望视觉对象将时间花费在呈现上，从代码中压榨每一分性能在呈现时变得至关重要。 

> [!NOTE]
> 随着我们不断改进和增强平台，新版本的 API 会不断发布。 若要充分利用 Power BI 视觉对象的平台和功能集，建议使用最新版本来保持最新状态。
>
> 由于最新版本 2.1  ，Power BI 视觉对象加载时间平均缩短了 20%。

## <a name="power-bi-visual-performance-tips"></a>Power BI 视觉对象性能提示
下面是有关如何实现最佳视觉对象性能的一些建议。 

### <a name="use-user-timing-api"></a>使用用户计时 API
使用用户计时 API  度量应用的 JavaScript 性能可帮助确定需要优化的脚本部分。

有关详细信息，请参阅[用户计时 API](https://msdn.microsoft.com/library/hh772738(v=vs.85).aspx)。

### <a name="review-animation-loops"></a>查看动画循环
动画循环是否会重绘未更改的元素？ 

 - 问题：这会浪费时间来绘制不会逐帧更改的元素。

 - 解决方案：有选择地更新帧。 
 
当需要对静态可视化效果进行动画处理时，将绘制代码集中到一个更新函数中，并为动画循环的每次迭代使用新数据重复调用它，这十分吸引人。

改为考虑以下更新模式，使用视觉对象构造函数方法绘制所有静态内容，然后更新函数只需要绘制更改的可视化效果元素。 

   > [!TIP]
   > 低效的动画循环通常出现在轴和图例中。

### <a name="cache-dom-nodes"></a>缓存 DOM 节点 
从 DOM 检索节点或节点列表时，需要考虑是否可以在以后的计算（有时甚至是下一次循环迭代）中重用它们。 只要不需要在相关区域添加或删除其他节点，缓存它们便可以提高应用程序的整体效率。

若要确保代码速度快且不会降低浏览器的速度，请将 DOM 访问保持在最低限度。 

- 早于: 

   ```javascript
   public update(options: VisualUpdateOptions) { 
       let axis = $(".axis"); 
   }
   ```

- 晚于： 

   ```javascript
   public constructor(options: VisualConstructorOptions) { 
       this.$root = $(options.element); 
       this.xAxis = this.$root.find(".xAxis"); 
   } 
 
   public update(options: VisualUpdateOptions) { 
       let axis = this.axis; 
   }
   ```

### <a name="avoid-dom-manipulation"></a>避免 DOM 操作 
尽可能限制 DOM 操作。  插入操作（如 `prepend()`、`append()` 和 `after()`）非常耗时，除非必要，否则不应使用。

例如：

  ```javascript
  for (let i=0; i<1000; i++) { 
      $('#list').append('<li>'+i+'</li>');
  }
  ```

可以通过使用 `html()` 并预先生成列表来加快上面的示例： 

  ```javascript
  let list = ''; 
  for (let i=0; i<1000; i++) { 
      list += '<li>'+i+'</li>'; 
  } 

  $('#list').html(list); 
  ```

### <a name="reconsider-jquery"></a>重新考虑 JQuery

尽可能限制 JS 框架并使用本机 JS 可以增加可用带宽并降低处理开销。 这也可以限制与较旧浏览器的兼容性问题。 

有关详细信息，请参阅 [youmightnotneedjquery.com](http://youmightnotneedjquery.com/)，以获取 JQuery `show`、`hide`、`addClass` 等函数的替代示例。  

### <a name="use-canvas-or-webgl"></a>使用画布或 WebGL 
若要重复使用动画，请考虑使用画布  或 WebGL  而不是 SVG。 与 SVG 不同，使用这些选项时，性能取决于大小而不是内容。 

若要详细了解差别，请参阅 [SVG 与画布：如何选择](https://msdn.microsoft.com/library/gg193983(v=vs.85).aspx)。 

### <a name="use-requestanimationframe-instead-of-settimeout"></a>使用 requestAnimationFrame 而不是 setTimeout 
如果使用 [requestAnimationFrame](https://www.w3.org/TR/animation-timing/) 更新屏幕动画，则会在浏览器调用另一个重新绘制  之前调用动画函数。

有关详细信息，请参阅有关使用 `requestAnimationFrame` 平滑动画的此[示例](https://testdrive-archive.azurewebsites.net/Graphics/RequestAnimationFrame/Default.html)。

## <a name="next-steps"></a>后续步骤

在 [Power BI 优化指南](/power-bi/guidance/power-bi-optimization)中详细了解优化技术。
