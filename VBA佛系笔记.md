### 基础格式

```vb
Sub helloworld()
    MsgBox "hello world!!!"
End Sub
```

### 注释

```vb
' 单行注释


'多行注释
'多行注释
'多行注释
'多行注释
'多行注释
```

### 续写符

```vb
'   续写符
    Columns("D:D").Select
    Selection.FormatConditions.Add Type:=xlCellValue, _
    Operator:=xlLess, _
```

### debug 调试

运行-->逐句

或者 F8

### 变量

```vb
Sub text2()
    y = InputBox("请输入你的出生年份")
    n = 2025 - y
    MsgBox "你已经" & n & "岁了"
End Sub
```

```vb
Dim x As Integer '整数

Dim st As String '文本

Dim rg As Range '对象
Set rg = Range("A1") ·'对象赋值

Dim arr(1 to 10) As Integer '数组

Long 长整数， Single 单精度，Double 双精度，Date 时间
```



- Public x As Interger ‘声明全局变量，所有模块都能用，不建议，可以使用函数取变量
- isnumeric(x) 判断x是否是数字,在vba.Information中
- set i = Range(“A1”) ‘set,可以将对象赋值给变量
- 判断变量未赋值 is nothing



![img](./VBA%E4%BD%9B%E7%B3%BB%E7%AC%94%E8%AE%B0.assets/baee26911f387d91c4cbefc08f2847b6.png)

### 对象

#### 对象的表达方法

excel有数百个对象，我们先记住一些常用对象
工作簿、工作表、单元格

**Workbooks**(“工作簿名”)
**ActiveWorkbook**活动工作簿
**ThisWorkBook**'代码所在工作簿

**Sheets(n)**第n个工作表	按工作表的顺序
**Sheetr**第n个工作表	按系统工作表名
**Sheets**("工作表名")）	按工作表名称
**ActiveSheet**活动工作表	可以用来判断动态下拉表格

**Range**("单元格地址”)
一个单元格，一行，一列，一个区域
**Cells**(行，列)
[A1]单元格简写
Activecell活动单元格
Selection 选择的区域

```vb
Sub cellsTest()

'[f3] = Sheets("6采购未交订单 (2)").Name
'[f3] = Sheets(3).Name
'Range("f3") = Sheets(4).Name  //一个单元格
'Range("f3:g5") = 5  //一个区域
'Range("f:f").Select //选择一列
'[f3] = 666
'MsgBox ActiveCell
Cells(3, 7) = 888

End Sub
```

#### 对象的属性和方法

![image-20251001233730680](./VBA%E4%BD%9B%E7%B3%BB%E7%AC%94%E8%AE%B0.assets/image-20251001233730680-1759333063007-3.png)



```vb
Sub cellsTest()

'Range("f3").Clear  '清空
'[g3].Clear
'MsgBox Workbooks("CTB.xlsx").Path  '文件地址
'MsgBox Sheets.Count    '统计
'Sheets(20).Name = "快学excel"  '更改名称
'MsgBox ActiveCell.Address  ' 当前活动单元格地址
'Range("a1").Interior.ColorIndex = 30    '设置单元格颜色
ThisWorkbook.Sheets(20).Range("a1").Interior.ColorIndex = 56

End Sub
```



```vb
Sub newWorkBooksTest()
'Workbooks.Add ' 新建一个工作簿


'a = ThisWorkbook.Path  ' 打开指定的工作簿
'Workbooks.Open (a & "\" & "07按LT下单.xlsx")

'ActiveWorkbook.Close   ' 关闭当前工作簿
'Worksheets.Add.Name = "textCopyExcel"  ' 增加一个工作表名字是
'ThisWorkbook.Sheets("快学excel").Copy ActiveWorkbook.Sheets(1)  ' 把第一个工作表的内容复制到 textCopyExcel
ActiveWorkbook.Sheets("快学excel").Name = "哈哈哈"
End Sub
```



### 单元格的基础操作







```vb

'Sub cellTest()

'Range("f10").Activate   '让f10单元格被选中/激活
'Range("d9").Copy [f10] 'copyTo f10 复制的是带格式的

'Range("d9").Copy
'Range("f10").PasteSpecial xlPasteValues '只粘贴值
'Range("d9").Copy:Range("f10").PasteSpecial xlPasteValues '只粘贴值 写成一行需要加个冒号
'Range("f10").Delete '删除 不是清空
'Range("f10").Clear  '清空所有内容,包括格式
'Range(f10).ClearContents    '只清空字体,保留格式

'End Sub
```



### IF语句





```vb
Sub ifTest()
Dim n%, x%
n = 3
x = 5
If n > x Then
    MsgBox "n比x大"
ElseIf n = x Then
    MsgBox "n等于x"
Else
    MsgBox "n比x小"
End If

End Sub
```



### for循环语句





```vb
Sub forTest()
' for循环语句
Dim n%
    For n = 2 To 19
        If Cells(n, 2) < 60 Then
            Cells(n, 2).Interior.ColorIndex = 3
        End If
    Next
End Sub
```



### for步长step



```vb
Sub forStepTest()

Dim n, cj
For n = 4 To 52 Step 4
    'MsgBox Cells(n, 4)
    cj = cj + Cells(n, 4)
    'MsgBox cj
Next
MsgBox cj
End Sub
```

### 循环嵌套



```vb
Sub forTwoTtest()
Dim n%, y%, x%
For n = 1 To 3
    MsgBox "外层循环第" & n & "次"
        For y = 1 To 5
        MsgBox "内层循环第" & y & "次"
        x = x + 1
        MsgBox "内层循环代码被执行了" & x & "次"
    Next y
Next n
End Sub
```



```vb
Sub forTwoTtest2()
For n = 2 To 26
    For y = 2 To 8 Step 2
        If Cells (n, y) < 60 Then
        	Cells(n, y).Interior.ColorIndex = 3
        End If
    Next y
Next n
End Sub
```



![image-20251008225429662](./VBA%E4%BD%9B%E7%B3%BB%E7%AC%94%E8%AE%B0.assets/image-20251008225429662-1759935272395-1.png)



### 动态获取行号和列号



![image-20251009232417081](./VBA%E4%BD%9B%E7%B3%BB%E7%AC%94%E8%AE%B0.assets/image-20251009232417081-1760023459592-1.png)



```vb
'动态获取行列号,进行筛选改变单元格颜色
Sub test()
Dim n%, y%
x = Range("al").End(xlToRight).Column
h = Range("al").End(xlDown).Row
For n = 2 To h
    For y = 2 To x Step 2
        If Cells(n, y) < 60 Then
            Cells(n, y).Interior.ColorIndex = 3
        End If
    Next y
Next n
End Sub
```



### row和rows



![image-20251009232818201](./VBA%E4%BD%9B%E7%B3%BB%E7%AC%94%E8%AE%B0.assets/image-20251009232818201-1760023699945-3.png)



```vb
'Sub testlO()
''MsgBox Range("b6:c10").Row
'Rows.Select '选中所有行
'Rows(1).Select  '选中第一个单元格
'Sheets(1).Name = 111    '
'Range("a5:el0").Rows("1").Select '选中区域的第一行
'End Sub




Sub testO()
Dim n%, y%
x = Cells(1, Columns.Count).End(xlToLeft).Column
h = Cells(Rows.Count, "f").End(xlUp).Row
    For n = 2 To h
        For y = 2 To x Step 2
            If Cells(n, y) < 60 Then
                Cells(n, y).Interior.ColorIndex = 3
            End If
        Next y
    Next n
End Sub
```





### usedrange



![image-20251009235012304](./VBA%E4%BD%9B%E7%B3%BB%E7%AC%94%E8%AE%B0.assets/image-20251009235012304-1760025013783-5.png)



```vb
Sub test()
Worksheets(1).UsedRange.Select
'Dim s As Worksheet
s.UsedRange
MsgBox ActiveSheet.UsedRange.Rows.Count
MsgBox ActiveSheet.UsedRange.Columns.Count
End Sub
```





### CurrentRegion单元格属性



![image-20251010230503441](./VBA%E4%BD%9B%E7%B3%BB%E7%AC%94%E8%AE%B0.assets/image-20251010230503441-1760108705245-1.png)





```vb
'类似 alt + A
Sub currentRegionTest()
'Sheets("快学excel").UsedRange.Select
'Range("a1").CurrentRegion.Select
ActiveCell.CurrentRegion.Select

End Sub
    
    
    
Sub testO()
Dim n%, y%
x = Range("a1").CurrentRegion.Columns.Count
h = Range("a1").CurrentRegion.Rows.Count
For n = 2 To h
    For y = 2 To x Step 2
        If Cells(n, y) < 60 Then
            Cells(n, y).Interior.ColorIndex = 3
        End If
    Next y
Next n
End Sub
```



### for each



![image-20251010232054418](./VBA%E4%BD%9B%E7%B3%BB%E7%AC%94%E8%AE%B0.assets/image-20251010232054418-1760109656047-3.png)



```vb
' 循环打印工作簿
Sub test()
Dim s As Workbook
For Each s In Workbooks
    MsgBox s.Name
Next
End Sub



'   循环打印单元格区域中的单元格内容
Sub testO()
Dim s As Range
For Each s In Range("a1:f14")
    MsgBox s
Next
End Sub
```



### ForEach 示例





```vb
Sub forEachTest()
Dim ss As Range
For Each ss In Range("c2", Cells(Rows.Count, 3).End(xlUp)).Select
    If ss.Value < 60 Then ss.Interior.ColorIndex = 3
Next ss
End Sub
```





```vb
'foreach循环创建sheet
Sub forEachNewSheetTest()
Dim ss As Range, n%
For Each ss In Range(Sheet1.[b2], Sheetl.Cells(Rows.Count, 2).End(xlUp))
    n = n + 1
    If ss.Value = "男" Then
        Worksheets.Add(after:=Sheets(Sheets.Count)).Name = Sheet1.Cells(n + 1, 1)
    End If
Next ss
End Sub
```





### offset 便偏移



![image-20251020231925811](./VBA%E4%BD%9B%E7%B3%BB%E7%AC%94%E8%AE%B0.assets/image-20251020231925811-1760973569833-1.png)



```vb
Sub offsetTest()
Range("a1").Offset(8, 4).Select
End Sub
    

'不建议
Sub offsetTest2()
Range("a1")(9, 5).Select
End Sub
```



```vb
修改后的:

'foreach循环创建sheet
Sub forEachNewSheetTest()
Dim ss As Range, n%
For Each ss In Range(Sheet1.[b2], Sheetl.Cells(Rows.Count, 2).End(xlUp))
    If ss.Value = "男" Then
        Worksheets.Add(after:=Sheets(Sheets.Count)).Name = ss.Offset(0, -1)
    End If
Next ss
End Sub

```



### 该看1-26





