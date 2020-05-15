---
title: Power BI 报表生成器中的表达式示例
description: Power BI Report Builder 分页报表中经常使用表达式来控制内容和报表外观。
ms.date: 10/21/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: 87ddb651-a1d0-4a42-8ea9-04dea3f6afa4
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 48e81c91a4555b4c8ea847ddffb1413058bbb152
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "78921139"
---
# <a name="expression-examples-in-power-bi-report-builder"></a>Power BI 报表生成器中的表达式示例
Power BI Report Builder 分页报表中经常使用表达式来控制内容和报表外观。 表达式是用 Microsoft Visual Basic 编写的，可以使用内置函数、自定义代码、报表和组变量以及用户定义的变量。 表达式以等号 (=) 开头。   

本主题提供可用于报表中常见任务的表达式的示例。  
  
-   [Visual Basic 函数](#VisualBasicFunctions) Visual Basic 日期、字符串、转换和条件函数的示例。  
  
-   [报表函数](#ReportFunctions) 聚合和其他内置报告函数的示例。  
  
-   [报表数据的外观](#AppearanceofReportData) 有关如何更改报表外观的示例。  
  
-   [属性](#Properties) 有关设置报表项属性以控制格式或可见性的示例。  
  
-   [参数](#Parameters) 在表达式中使用参数的示例。  
  
-   [自定义代码](#CustomCode) 嵌入式自定义代码的示例。  
  
有关简单表达式和复杂表达式（可使用表达式的位置）以及表达式中可包含的引用的类型的详细信息，请参阅 [Power BI 报表生成器中的表达式](report-builder-expressions.md)下的主题。 
  
## <a name="functions"></a>函数  
 报表中的许多表达式都包含函数。 可使用这些函数设置数据格式化、应用逻辑和访问报表元数据。 可以编写使用 Microsoft Visual Basic 运行时库以及 `xref:System.Convert` 和 `xref:System.Math` 命名空间中的函数的表达式。 你可以在自定义代码中添加对函数的引用。 还可以使用 Microsoft .NET Framework 中的类，包括 `xref:System.Text.RegularExpressions`。  
  
##  <a name="visual-basic-functions"></a><a name="VisualBasicFunctions"></a> Visual Basic 函数  
 可以使用 Visual Basic 函数来操作文本框中显示的数据或用于参数、属性或报表其他区域的数据。 本部分提供的示例展示其中一些功能。 有关详细信息，请参阅 MSDN 上的 [Visual Basic 运行时库成员](https://go.microsoft.com/fwlink/?LinkId=198941)。  
  
 .NET Framework 提供许多自定义格式选项，例如，特定日期格式。 有关详细信息，请参阅[格式设置类型](/dotnet/standard/base-types/formatting-types)。  
  
### <a name="math-functions"></a>日期函数  
  
-   “Round”函数可将数字舍入到最接近的整数  。 以下表达式将 1.3 舍入为 1：  
  
    ```  
    = Round(1.3)  
    ```  
  
     还可以编写表达式以将值舍入为指定的倍数，类似于 Excel 中的“MRound”函数  。 将值乘以生成整数的因子，将数字四舍五入取整，然后除以同一因子。 例如，若要将 1.3 舍入 0.2 最接近的倍数 (1.4)，可使用以下表达式：  
  
    ```  
    = Round(1.3*5)/5  
    ```  
  
###  <a name="date-functions"></a><a name="DateFunctions"></a> 日期函数  
  
-   “Today”函数提供当前日期  。 此表达式可在文本框中使用，用于显示报表上的日期，或在参数中使用，用于根据当前日期筛选数据。  
  
    ```  
    =Today()  
    ```  
  
-   使用“DateInterval”函数提取日期的特定部分  。 以下是一些有效的“DateInterval”参数  ：

    -   DateInterval.Second
    -   DateInterval.Minute
    -   DateInterval.Hour
    -   DateInterval.Weekday
    -   DateInterval.Day
    -   DateInterval.DayOfYear
    -   DateInterval.WeekOfYear
    -   DateInterval.Month
    -   DateInterval.Quarter
    -   DateInterval.Year

    例如，此表达式显示今天的日期在当前年份中为第几周：
  
    ```  
    =DatePart(DateInterval.WeekOfYear, today()) 
    ```  
  
-   “DateAdd”函数用于根据单个参数提供一系列日期  。 以下表达式提供一个日期，该日期是“StartDate”参数所确定的日期六个月之后的日期  。  
  
    ```  
    =DateAdd(DateInterval.Month, 6, Parameters!StartDate.Value)  
    ```  
  
-   “Year”函数显示特定日期的年份  。 可以使用此选项将日期组合在一起，或将年份显示为一组日期的标签。 此表达式可以提供一组给定的销售订单日期的年份。 也可用“Month”函数和其他功能来操作日期  。 有关详细信息，请参阅 Visual Basic 文档。  
  
    ```  
    =Year(Fields!OrderDate.Value)  
    ```  
  
-   可以在表达式中组合函数来自定义格式。 以下表达式将某个日期的格式从月 - 日 - 年更改为月 - 周 - 周序号。 例如，将 12/23/2009 更改为 12 月第 3 周：  
  
    ```  
    =Format(Fields!MyDate.Value, "MMMM") & " Week " &   
    (Int(DateDiff("d", DateSerial(Year(Fields!MyDate.Value),   
    Month(Fields!MyDate.Value),1), Fields!FullDateAlternateKey.Value)/7)+1).ToString  
    ```  
  
     如果将表达式用作某个数据集的计算字段，可在图表上使用此表达式按周聚合每个月内的值。  
  
-   以下表达式将 SellStartDate 值的格式设置为 MMM-YY。 SellStartDate 字段是日期时间数据类型。  
  
    ```  
    =FORMAT(Fields!SellStartDate.Value, "MMM-yy")  
    ```  
  
-   以下表达式将 SellStartDate 值的格式设置为 dd/MM/yyyy。 SellStartDate 字段是日期时间数据类型。  
  
    ```  
    =FORMAT(Fields!SellStartDate.Value, "dd/MM/yyyy")  
    ```  
  
-   “CDate”函数将值转换为日期  。 “Now”函数返回包含当前日期和时间（根据系统）的日期值  。 “DateDiff”返回 Long 值，该值指定两个日期值之间的时间间隔数  。  
  
     以下示例显示当前年份的开始日期  
  
    ```  
    =DateAdd(DateInterval.Year,DateDiff(DateInterval.Year,CDate("01/01/1900"),Now()),CDate("01/01/1900"))  
    ```  
  
-   以下示例根据当前月份显示上个月的开始日期。  
  
    ```  
    =DateAdd(DateInterval.Month,DateDiff(DateInterval.Month,CDate("01/01/1900"),Now())-1,CDate("01/01/1900"))  
    ```  
  
-   以下表达式生成 SellStartDate 和 LastReceiptDate 之间间隔的年份。 这些字段位于两个不同的数据集 DataSet1 和 DataSet2 中。  
  
    ```  
    =DATEDIFF("yyyy", First(Fields!SellStartDate.Value, "DataSet1"), First(Fields!LastReceiptDate.Value, "DataSet2"))  
    ```  
  
-   “DatePart”函数返回 Integer 值，该值包含给定日期值的指定元素。以下表达式返回 DataSet1 中 SellStartDate 的第一个值的年份  。 指定数据集的范围是因为报表中有多个数据集。  
  
    ```  
    =Datepart("yyyy", First(Fields!SellStartDate.Value, "DataSet1"))  
  
    ```  
  
-   “DateSerial”函数返回日期值，该值表示某个指定的年、月和日，时间信息设置为午夜  。 以下示例根据当前月份显示上个月的结束日期。  
  
    ```  
    =DateSerial(Year(Now()), Month(Now()), "1").AddDays(-1)  
    ```  
  
-   以下表达式根据用户选择的日期参数值显示各种日期。  
  
|示例说明|示例|  
|-------------------------|-------------|  
|昨天|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value)-1)`|  
|两天前|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value)-2)`|  
|一个月前|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value)-1,Day(Parameters!TodaysDate.Value))`|  
|两个月前|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value)-2,Day(Parameters!TodaysDate.Value))`|  
|一年前|`=DateSerial(Year(Parameters!TodaysDate.Value)-1,Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value))`|  
|两年前|`=DateSerial(Year(Parameters!TodaysDate.Value)-2,Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value))`|  
  
###  <a name="string-functions"></a><a name="StringFunctions"></a> 字符串函数  
  
-   通过使用连接运算符和 Visual Basic 常量组合多个字段。 以下表达式返回两个字段，它们分别位于同一文本框的不同行中：  
  
    ```  
    =Fields!FirstName.Value & vbCrLf & Fields!LastName.Value   
    ```  
  
-   使用“Format”函数设置字符串中日期和数字的格式  。 以下表达式以长日期格式显示 StartDate 和 EndDate 参数的值   ：  
  
    ```  
    =Format(Parameters!StartDate.Value, "D") & " through " &  Format(Parameters!EndDate.Value, "D")    
    ```  
  
     如果文本框仅包含日期或数字，则应使用文本框的“Format”属性来应用格式而不是在文本框中使用“Format”函数  。  
  
-   “Right”、“Len”和“InStr”函数可用于返回子字符串，例如，将 DOMAIN\\username 剪裁为仅用户名称      。 以下表达式将字符串的一部分返回到名为 User 的参数的反斜杠 (\\) 字符的右侧  ：  
  
    ```  
    =Right(Parameters!User.Value, Len(Parameters!User.Value) - InStr(Parameters!User.Value, "\"))  
    ```  
  
     以下表达式与前一个表达式的结果相同，使用 .NET Framework `xref:System.String` 类的成员而不是 Visual Basic 函数：  
  
    ```  
    =Parameters!User.Value.Substring(Parameters!User.Value.IndexOf("\")+1, Parameters!User.Value.Length-Parameters!User.Value.IndexOf("\")-1)  
    ```  
  
-   显示多值参数的所选值。 以下示例使用“Join”函数将参数 MySelection 的选定值连接成一个字符串，该字符串可以设置为报表项中文本框值的表达式   ：  
  
    ```  
    = Join(Parameters!MySelection.Value)  
    ```  
  
     以下示例的作用与上面的示例相同，另外在所选值列表之前显示文本字符串。  
  
    ```  
    ="Report for " & JOIN(Parameters!MySelection.Value, " & ")  
  
    ```  
  
-   .NET Framework `xref:System.Text.RegularExpressions` 中的“Regex”函数可用于更改现有字符串的格式，例如，设置电话号码的格式  。 以下表达式使用“Replace”函数将字段中 10 位电话号码的格式从“nnn-nnn-nnnn”更改为“(nnn)nnn-nnnn”        ：  
  
    ```  
    =System.Text.RegularExpressions.Regex.Replace(Fields!Phone.Value, "(\d{3})[ -.]*(\d{3})[ -.]*(\d{4})", "($1) $2-$3")  
    ```  
  
    > [!NOTE]  
    >  验证 Fields!Phone.Value 的值没有多余的空格且类型为 `xref:System.String`。  
  
### <a name="lookup"></a>LookUp  
  
-   通过指定键字段，可以使用“Lookup”函数从数据集中检索一对一关系的值，例如键值对  。 在给定要匹配的产品标识符的情况下，以下表达式显示数据集（“Product”）中的产品名称：  
  
    ```  
    =Lookup(Fields!PID.Value, Fields!ProductID.Value, Fields.ProductName.Value, "Product")  
    ```  
  
### <a name="lookupset"></a>LookupSet  
  
-   通过指定键字段，可以使用“LookupSet”函数从数据集中检索一对多关系的值  。 例如，一个人可以有多个电话号码。 在以下示例中，假设数据集 PhoneList 包含每个行中的人员标识符和电话号码。 “LookupSet”返回一个值数组  。 以下表达式将返回值组合为单个字符串，并显示 ContactID 指定的人员的电话号码列表：  
  
    ```  
    =Join(LookupSet(Fields!ContactID.Value, Fields!PersonID.Value, Fields!PhoneNumber.Value, "PhoneList"),",")  
    ```  
  
###  <a name="conversion-functions"></a><a name="ConversionFunctions"></a> 转换函数  
 可以使用 Visual Basic 函数将字段从一种数据类型转换为另一种数据类型。 转换函数可用于将字段的默认数据类型转换为计算或组合文本所需的数据类型。  
  
-   以下表达式将常量 500 转换为十进制类型，以便将其与某个筛选表达式的“值”字段中的 Transact-SQL money 数据类型进行比较。  
  
    ```  
    =CDec(500)  
    ```  
  
-   以下表达式显示为多值参数 MySelection 选择的值的数量  。  
  
    ```  
    =CStr(Parameters!MySelection.Count)  
    ```  
  
###  <a name="decision-functions"></a><a name="DecisionFunctions"></a> 决策函数  
  
-   “Iif”函数根据表达式是否为 true，返回两个值中的一个  。 如果 `LineTotal` 的值超过 100，则以下表达式使用“Iif”函数返回布尔值“True”   。 否则它将返回“False”  ：  
  
    ```  
    =IIF(Fields!LineTotal.Value > 100, True, False)  
    ```  
  
-   使用多个“IIF”函数（也称为“嵌套 IIF”）根据 `PctComplete` 的值返回三个值中的一个  。 可以将以下表达式放置在文本框的填充颜色中，用于根据文本框中的值更改背景颜色。  
  
    ```  
    =IIF(Fields!PctComplete.Value >= 10, "Green", IIF(Fields!PctComplete.Value >= 1, "Blue", "Red"))  
    ```  
  
     大于或等于 10 的值显示绿色背景，1 到 9 显示蓝色背景，小于1 显示红色背景。  
  
-   另一种等效方法是使用“Switch”函数  。 如果要测试三个或更多条件时，可使用“Switch”函数  。 “Switch”函数返回与计算结果为 true 的一系列表达式中第一个关联的值  ：  
  
    ```  
    =Switch(Fields!PctComplete.Value >= 10, "Green", Fields!PctComplete.Value >= 1, "Blue", Fields!PctComplete.Value = 1, "Yellow", Fields!PctComplete.Value <= 0, "Red")  
    ```  
  
     值大于或等于 10 时，显示绿色背景；介于 1 和 9 之间时，显示蓝色背景；等于 1 时显示黄色背景；小于或等于 0 时，显示红色背景。  
  
-   测试 `ImportantDate` 字段的值，如果超过一周，则返回“红色”，否则返回“蓝色”。 此表达式可用于控制报表项中文本框的 Color 属性：  
  
    ```  
    =IIF(DateDiff("d",Fields!ImportantDate.Value, Now())>7,"Red","Blue")  
    ```  
  
-   测试 `PhoneNumber` 字段的值，如果它是“null”（在 Visual Basic 中为“Nothing”），则返回“无值”；否则返回电话号码值   。 此表达式可用于控制报表项中文本框的值。  
  
    ```  
    =IIF(Fields!PhoneNumber.Value Is Nothing,"No Value",Fields!PhoneNumber.Value)  
    ```  
  
-   测试 `Department` 字段的值并返回子报表名称或“null”（在 Visual Basic 中为“Nothing”）   。 此表达式可用于条件钻取子报表。  
  
    ```  
    =IIF(Fields!Department.Value = "Development", "EmployeeReport", Nothing)  
    ```  
  
-   测试字段值是否为 null。 此表达式可用于控制图像报表项的“Hidden”属性  。 在以下示例中，仅当 [LargePhoto] 字段的值不为 null 时，才会显示由该字段指定的图像。  
  
    ```  
    =IIF(IsNothing(Fields!LargePhoto.Value),True,False)  
    ```  
  
-   “MonthName”函数返回包含指定月份名称的字符串值  。 以下示例在“月份”字段包含值 0 时在该字段中显示 NA。  
  
    ```  
    IIF(Fields!Month.Value=0,"NA",MonthName(IIF(Fields!Month.Value=0,1,Fields!Month.Value)))  
  
    ```  
  
##  <a name="report-functions"></a><a name="ReportFunctions"></a> 报表函数  
 在表达式中，可以添加对可操作报表中数据的其他报表函数的引用。 本节提供了其中两个函数的示例。 
  
###  <a name="sum"></a><a name="Sum"></a> Sum  
  
-   “Sum”函数可以对组或数据区域中的值进行求和  。 此功能可用于组的页眉或页脚中。 以下表达式显示 Order 组或数据区域中的数据的总和：  
  
    ```  
    =Sum(Fields!LineTotal.Value, "Order")  
    ```  
  
-   此外，还可以使用“Sum”函数进行条件聚合计算  。 例如，如果数据集具有名为 State 的字段，其可能的值为 Not Started、Started、Finished，则以下表达式（放入组标头时）只计算“Finished”值的总和：  
  
    ```  
    =Sum(IIF(Fields!State.Value = "Finished", 1, 0))  
    ```  
  
###  <a name="rownumber"></a><a name="RowNumber"></a> RowNumber  
  
-   在数据区域的文本框中使用“RowNumber”函数时，会显示表达式所在的文本框的每个实例的行号  。 此函数可用于对表中的行进行编号。 它还可用于更复杂的任务，例如根据行数提供分页符。 有关详细信息，请参阅本主题中的[分页符](#PageBreaks)。  
  
     为“RowNumber”指定的范围控制何时开始重新编号  。 “Nothing”关键字指示函数从最外层数据区域的第一行开始计数  。 要从嵌套的数据区域内开始计数，请使用数据区域的名称。 要从组内开始计数，请使用组的名称。  
  
    ```  
    =RowNumber(Nothing)  
    ```  
  
##  <a name="appearance-of-report-data"></a><a name="AppearanceofReportData"></a> 报表数据的外观  
 可以使用表达式来控制数据在报表上的显示方式。 例如，可以在单个文本框中显示两个字段的值、显示有关报表的信息或影响在报表中插入分页符的方式。  
  
###  <a name="page-headers-and-footers"></a><a name="PageHeadersandFooters"></a> 页眉和页脚  
 设计报表时，可能会想在报表页脚中显示报表名称和页码。 可以使用以下表达式来实现此目的：  
  
-   以下表达式提供报表的名称及其运行时间。 可将其放在报表页脚的文本框中，也可以放在报表正文中。 使用用于短日期的 .NET Framework 格式字符串来格式化时间：  
  
    ```  
    =Globals.ReportName & ", dated " & Format(Globals.ExecutionTime, "d")  
    ```  
  
-   以下表达式放置在报表页脚的文本框中，可提供报表中的页码和总页数：  
  
    ```  
    =Globals.PageNumber & " of " & Globals.TotalPages  
    ```  
  
 以下示例描述了如何在页眉中显示页面的第一个和最后一个值，这类似于目录列表中的值。 该示例假定数据区域包含名为 `LastName` 的文本框。  
  
-   以下表达式放在页眉左侧的文本框中，提供页面上 `LastName` 文本框的第一个值：  
  
    ```  
    =First(ReportItems("LastName").Value)  
    ```  
  
-   以下表达式放在页眉右侧的文本框中，提供页面上 `LastName` 文本框的最后一个值：  
  
    ```  
    =Last(ReportItems("LastName").Value)  
    ```  
  
 以下示例说明如何显示页面总值。 该示例假定数据区域包含名为 `Cost` 的文本框。  
  
-   以下表达式放置在页眉或页脚中，提供页面的 `Cost` 文本框中值的总和：  
  
    ```  
    =Sum(ReportItems("Cost").Value)  
    ```  
  
> [!NOTE]  
>  页眉或页脚中的每个表达式只能引用一个报表项。 此外，还可以在页眉和页脚表达式中引用文本框名称，但不能引用文本框中的实际数据表达式。  
  
###  <a name="page-breaks"></a><a name="PageBreaks"></a> 分页符  
 在某些报表中，你可能想要在指定行数的末尾放置分页符，而不是在组或报表项上添加。 若要实现此目的，请创建一个包含所需组或详细信息记录的组，向该组添加分页符，然后按指定的行数向组添加组表达式。  
  
-   以下表达式放置在组表达式中时，可为以 25 行为单位的每个组分配一个数字。 当为组定义分页符时，该表达式每 25 行产生一个分页符。  
  
    ```  
    =Ceiling(RowNumber(Nothing)/25)  
    ```  
  
     若要允许用户为每页的行数设置一个值，需创建一个名为 `RowsPerPage` 的参数，并作为组表达式的基础，如下面的表达式所示：  
  
    ```  
    =Ceiling(RowNumber(Nothing)/Parameters!RowsPerPage.Value)  
    ```  
  
##  <a name="properties"></a><a name="Properties"></a> 属性  
 表达式不仅可用于在文本框中显示数据。 还可用于更改对报表项应用属性的方式。 可以更改报表项的样式信息，或更改其可见性。  
  
###  <a name="formatting"></a><a name="Formatting"></a> 格式设置  
  
-   在文本框的 Color 属性中使用以下表达式时，它会根据 `Profit` 字段的值更改文本的颜色：  
  
    ```  
    =Iif(Fields!Profit.Value < 0, "Red", "Black")  
    ```  
  
     此外，还可以使用 Visual Basic 对象变量 `Me`。 此变量是引用文本框值的另一种方式。  
  
     `=Iif(Me.Value < 0, "Red", "Black")`  
  
-   如果数据区域中报表项的 BackgroundColor 属性中使用以下表达式，它会将每行的背景颜色交替显示为淡绿色和白色：  
  
    ```  
    =Iif(RowNumber(Nothing) Mod 2, "PaleGreen", "White")  
    ```  
  
     如果要在指定的范围内使用表达式，可能需要指示聚合函数的数据集：  
  
    ```  
    =Iif(RowNumber("Employees") Mod 2, "PaleGreen", "White")  
    ```  
  
> [!NOTE]  
>  可使用的颜色来自 .NET Framework KnownColor 枚举。  
  
### <a name="chart-colors"></a>图表颜色  
 要指定形状图表的颜色，可以使用自定义代码来控制颜色映射到数据点值的顺序。 这有助于为具有相同类别组的多个图表使用一致的颜色。 
  
###  <a name="visibility"></a><a name="Visibility"></a> 可见性  
 您可以使用报表项的可见性属性来显示和隐藏报表中的项。 在诸如表之类的数据区域中，可以在一开始根据表达式中的值隐藏详细信息行。  
  
-   以下表达式在用于组中详细信息行的初始可见性时，会在 `PctQuota` 字段中显示超过 90% 的总销售额的详细信息行：  
  
    ```  
    =Iif(Fields!PctQuota.Value>.9, False, True)  
    ```  
  
-   如果在表的隐藏属性中设置以下表达式，结果是仅当表具有超过 12 行时才会显示该表：  
  
    ```  
    =IIF(CountRows()>12,false,true)  
    ```  
  
-   如果在列的“Hidden”属性中设置以下表达式，结果是只有在从数据源检索数据后，报表数据集中存在该字段时，才会显示该列  ：  
  
    ```  
    =IIF(Fields!Column_1.IsMissing, true, false)  
    ```  
  
###  <a name="urls"></a><a name="Hyperlinks"></a> URLs  
 可以使用报表数据自定义 URL，还可以有条件地控制是否添加 URL，作为文本框的一个操作。  
  
-   如果使用以下表达式来实现针对文本框的一个操作，该表达式会生成自定义 URL，该 URL 将数据集字段 `EmployeeID` 指定为 URL 参数。  
  
    ```  
    ="https://adventure-works/MyInfo?ID=" & Fields!EmployeeID.Value  
    ```  
  
-   以下表达式有条件地控制是否在文本框中添加 URL。 此表达式依赖于名为 `IncludeURLs` 的参数，该参数允许用户决定是否在报表中包含活动 URL。 此表达式设置为对文本框的一个操作。 通过将参数设置为 False，然后查看报表，可以导出没有超链接的报表 Microsoft Excel。  
  
    ```  
    =IIF(Parameters!IncludeURLs.Value,"https://adventure-works.com/productcatalog",Nothing)  
    ```  
  
##  <a name="report-data"></a><a name="ReportData"></a> 报表数据  
 表达式可用于操作报表中使用的数据。 可以引用参数和其他报表信息。 甚至可以更改用于检索报表数据的查询。  
  
###  <a name="parameters"></a><a name="Parameters"></a> 参数  
 可以在参数中使用表达式来更改参数的默认值。 例如，可以使用参数，基于运行报表时所使用的用户 ID，将数据筛选限定到特定用户。  
  
-   以下表达式在用作参数的默认值时，会收集运行报表的人员的用户 ID：  
  
    ```  
    =User!UserID  
    ```  
  
-   若要在查询参数、筛选表达式、文本框或报表的其他区域中引用参数，请使用“参数”全局集合  。 此示例假定参数名为 Department  ：  
  
    ```  
    =Parameters!Department.Value  
    ```  
  
-   可以在报表中创建参数，并设置为隐藏。 当报表在报表服务器上运行时，参数不会显示在工具栏中，报表阅读器也无法更改默认值。 可以使用设置为默认值的隐藏参数作为自定义常量。 可以在任何表达式（包括字段表达式）中使用此值。 以下表达式可标识由名为 ParameterField 的参数的默认参数值指定的字段：   
  
    ```  
    =Fields(Parameters!ParameterField.Value).Value  
    ```  
  
##  <a name="custom-code"></a><a name="CustomCode"></a> 自定义代码  
 可以使用报表中嵌入的自定义代码。 
  
### <a name="using-group-variables-for-custom-aggregation"></a>使用组变量实现自定义聚合  
 可以将限定到特定组范围的组变量的值进行初始化，然后在表达式中包含对该变量的引用。 将组变量与自定义代码一起使用的方法之一是实现自定义聚合。 
  
## <a name="suppressing-null-or-zero-values-at-run-time"></a>在运行时取消 null 或零值  
 表达式中的某些值在报表处理时可能会计算为 null 或未定义。 这可能会产生运行时错误，导致在文本框中显示“#Error”而不是计算表达式  。 “IIF”函数对这种行为特别敏感，因为与 If-Then-Else 语句不同，“IIF”语句的每个部分会在传递到执行“true”或“false”测试的例程之前进行评估（包括函数调用）     。 如果 `Fields!Sales.Value` 为 NOTHING，则语句 `=IIF(Fields!Sales.Value is NOTHING, 0, Fields!Sales.Value)` 在呈现的报表中生成“#Error”  。  
  
 若要避免这种情况，请使用以下策略之一：  
  
-   如果字段 B 的值为 0 或未定义，则将分子设置为 0，分母设置为 1；否则，将分子设置为字段 A 的值，将分母设置为字段 B 的值。  
  
    ```  
    =IIF(Field!B.Value=0, 0, Field!A.Value / IIF(Field!B.Value =0, 1, Field!B.Value))  
    ```  
  
-   使用自定义代码函数返回表达式的值。 以下示例返回当前值和先前值之间的百分比差异。 这可用于计算任意两个连续值之间的差值，它处理首次比较的极端情况（不存在之前的值），以及之前的值或当前值是否为“null”的情况（在 Visual Basic 中为 Nothing）   。  
  
    ```  
    Public Function GetDeltaPercentage(ByVal PreviousValue, ByVal CurrentValue) As Object  
        If IsNothing(PreviousValue) OR IsNothing(CurrentValue) Then  
            Return Nothing  
        Else if PreviousValue = 0 OR CurrentValue = 0 Then  
            Return Nothing  
        Else   
            Return (CurrentValue - PreviousValue) / CurrentValue  
        End If  
    End Function  
    ```  
  
     下面的表达式显示了如何从“ColumnGroupByYear”容器（组或数据区域）的文本框中调用此自定义代码。  
  
    ```  
    =Code.GetDeltaPercentage(Previous(Sum(Fields!Sales.Value),"ColumnGroupByYear"), Sum(Fields!Sales.Value))  
    ```  
  
     这有助于避免运行时异常。 现在，可以在文本框的“Color”属性中使用类似 `=IIF(Me.Value < 0, "red", "black")` 的表达式，根据值是否大于或小于 0 来有条件地显示文本  。  
  
## <a name="next-steps"></a>后续步骤

- [Power BI Premium 中的分页报表是什么？](paginated-reports-report-builder-power-bi.md)
  
