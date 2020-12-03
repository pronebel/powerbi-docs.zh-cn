---
title: 在 Power BI 移动应用中设置数据警报
description: 了解如何在 Power BI 移动应用中设置数据警报，以便在仪表板中的数据更改超出你设置的限制时通知你。
author: paulinbar
ms.author: painbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: how-to
ms.date: 12/11/2019
ms.openlocfilehash: 4e9820b8ebff411434d9d6c408f36a36a644ea9d
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/01/2020
ms.locfileid: "96417994"
---
# <a name="set-data-alerts-in-the-power-bi-mobile-apps"></a>在 Power BI 移动应用中设置数据警报
适用于：

| ![iPhone](./media/mobile-set-data-alerts-in-the-mobile-apps/iphone-logo-50-px.png) | ![iPad](./media/mobile-set-data-alerts-in-the-mobile-apps/ipad-logo-50-px.png) | ![Android 手机](./media/mobile-set-data-alerts-in-the-mobile-apps/android-phone-logo-50-px.png) | ![Android 平板电脑](./media/mobile-set-data-alerts-in-the-mobile-apps/android-tablet-logo-50-px.png) | ![Windows 10 设备。](./media/mobile-set-data-alerts-in-the-mobile-apps/win-10-logo-50-px.png) |
|:--- |:--- |:--- |:--- |:--- |
| iPhone |iPad |Android 手机 |Android 平板电脑 |Windows 10 设备 |

可以在 Power BI 移动应用和 Power BI 服务中的仪表板上设置警报。 当磁贴中的数据更改超出设置的限制时，警报会通知你。 警报适用于包含单一数字的磁贴（如卡和仪表），但不适用于包含流数据的磁贴。 你可以在移动设备上设置数据警报，并在 Power BI 服务中查看，反之亦然。 即使你共享了仪表板或磁贴的快照，也只有你可以看到自己设置的数据警报。

如果拥有 Power BI Pro 许可证，或者共享仪表板采用高级容量，则可以在磁贴上设置警报。 

> [!WARNING]
> 数据驱动的警报通知提供有关数据的信息。 如果设备被盗，我们建议你转到 Power BI 服务，关闭所有数据驱动的警报规则。 
> 
> 详细了解[管理 Power BI 服务中的数据警报](../../create-reports/service-set-data-alerts.md)。
> 
> 

## <a name="data-alerts-on-an-iphone-or-ipad"></a>iPhone 或 iPad 上的数据警报
### <a name="set-an-alert-on-an-iphone-or-ipad"></a>在 iPhone 或 iPad 上设置警报
1. 点击仪表板中的数字或仪表盘磁贴以焦点模式打开该磁贴。  
   
   ![仪表板的屏幕截图，其中显示了焦点模式下的仪表盘磁贴。](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-card-visual.png)
2. 点击钟形图标 :::image type="icon" source="media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-alert-icon.png" border="false"::: 添加警报。  
3. 点击“添加警报规则”。
   
   ![警报规则的屏幕截图，其中显示未设置任何警报。](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-add-alert-rule.png)
4. 选择在大于或小于某个值时接收警报，然后设置值。
   
   ![警报设置的屏幕截图，其中显示了要设置的警报标题和值](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-set-alert-threshold.png)
5. 决定是否要每小时或每天接收警报，以及是否要在收到警报的同时也接收电子邮件。
   
   > [!NOTE]
   > 不会每小时或每天都收到一次警报，除非数据确实在那时进行了刷新。
   > 
   > 
6. 也可以更改警报标题。
7. 点击 **保存**。
8. 单个的磁贴可以有超过或低于阈值的值的警报。 在“管理警报”中，点击“添加警报规则”。
   
   ![管理警报的屏幕截图，其中显示指针指向“添加警报规则”。](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-add-another-alert-rule.png)

### <a name="manage-alerts-on-your-iphone-or-ipad"></a>在 iPhone 或 iPad 上管理警报
可以在移动设备上管理单个警报，或 [在 Power BI 服务中管理所有警报](../../create-reports/service-set-data-alerts.md)。

1. 在仪表板中，点击具有警报的数字或仪表盘磁贴。  
   
   ![iPhone 或 iPad 上仪表板的屏幕截图，其中显示了有警报的数字磁贴。](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-card-visual_has_alert.png)

2. 点击钟形图标 :::image type="icon" source="media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-has-alert-icon.png" border="false":::。  
3. 点击该警报名称以对其进行编辑，点击滑块以关闭电子邮件警报，或点击垃圾回收删除该警报。
   
    ![警报的屏幕截图，其中指针指向警报名称、用于删除警报的垃圾箱，以及用于关闭警报的滑块。](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-edit-delete-alert.png)

## <a name="data-alerts-on-an-android-device"></a>Android 设备上的数据警报
### <a name="set-an-alert-on-an-android-device"></a>在 Android 设备上设置警报
1. 在 Power BI 仪表板中，点击数字或仪表磁贴打开它。  
2. 点击钟形图标 :::image type="icon" source="media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-android-alert-icon.png" border="false"::: 添加警报。  
   
   ![Android 设备上仪表板的屏幕截图，其中显示了有警报的数字磁贴。](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-android-tap-alert.png)
3. 点击加号图标 (+)。
   
   ![管理警报的屏幕截图，其中指针指向加号图标。](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-android-plus-alert.png)
4. 选择在大于或小于某个值时接收警报，然后键入值。
   
   ![警报设置的屏幕截图，其中指针指向“保存”和“完成”。](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-android-tablet-set-alert-condition.png)
5. 点击“**完成**”。
6. 决定是否要每小时或每天接收警报，以及是否要在收到警报的同时也接收电子邮件。
   
   > [!NOTE]
   > 不会每小时或每天都收到一次警报，除非数据确实在那时进行了刷新。
   > 
   > 
7. 也可以更改警报标题。
8. 点击 **保存**。

### <a name="manage-alerts-on-an-android-device"></a>在 Android 设备上管理警报
你可以在 Power BI 移动应用中管理单个警报，或[在 Power BI 移动应用中管理所有警报](../../create-reports/service-set-data-alerts.md)。

1. 在仪表板中，点击具有警报的卡片或仪表盘磁贴。  
2. 点击实心铃图标 :::image type="icon" source="media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-android-filled-alert-bell.png" border="false":::。  
3. 点击该警报以更改值或将其关闭。
   
    ![“管理警报”磁贴的屏幕截图，其中显示了用于添加警报的加号图标。](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-android-manage-alerts.png)
4. 点击加号图标（+），向同一磁贴添加其他警报。
5. 若要完全删除警报，请点击垃圾箱图标 ![垃圾箱图标](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-android-delete-alert-icon.png).

## <a name="data-alerts-on-a-windows-device"></a>Windows 设备上的数据警报

>[!NOTE]
>我们将于 2021 年 3 月 16 日终止对使用 Windows 10 移动版的手机提供 Power BI 移动应用支持。 [了解详细信息](/legal/powerbi/powerbi-mobile/power-bi-mobile-app-end-of-support-for-windows-phones)

### <a name="set-data-alerts-on-a-windows-device"></a>在 Windows 设备上设置数据警报
1. 点击仪表板中的数字或仪表盘磁贴以打开该磁贴。  
2. 点击钟形图标 :::image type="icon" source="media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-alert-bell-off.png" border="false"::: 以添加警报。  
   
   ![Windows 设备上仪表板的屏幕截图，其中显示了有警报的数字磁贴。](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-tap-alert.png)
3. 点击加号图标 (+)。
   
   ![管理警报的屏幕截图，其中显示未设置任何警报。](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-no-alerts-yet.png)
4. 选择在大于或小于某个值时接收警报，然后键入值。
   
   ![警报设置的屏幕截图，其中显示了用于编辑警报的条目。](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-set-alert.png)
5. 决定是否要每小时或每天接收警报，以及是否要在收到警报的同时也接收电子邮件。
   
   > [!NOTE]
   > 不会每小时或每天都收到一次警报，除非数据确实在那时进行了刷新。
   > 
   > 
6. 也可以更改警报标题。
7. 点击复选标记。
8. 单个的磁贴可以有超过或低于阈值的值的警报。 在“管理警报”中，点击加号 (+)。
   
   ![管理警报的屏幕截图，其中显示了用于添加警报的加号。](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-add-another-alert.png)

### <a name="manage-alerts-on-a-windows-device"></a>在 Windows 设备上管理警报
你可以在 Power BI 移动应用中管理单个警报，或[在 Power BI 移动应用中管理所有警报](../../create-reports/service-set-data-alerts.md)。

1. 在仪表板中，点击具有警报的卡片或仪表盘磁贴。  
2. 点击钟形图标 :::image type="icon" source="media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-alert-bell-on.png" border="false":::。  
   
   ![仪表板的屏幕截图，其中显示了具有警报的数字磁贴。](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-has-alerts.png)
3. 点击该警报以更改值或将其关闭。
   
    ![管理警报的屏幕截图，其中显示了用于添加警报的加号。](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-add-another-alert.png)
4. 若要完全删除该警报，请单击右键或点击并按住 >“删除”。

## <a name="receiving-alerts"></a>接收警报
在移动设备上或在 Power BI 服务中的 Power BI [通知中心](mobile-apps-notification-center.md) 中接收警报，以及关于他人与你共享的新仪表板的通知。

虽然可以更频繁地刷新数据源，但是通常将其设置为每天刷新。 当仪表板中的数据刷新时，如果被跟踪的数据到达其中一个你所设定的阈值时，将发生下列情况。

1. Power BI 会检查自最后一个警报发出是否已超过 1 个小时或 24 个小时（具体取决于所选择的选项）。
   
   只要数据超过了阈值，则每 1 小时或每 24 小时你将会收到一个警报。
2. 如果你已设置警报向你发送电子邮件，则你将在收件箱中找到如下内容。
   
   ![显示警报的电子邮件通知的屏幕截图。](media/mobile-set-data-alerts-in-the-mobile-apps/powerbi-alerts-email.png)
3. Power BI 将消息添加到[通知中心](mobile-apps-notification-center.md)，并向标题栏上的钟形图标 :::image type="icon" source="media/mobile-set-data-alerts-in-the-mobile-apps/powerbi-alert-tile-notification-icon.png" border="false":::（iOS 和 Android）或全局导航按钮 ![全局导航按钮](./media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-alert-global-nav-button.png)（Windows 10 设备）添加黄色点。


4. 点击钟形图标 :::image type="icon" source="media/mobile-set-data-alerts-in-the-mobile-apps/powerbi-alert-tile-notification-icon.png" border="false"::: 或全局导航按钮 ![全局导航按钮](./media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-alert-global-nav-button.png)，以[打开“通知中心”](mobile-apps-notification-center.md)，并查看警报详细信息。
   
     

> [!NOTE]
> 警报仅适用于刷新的数据。 数据刷新时，Power BI 会查看是否为该数据设置了警报。 如果数据已达到了警报的阈值，则会触发警报。
> 
> 

## <a name="tips-and-troubleshooting"></a>提示和故障排除
* 警报当前对于 Bing 磁贴或带有日期/时间度量值的卡片磁贴不受支持。
* 警报仅适用于数字数据。
* 警报仅适用于刷新的数据。 它们不适用于静态数据。
* 警报不适用于包含流数据的磁贴。

## <a name="next-steps"></a>后续步骤
* [在 Power BI 服务中管理警报](../../create-reports/service-set-data-alerts.md)
* [Power BI 移动通知中心](mobile-apps-notification-center.md)
* 是否有任何问题? [尝试咨询 Power BI 社区](https://community.powerbi.com/)