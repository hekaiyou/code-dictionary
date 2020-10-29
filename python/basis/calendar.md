# Python3 日历 {docsify-ignore}

## calendar.calendar(year, w=2, l=1, c=6)

###### 描述

返回一个多行字符串格式的 `year` 年日历，3个月一行，每行长度为 `21*W + 18 + 2*C`。

###### 语法

```python
import calendar
calendar.calendar(year, w=2, l=1, c=6)
```

###### 参数

- year -- 日历年份
- w -- 每日宽度间隔字符
- l -- 每星期行数
- c -- 间隔距离

###### 返回值

一个多行字符串格式的 `year` 年日历。

###### 实例

```python
import calendar
print(calendar.calendar(2020, w=2, l=1, c=6))
```

以上实例输出结果如下：

```powershell
                                  2020

      January                   February                   March
Mo Tu We Th Fr Sa Su      Mo Tu We Th Fr Sa Su      Mo Tu We Th Fr Sa Su
       1  2  3  4  5                      1  2                         1
 6  7  8  9 10 11 12       3  4  5  6  7  8  9       2  3  4  5  6  7  8
13 14 15 16 17 18 19      10 11 12 13 14 15 16       9 10 11 12 13 14 15
20 21 22 23 24 25 26      17 18 19 20 21 22 23      16 17 18 19 20 21 22
27 28 29 30 31            24 25 26 27 28 29         23 24 25 26 27 28 29
                                                    30 31

       April                      May                       June
Mo Tu We Th Fr Sa Su      Mo Tu We Th Fr Sa Su      Mo Tu We Th Fr Sa Su
       1  2  3  4  5                   1  2  3       1  2  3  4  5  6  7
 6  7  8  9 10 11 12       4  5  6  7  8  9 10       8  9 10 11 12 13 14
13 14 15 16 17 18 19      11 12 13 14 15 16 17      15 16 17 18 19 20 21
20 21 22 23 24 25 26      18 19 20 21 22 23 24      22 23 24 25 26 27 28
27 28 29 30               25 26 27 28 29 30 31      29 30

        July                     August                  September
Mo Tu We Th Fr Sa Su      Mo Tu We Th Fr Sa Su      Mo Tu We Th Fr Sa Su
       1  2  3  4  5                      1  2          1  2  3  4  5  6
 6  7  8  9 10 11 12       3  4  5  6  7  8  9       7  8  9 10 11 12 13
13 14 15 16 17 18 19      10 11 12 13 14 15 16      14 15 16 17 18 19 20
20 21 22 23 24 25 26      17 18 19 20 21 22 23      21 22 23 24 25 26 27
27 28 29 30 31            24 25 26 27 28 29 30      28 29 30
                          31

      October                   November                  December
Mo Tu We Th Fr Sa Su      Mo Tu We Th Fr Sa Su      Mo Tu We Th Fr Sa Su
          1  2  3  4                         1          1  2  3  4  5  6
 5  6  7  8  9 10 11       2  3  4  5  6  7  8       7  8  9 10 11 12 13
12 13 14 15 16 17 18       9 10 11 12 13 14 15      14 15 16 17 18 19 20
19 20 21 22 23 24 25      16 17 18 19 20 21 22      21 22 23 24 25 26 27
26 27 28 29 30 31         23 24 25 26 27 28 29      28 29 30 31
                          30
```

## calendar.firstweekday()

###### 描述

返回当前每周起始日期的设置，默认情况下，首次载入 `caendar` 模块时返回0，即星期一。

###### 语法

```python
import calendar
calendar.firstweekday()
```

###### 返回值

当前每周起始日期的设置。

###### 实例

```python
import calendar
print("每周起始日期: ", calendar.firstweekday())
```

以上实例输出结果如下：

```powershell
每周起始日期:  0
```

## calendar.isleap(year)

###### 描述

判断是否闰年，是闰年则返回 `True`，否则为 `False`。

###### 语法

```python
import calendar
calendar.isleap(year)
```

###### 返回值

是闰年返回 `True`，否则为 `False`。

###### 实例

```python
import calendar
print("2020年是闰年: ", calendar.isleap(2020))
```

以上实例输出结果如下：

```powershell
2020年是闰年:  True
```

## calendar.leapdays(y1, y2)

###### 描述

返回在 `y1`、`y2` 两年之间的闰年总数。

###### 语法

```python
import calendar
calendar.leapdays(y1, y2)
```

###### 返回值

在 `y1`、`y2` 两年之间的闰年总数。

###### 实例

```python
import calendar
print("2000~2020年间有 %s 个闰年" % calendar.leapdays(2000, 2020))
```

以上实例输出结果如下：

```powershell
2000~2020年间有 5 个闰年
```

## calendar.month(year, month, w=2, l=1)

###### 描述

返回一个多行字符串格式的 `year` 年 `month` 月日历，每行的长度为 `7*w + 6`。

###### 语法

```python
import calendar
calendar.month(year, month, w=2, l=1)
```

###### 参数

- year -- 日历年份
- month -- 日历月份
- w -- 每日宽度间隔字符
- l -- 每星期的行数

###### 返回值

一个多行字符串格式的 `year` 年 `month` 月日历。

###### 实例

```python
import calendar
print(calendar.month(2000, 8, w=2, l=1))
```

以上实例输出结果如下：

```powershell
    August 2000
Mo Tu We Th Fr Sa Su
    1  2  3  4  5  6
 7  8  9 10 11 12 13
14 15 16 17 18 19 20
21 22 23 24 25 26 27
28 29 30 31
```

## calendar.monthcalendar(year, month)

###### 描述

返回一个整数的单层嵌套列表，每个子列表装载代表一个星期的整数，`year` 年 `month` 月外的日期都设为0，范围内的日都由该月第几日表示，从1开始。

###### 语法

```python
import calendar
calendar.monthcalendar(year, month)
```

###### 参数

- year -- 日历年份
- month -- 日历月份

###### 返回值

一个整数的单层嵌套列表，每个子列表装载代表一个星期的整数。

###### 实例

```python
import calendar
print(calendar.monthcalendar(2000, 8))
```

以上实例输出结果如下：

```powershell
[[0, 1, 2, 3, 4, 5, 6], [7, 8, 9, 10, 11, 12, 13], [14, 15, 16, 17, 18, 19, 20], [21, 22, 23, 24, 25, 26, 27], [28, 29, 30, 31, 0, 0, 0]]
```

## calendar.monthrange(year, month)

###### 描述

返回两个整数，第一个是该月的星期几的日期码，第二个是该月的日期码。日从0（星期一）到6（星期日），月从1到12。

###### 语法

```python
import calendar
calendar.monthrange(year, month)
```

###### 参数

- year -- 日历年份
- month -- 日历月份

###### 返回值

两个整数，第一个是该月的星期几的日期码，第二个是该月的日期码。

###### 实例

```python
import calendar
print(calendar.monthrange(2000, 8))
```

以上实例输出结果如下：

```powershell
(1, 31)
```

## calendar.prcal(year, w=2, l=1, c=6)

###### 描述

相当于 `print(calendar.calendar(year, w, l, c))`，返回一个多行字符串格式的 `year` 年日历。

###### 语法

```python
import calendar
calendar.prcal(year, w=2, l=1, c=6)
```

###### 参数

- year -- 日历年份
- w -- 每日宽度间隔字符
- l -- 每星期行数
- c -- 间隔距离

###### 返回值

一个多行字符串格式的 `year` 年日历。

###### 实例

```python
import calendar
calendar.prcal(2020, w=2, l=1, c=6)
```

以上实例输出结果如下：

```powershell
                                  2020

      January                   February                   March
Mo Tu We Th Fr Sa Su      Mo Tu We Th Fr Sa Su      Mo Tu We Th Fr Sa Su
       1  2  3  4  5                      1  2                         1
 6  7  8  9 10 11 12       3  4  5  6  7  8  9       2  3  4  5  6  7  8
13 14 15 16 17 18 19      10 11 12 13 14 15 16       9 10 11 12 13 14 15
20 21 22 23 24 25 26      17 18 19 20 21 22 23      16 17 18 19 20 21 22
27 28 29 30 31            24 25 26 27 28 29         23 24 25 26 27 28 29
                                                    30 31

       April                      May                       June
Mo Tu We Th Fr Sa Su      Mo Tu We Th Fr Sa Su      Mo Tu We Th Fr Sa Su
       1  2  3  4  5                   1  2  3       1  2  3  4  5  6  7
 6  7  8  9 10 11 12       4  5  6  7  8  9 10       8  9 10 11 12 13 14
13 14 15 16 17 18 19      11 12 13 14 15 16 17      15 16 17 18 19 20 21
20 21 22 23 24 25 26      18 19 20 21 22 23 24      22 23 24 25 26 27 28
27 28 29 30               25 26 27 28 29 30 31      29 30

        July                     August                  September
Mo Tu We Th Fr Sa Su      Mo Tu We Th Fr Sa Su      Mo Tu We Th Fr Sa Su
       1  2  3  4  5                      1  2          1  2  3  4  5  6
 6  7  8  9 10 11 12       3  4  5  6  7  8  9       7  8  9 10 11 12 13
13 14 15 16 17 18 19      10 11 12 13 14 15 16      14 15 16 17 18 19 20
20 21 22 23 24 25 26      17 18 19 20 21 22 23      21 22 23 24 25 26 27
27 28 29 30 31            24 25 26 27 28 29 30      28 29 30
                          31

      October                   November                  December
Mo Tu We Th Fr Sa Su      Mo Tu We Th Fr Sa Su      Mo Tu We Th Fr Sa Su
          1  2  3  4                         1          1  2  3  4  5  6
 5  6  7  8  9 10 11       2  3  4  5  6  7  8       7  8  9 10 11 12 13
12 13 14 15 16 17 18       9 10 11 12 13 14 15      14 15 16 17 18 19 20
19 20 21 22 23 24 25      16 17 18 19 20 21 22      21 22 23 24 25 26 27
26 27 28 29 30 31         23 24 25 26 27 28 29      28 29 30 31
                          30
```

## calendar.prmonth(year, month, w, l)

###### 描述

相当于 `print(calendar.month(year, month, w=2, l=1))`，返回一个多行字符串格式的 `year` 年 `month` 月日历。

###### 语法

```python
import calendar
calendar.prmonth(year, month, w=2, l=1)
```

###### 参数

- year -- 日历年份
- month -- 日历月份
- w -- 每日宽度间隔字符
- l -- 每星期的行数

###### 返回值

一个多行字符串格式的 `year` 年 `month` 月日历。

###### 实例

```python
import calendar
calendar.prmonth(2020, 8, w=2, l=1)
```

以上实例输出结果如下：

```powershell
    August 2020
Mo Tu We Th Fr Sa Su
                1  2
 3  4  5  6  7  8  9
10 11 12 13 14 15 16
17 18 19 20 21 22 23
24 25 26 27 28 29 30
31
```

## calendar.setfirstweekday(weekday)

###### 描述

设置每周的起始日期码，0（星期一）到6（星期日）。

###### 语法

```python
import calendar
calendar.setfirstweekday(weekday)
```

###### 参数

- weekday -- 每周从星期几（0~6）开始

###### 实例

```python
import calendar
calendar.prmonth(2020, 8, w=2, l=1)
calendar.setfirstweekday(3)
calendar.prmonth(2020, 8, w=2, l=1)
```

以上实例输出结果如下：

```powershell
    August 2020
Mo Tu We Th Fr Sa Su
                1  2
 3  4  5  6  7  8  9
10 11 12 13 14 15 16
17 18 19 20 21 22 23
24 25 26 27 28 29 30
31
    August 2020
Th Fr Sa Su Mo Tu We
       1  2  3  4  5
 6  7  8  9 10 11 12
13 14 15 16 17 18 19
20 21 22 23 24 25 26
27 28 29 30 31
```

## calendar.timegm(tupletime)

###### 描述

和 `time.gmtime` 相反，接受一个时间元组形式，返回该时刻的时间戳（1970纪元后经过的浮点秒数）。

###### 语法

```python
import calendar
calendar.timegm(tupletime)
```

###### 参数

- tupletime -- 时间元组

###### 返回值

该时刻的时间戳（1970纪元后经过的浮点秒数）。

###### 实例

```python
import time
import calendar
print(calendar.timegm(time.localtime()))
```

以上实例输出结果如下：

```powershell
1598815166
```

## calendar.weekday(year, month, day)

###### 描述

返回给定日期的星期码，0（星期一）到6（星期日）。

###### 语法

```python
import calendar
calendar.weekday(year, month, day)
```

###### 参数

- year -- 日历年份
- month -- 日历月份
- day -- 日历天数

###### 返回值

给定日期的星期码，0（星期一）到6（星期日）。

###### 实例

```python
import calendar
print(calendar.weekday(2020, 8, 30))
```

以上实例输出结果如下：

```powershell
6
```
