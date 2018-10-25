---
title: 使用 Power BI Desktop 中的形状地图（预览版）
description: 使用 Power BI Desktop 中的形状地图创建区域的相对比较
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 09/11/2018
ms.author: mihart
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 71dbdd79e6bedee3f1377f0e7c29fcc6efbbba03
ms.sourcegitcommit: ce8332a71d4d205a1f005b703da4a390d79c98b6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/27/2018
ms.locfileid: "47417317"
---
# <a name="shape-maps-in-power-bi-desktop-preview"></a>Power BI Desktop 中的形状地图（预览版）
创建“形状地图”视觉对象以使用颜色比较地图上的区域 与“地图”视觉对象不同，“形状地图”无法在地图上显示数据点的精确地理位置。 相反，其主要目的是通过不同方式对地图上的区域着色来显示这些区域的相对比较。

“形状地图”视觉对象基于 ESRI/TopoJSON 地图，它有一项极具吸引力的功能，即，使用你可以创建的自定义地图。 例如地理位置、座位安排、楼层平面图等等。 在预览版“形状地图”中无法使用自定义地图。

## <a name="creating-shape-maps"></a>创建形状地图
你可以使用与此预览版本一同发行的地图测试“形状地图”控件，或者你可以使用自定义地图，只要它满足以下**使用自定义映射**章节中列出的要求。

**形状地图**视觉对象为预览功能，必须在 Power BI Desktop 中启用。 若要启用“形状地图”，请选择“文件”>“选项和设置”>“选项”>“预览功能”，然后选中“形状地图视觉对象”复选框。 完成选择后需要重启 Power BI Desktop。

![](media/desktop-shape-map/shape-map_1a.png)

启用“形状地图”后，即可单击“可视化效果”窗格中的“形状地图”控件。

![](media/desktop-shape-map/shape-map_2.png)

Power BI Desktop 将创建一个空的“形状地图”视觉对象设计画布。

![](media/desktop-shape-map/shape-map_3.png)

通过执行以下步骤创建**形状地图**：

1. 在“字段”窗格中，将具有区域名称（或缩写）的数据字段拖至“位置”Bucket，将数据度量值字段拖至“色彩饱和度”Bucket（暂时看不到地图）。

   > [!NOTE]
   > 有关如何快速获取地图数据以测试形状地图的信息，请参阅下文的“获取地图数据”一节。
   > 
   > 

   ![](media/desktop-shape-map/shape-map_3a.png)
2. 在“格式”设置窗格中，展开“形状”，并从“标准地图”下拉列表中选择某个地图来显示你的数据。 此时将出现一个绘制工具，如下图所示。

   ![](media/desktop-shape-map/shape-map_3b.png)

   > [!NOTE]
   > 本文末尾的“区域键”一节中有一组具有地图区域键的表，可以使用这些区域键来测试“形状地图”视觉对象。
   > 
   > 
3. 然后，可以从“格式”设置窗格中修改地图投影和缩放设置，以及数据点的颜色。 还可以修改缩放设置。 例如，可以更改颜色、设置最大值和最小值等等。

   ![](media/desktop-shape-map/shape-map_3d.png)
4. 还可以向“图例”存储段添加一个类别数据列，并基于类别对地图区域分类。

## <a name="use-custom-maps"></a>使用自定义地图
只要自定义地图为 **TopoJSON** 格式，你可以将其与“形状地图”一同使用。 如果你的地图是另一种格式，则可以使用在线工具（如[**地图整形程序**](http://mapshaper.org/)）来转换*形状文件*或将 *GeoJSON* 地图转换为 **TopoJSON** 格式。

若要使用 TopoJSON 地图文件，请将 ShapeMap 视觉对象添加到报表，并向“位置”和“色彩饱和度”Bucket 添加一些数据。 然后，在选中“格式”部分（如下图 (1) 中所示）的“可视化效果”窗格中，展开“形状”部分，选择“+ 添加地图”。

![](media/desktop-shape-map/shape-map_6.png)

## <a name="sample-custom-map"></a>自定义地图示例
美国律师办事处发布了关于诉讼和案件数量数据的年度财务报告。  在下面的链接中可以找到他们的所有报告，

https://www.justice.gov/usao/resources/annual-statistical-reports

由于可以将州分为多个区，我们需要使用自定义形状地图。  通过将美国司法区的 TopoJSON 地图导入到 Power BI Desktop，我们可以直观表示年度财务区律师数据。  下图展示了此地图的示例。

![](media/desktop-shape-map/shape-map_7a.png)

你也能对单个州地图进行一些有趣的操作，并基于它所包含的区显示更多详细信息。 

![](media/desktop-shape-map/shape-map_7b.png)

如果想试验该数据集和可视化效果，可以从下列链接下载用于生成此报表的原始 PBIX 文件。

* [自定义形状地图的演示 .PBIX 文件](http://download.microsoft.com/download/1/2/8/128943FB-9231-42BD-8A5D-5E2362C9D589/DistrictAttorneyFiscalReport.pbix)

## <a name="getting-map-data"></a>获取地图数据
若要将数据快速导入模型以便测试“形状地图”，你可以复制本文末尾的其中一个表，然后从“主页”功能区中选择“输入数据”。

![](media/desktop-shape-map/shape-map_4.png)

如果你的数据有多个列，则需要使用 Excel 等编辑器来粘贴数据，然后分别复制每个数据列。 接着，可以将该数据粘贴到 Power BI Desktop 中。 最上面的一行自动标识为标题。

![](media/desktop-shape-map/shape-map_5.png)

只需键入新的列名称（在右侧的空白列中），就可以输入一个新列，然后在每个单元格中添加值，就像在 Excel 中一样。 完成后，选择“加载”，该表将添加到 Power BI Desktop 的数据模型中。

> [!NOTE]
> 处理国家或地区时，请使用三字母缩写，以确保地理编码可以在地图可视化效果中正常运行。 不要使用两字母缩写，因为这样可能无法正确识别某些国家或地区。
> 
> 如果只有两字母缩写，请参阅[这篇外部博文](https://blog.ailon.org/how-to-display-2-letter-country-data-on-a-power-bi-map-85fc738497d6#.yudauacxp)，了解将两字母国家/地区缩写与三字母国家/地区缩写相关联的具体步骤。
> 
> 

## <a name="preview-behavior-and-requirements"></a>预览版行为和要求
使用此预览版的“形状地图”时有几条注意事项和要求：

* **形状地图**视觉对象为预览功能，必须在 Power BI Desktop 中启用。 若要启用“形状地图”，请选择“文件”>“选项和设置”>“选项”>“预览功能”，然后选中“形状地图视觉对象”复选框。
* 目前，还必须设置“色彩饱和度”Bucket，“图例”分类才能正常工作。
* 形状地图的最终发布版本将具有一个显示当前所选地图的地图键的用户界面（最终版本中没有日期集，且形状地图仍为预览版）。 在此预览版本中，可以引用表中的地图区域键，如本文中的“区域键”部分所述。
* “形状地图”视觉对象最多可绘制 1,000 个数据点。

## <a name="region-keys"></a>区域键
在此预览版中使用以下**区域键**来测试**形状地图**。

### <a name="australia-states"></a>澳大利亚：州

| `id` | `abbr` | `iso` | `name` | `postal` |
| --- | --- | --- | --- | --- |
| au-wa |WA |AU-WA |西澳大利亚 |WA |
| au-vic |Vic |AU-VIC |维多利亚州 |VIC |
| au-tas |Tas |AU-TAS |塔斯马尼亚岛 |TAS |
| au-sa |SA |AU-SA |南澳大利亚 |SA |
| au-qld |Qld |AU-QLD |昆士兰 |QLD |
| au-nt |NT |AU-NT |澳北区 |NT |
| au-nsw |NSW |AU-NSW |新南威尔士州 |NSW |
| au-act |ACT |AU-ACT |澳大利亚首都直辖区 |ACT |

### <a name="austria-states"></a>奥地利：州

| `id` | `iso` | `name` | `name-en` | `postal` |
| --- | --- | --- | --- | --- |
| at-wi |AT-9 |维也纳 |维也纳 |WI |
| at-vo |AT-8 |福尔贝格州 |福尔贝格州 |VO |
| at-tr |AT-7 |提洛尔 |提洛尔 |TR |
| at-st |AT-6 |施第里尔 |施第里尔 |ST |
| at-sz |AT-5 |萨尔斯堡 |萨尔斯堡 |SZ |
| at-oo |AT-4 |上奥地利州 |上奥地利州 |OO |
| at-no |AT-3 |下奥地利州 |下奥地利州 |NO |
| at-ka |AT-2 |卡林西亚 |卡林西亚 |KA |
| at-bu |AT-1 |布尔根兰 |布尔根兰 |BU |

### <a name="brazil-states"></a>巴西：州

| `id` |
| --- |
| 托刊亭斯州 |
| 伯南布哥 |
| 戈亚斯州 |
| 塞尔希培 |
| 圣保罗 |
| 圣卡塔琳娜州 |
| 罗赖马州 |
| 隆多尼亚 |
| 南里奥格兰德 |
| 北里奥格兰德 |
| 里约热内卢 |
| 皮奥伊 |
| 巴拉那 |
| 帕拉伊巴 |
| 帕拉州 |
| 米纳斯吉拉斯 |
| 马托格罗索 |
| 马拉尼昂 |
| 南马托格罗索 |
| 联邦直辖区 |
| 塞阿拉 |
| 圣埃斯皮里图 |
| 巴伊亚 |
| 亚马孙 |
| 阿马帕 |
| 阿拉戈斯 |
| 阿克里州 |
| 争议区域 1 |
| 争议区域 2 |
| 争议区域 3 |
| 争议区域 4 |

### <a name="canada-provinces"></a>加拿大：省

| `id` | `iso` | `name` | `postal` |
| --- | --- | --- | --- |
| ca-nu |CA-NU |努勒维特 |NU |
| ca-nt |CA-NT |西北地区 |NT |
| ca-yt |CA-YT |育空 |YT |
| ca-sk |CA-SK |萨斯喀彻温 |SK |
| ca-qc |CA-QC |魁北克 |QC |
| ca-pe |CA-PE |爱德华王子岛 |PE |
| ca-on |CA-ON |安大略 |ON |
| ca-ns |CA-NS |新斯科舍 |NS |
| ca-nl |CA-NL |纽芬兰-拉布拉多 |NL |
| ca-nb |CA-NB |新不伦瑞克 |NB |
| ca-mb |CA-MB |马尼托巴 |MB |
| ca-bc |CA-BC |不列颠哥伦比亚 |BC |
| ca-ab |CA-AB |亚伯达 |AB |

### <a name="france-regions"></a>法国：区域

| `id` | `name` | `name-en` |
| --- | --- | --- |
| 阿尔萨斯 |阿尔萨斯 |阿尔萨斯 |
| 罗纳-阿尔卑斯大区 |罗纳-阿尔卑斯大区 |罗纳-阿尔卑斯大区 |
| 普罗旺斯-阿尔卑斯-蓝色海岸 |普罗旺斯-阿尔卑斯-蓝色海岸 |普罗旺斯-阿尔卑斯-蓝色海岸 |
| 普瓦图-夏朗德 |普瓦图-夏朗德 |普瓦图-夏朗德 |
| 皮卡第 |皮卡第 |皮卡第 |
| 卢瓦尔河地区 |卢瓦尔河地区 |卢瓦尔河地区 |
| 北部-加来海峡 |北部-加来海峡 |北部-加来海峡 |
| 南部-比利牛斯 |南部-比利牛斯 |南部-比利牛斯 |
| 洛林 |洛林 |洛林 |
| 利穆赞大区 |利穆赞大区 |利穆赞大区 |
| 朗格多克-鲁西永 |朗格多克-鲁西永 |朗格多克-鲁西永 |
| 法兰西岛大区 |法兰西岛大区 |法兰西岛大区 |
| 上诺曼底 |上诺曼底 |上诺曼底 |
| 弗朗什-孔泰大区 |弗朗什-孔泰大区 |弗朗什-孔泰大区 |
| 科西嘉岛 |科西嘉岛 |科西嘉岛 |
| 香槟-阿登 |香槟-阿登 |香槟-阿登 |
| 中央-卢瓦尔河谷大区 |中央-卢瓦尔河谷大区 |中央-卢瓦尔河谷大区 |
| 布列塔尼大区 |布列塔尼大区 |布列塔尼大区 |
| 勃艮第 |勃艮第 |勃艮第 |
| 下诺曼底 |下诺曼底 |下诺曼底 |
| 奥弗涅大区 |奥弗涅大区 |奥弗涅大区 |
| 阿基坦 |阿基坦 |阿基坦 |

### <a name="germany-states"></a>德国：州

| `id` | `iso` | `name` | `name-en` | `postal` |
| --- | --- | --- | --- | --- |
| de-be |DE-BE |柏林 |柏林 |BE |
| de-th |DE-TH |图林根 |图林根 |TH |
| de-st |DE-ST |萨克森-安哈尔特 |萨克森-安哈尔特 |ST |
| de-sn |DE-SN |萨克森自由州 |萨克森自由州 |SN |
| de-mv |DE-MV |梅克伦堡-前波美拉尼亚 |梅克伦堡-前波美拉尼亚 |MV |
| de-bb |DE-BB |勃兰登堡 |勃兰登堡 |BB |
| de-sh |DE-SH |石勒苏益格-荷尔斯泰因 |石勒苏益格-荷尔斯泰因 |SH |
| de-sl |DE-SL |萨尔兰 |萨尔兰 |SL |
| de-rp |DE-RP |莱茵兰-普法尔茨 |莱茵兰-普法尔茨 |RP |
| de-nw |DE-NW |北莱茵-威斯特法伦 |北莱茵-威斯特法伦 |NW |
| de-ni |DE-NI |下萨克森 |下萨克森 |NI |
| de-he |DE-HE |黑森 |黑森 |HE |
| de-hh |DE-HH |汉堡 |汉堡 |HH |
| de-hb |DE-HB |不来梅 |不来梅 |HB |
| de-by |DE-BY |巴伐利亚 |巴伐利亚 |BY |
| de-bw |DE-BW |巴登-符腾堡州 |巴登-符腾堡州 |BW |

### <a name="ireland-counties"></a>爱尔兰：郡

| `id` |
| --- |
| 威克洛 |
| 韦克斯福德 |
| 韦斯特米斯 |
| 沃特福德 |
| 斯莱戈 |
| 蒂珀雷里郡 |
| 罗斯康芒 |
| 奥法利 |
| 莫纳亨 |
| 米斯 |
| 梅奥 |
| 劳斯 |
| 朗福德 |
| 利默里克 |
| 利特里姆 |
| 莱锡 |
| 基尔肯尼 |
| 基尔代尔 |
| 凯里 |
| 戈尔韦 |
| 都柏林 |
| 多尼哥 |
| 科克 |
| 克莱尔 |
| 卡文 |
| 卡洛 |

### <a name="italy-regions"></a>意大利：区域

| `id` | `iso` | `name` | `name-en` | `postal` |
| --- | --- | --- | --- | --- |
| it-vn |IT-34 |威尼托 |威尼托 |VN |
| it-vd |IT-23 |瓦莱达奥斯塔 |瓦莱达奥斯塔 |VD |
| it-um |IT-55 |翁布里亚 |翁布里亚 |UM |
| it-tt |IT-32 |特伦蒂诺—阿尔托阿迪杰区 |特伦蒂诺—阿尔托阿迪杰区 |TT |
| it-tc |IT-52 |托斯卡尼 |托斯卡尼 |TC |
| it-sc |IT-82 |西西里岛 |西西里岛 |SC |
| it-sd |IT-88 |萨丁岛 |萨丁岛 |SD |
| it-pm |IT-21 |皮埃蒙特 |皮埃蒙特 |PM |
| it-ml |IT-67 |莫利塞 |莫利塞 |ML |
| it-mh |IT-57 |马尔凯 |马尔凯 |MH |
| it-lm |IT-25 |伦巴蒂大区 |伦巴蒂大区 |LM |
| it-lg |IT-42 |利古利亚 |利古利亚 |LG |
| it-lz |IT-62 |拉齐奥 |拉齐奥 |LZ |
| it-fv |IT-36 |弗留利—威尼斯朱利亚 |弗留利—威尼斯朱利亚 |FV |
| it-er |IT-45 |艾米利亚-罗马涅区 |艾米利亚-罗马涅区 |ER |
| it-cm |IT-72 |坎帕尼亚 |坎帕尼亚 |CM |
| it-lb |IT-78 |卡拉布利亚 |卡拉布利亚 |LB |
| it-bc |IT-77 |巴斯利卡塔 |巴斯利卡塔 |BC |
| it-pu |IT-75 |阿普利亚 |阿普利亚 |PU |
| it-ab |IT-65 |阿布鲁佐 |阿布鲁佐 |AB |

### <a name="mexico-states"></a>墨西哥：州

| `id` | `abreviatura` | `iso` | `name` | `name-en` | `postal` |
| --- | --- | --- | --- | --- | --- |
| mx-zac |Zac. |MX-ZAC |萨卡特卡斯 |萨卡特卡斯 |ZA |
| mx-yuc |Yuc. |MX-YUC |尤卡坦 |尤卡坦 |YU |
| mx-ver |Ver. |MX-VER |韦拉克鲁斯 |韦拉克鲁斯 |VE |
| mx-tla |Tlax. |MX-TLA |特拉斯卡拉 |特拉斯卡拉 |TL |
| mx-tam |Tamps. |MX-TAM |塔毛利帕斯 |塔毛利帕斯 |TM |
| mx-tab |Tab. |MX-TAB |塔巴斯科 |塔巴斯科 |TB |
| mx-son |Son. |MX-SON |索诺拉省 |索诺拉省 |SO |
| mx-sin |Sin. |MX-SIN |锡那罗亚 |锡那罗亚 |SI |
| mx-slp |S.L.P. |MX-SLP |圣路易斯波托西 |圣路易斯波托西 |SL |
| mx-roo |Q.R. |MX-ROO |金塔纳罗奥 |金塔纳罗奥 |QR |
| mx-que |Qro. |MX-QUE |克雷塔罗 |克雷塔罗 |QE |
| mx-pue |Pue. |MX-PUE |普埃布拉 |普埃布拉 |PU |
| mx-oax |Oax. |MX-OAX |瓦哈卡 |瓦哈卡 |OA |
| mx-nle |N.L. |MX-NLE |新莱昂 |新莱昂 |NL |
| mx-nay |Nay. |MX-NAY |纳亚里特 |纳亚里特 |NA |
| mx-mor |Mor. |MX-MOR |莫雷洛斯 |莫雷洛斯 |MR |
| mx-mic |Mich. |MX-MIC |米却肯 |米却肯 |MC |
| mx-mex |Méx. |MX-MEX |墨西哥州 |墨西哥州 |MX |
| mx-jal |Jal. |MX-JAL |哈利斯科 |哈利斯科 |JA |
| mx-hid |Hgo. |MX-HID |伊达尔戈 |伊达尔戈 |HI |
| mx-gro |Gro. |MX-GRO |格雷罗 |格雷罗 |GR |
| mx-gua |Gto. |MX-GUA |瓜纳华托 |瓜纳华托 |GT |
| mx-dur |Dgo. |MX-DUR |杜兰戈 |杜兰戈 |DU |
| mx-dif |Col. |MX-DIF |墨西哥城 |墨西哥城 |DF |
| mx-col |Coah. |MX-COL |科利马 |科利马 |CL |
| mx-coa |Chis. |MX-COA |科阿韦拉 |科阿韦拉 |CA |
| mx-chh |Chih. |MX-CHH |奇瓦瓦 |奇瓦瓦 |CH |
| mx-chp |CDMX. |MX-CHP |恰帕斯 |恰帕斯 |CP |
| mx-cam |Camp. |MX-CAM |坎佩切 |坎佩切 |CM |
| mx-bcs |B.C.S. |MX-BCS |南下加利福尼亚 |南下加利福尼亚 |BS |
| mx-bcn |B.C. |MX-BCN |下加利福尼亚 |下加利福尼亚 |BN |
| mx-agu |Ags. |MX-AGU |阿瓜斯卡连特斯 |阿瓜斯卡连特斯 |AG |

### <a name="netherlands-provinces"></a>荷兰：省

| `id` | `iso` | `name` | `name-en` |
| --- | --- | --- | --- |
| nl-zh |NL-ZH |南荷兰 |南荷兰 |
| nl-ze |NL-ZE |泽兰 |泽兰 |
| nl-ut |NL-UT |乌特勒支 |乌特勒支 |
| nl-ov |NL-OV |上艾瑟尔 |上艾瑟尔 |
| nl-nh |NL-NH |北荷兰 |北荷兰 |
| nl-nb |NL-NB |北布拉班特 |北布拉班特 |
| nl-li |NL-LI |林堡 |林堡 |
| nl-gr |NL-GR |格罗宁根 |格罗宁根 |
| nl-ge |NL-GE |格尔德兰 |格尔德兰 |
| nl-fr |NL-FR |弗里斯兰 |弗里斯兰 |
| nl-fl |NL-FL |弗莱福兰 |弗莱福兰 |
| nl-dr |NL-DR |德伦特 |德伦特 |

### <a name="uk-countries"></a>英国：国家/地区

| `id` | `iso` | `name` |
| --- | --- | --- |
| gb-wls |GB-WLS |威尔士 |
| gb-sct |GB-SCT |苏格兰 |
| gb-nir |GB-NIR |北爱尔兰自治区 |
| gb-eng |GB-ENG |英格兰 |

### <a name="usa-states"></a>美国：州

| `id` | `name` | `postal` |
| --- | --- | --- |
| us-mi |密歇根 |MI |
| us-ak |阿拉斯加 |AK |
| us-hi |夏威夷 |HI |
| us-fl |佛罗里达 |FL |
| us-la |路易斯安那 |LA |
| us-ar |阿肯色 |AR |
| us-sc |南卡罗来纳 |SC |
| us-ga |格鲁吉亚 |GA |
| us-ms |密西西比 |MS |
| us-al |阿拉巴马 |AL |
| us-nm |新墨西哥 |NM |
| us-tx |德克萨斯 |TX |
| us-tn |田纳西 |TN |
| us-nc |北卡罗来纳 |NC |
| us-ok |俄克拉荷马 |确定 |
| us-az |亚利桑那 |AZ |
| us-mo |密苏里 |MO |
| us-va |弗吉尼亚 |VA |
| us-ks |堪萨斯 |KS |
| us-ky |肯塔基 |KY |
| us-co |科罗拉多 |CO |
| us-md |马里兰 |MD |
| us-wv |西佛吉尼亚 |WV |
| us-de |特拉华 |DE |
| us-dc |哥伦比亚特区 |DC |
| us-il |伊利诺斯 |IL |
| us-oh |俄亥俄 |OH |
| us-ca |加利福尼亚 |CA |
| us-ut |犹他 |UT |
| us-nv |内华达 |NV |
| us-in |印第安纳 |IN |
| us-nj |新泽西 |NJ |
| us-ri |罗德岛 |RI |
| us-ct |康乃迪克 |CT |
| us-pa |宾夕法尼亚 |PA |
| us-ny |纽约 |NY |
| us-ne |内布拉斯加 |NE |
| us-ma |马萨诸塞 |MA |
| us-ia |爱荷华 |IA |
| us-nh |新罕布什尔 |NH |
| us-or |俄勒冈 |OR |
| us-mn |明尼苏达 |MN |
| us-vt |佛蒙特 |VT |
| us-id |爱达荷 |ID |
| us-wi |威斯康星 |WI |
| us-wy |怀俄明 |WY |
| us-sd |南达科他 |SD |
| us-nd |北达科他 |ND |
| us-me |缅因 |ME |
| us-mt |蒙大拿 |MT |
| us-wa |华盛顿 |WA |

## <a name="next-steps"></a>后续步骤
[Power BI 中的矩阵视觉对象](desktop-matrix-visual.md)

[Power BI 中的可视化效果类型](power-bi-visualization-types-for-reports-and-q-and-a.md)