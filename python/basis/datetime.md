# Python3 日期时间 {docsify-ignore}

## datetime.date

###### 描述

处理年月日这种日期时间。

###### 语法

```python
datetime.date(year, month, day)
```

###### 参数

- year -- [最小年份, 最大年份]
- month -- [1, 12]
- day -- [1, 指定年份的月份中的天数]

###### 返回值

`datetime.date` 类对象。

###### 实例

```python
import datetime

print('最大日期：', datetime.date.max)
print('最小日期：', datetime.date.min)
d = datetime.date.today()
print('今天日期：', d)
print('今天年份：', d.year)
print('今天月份：', d.month)
print('今天天数：', d.day)
print('替换年份+月份：', d.replace(2018, 5))
print('替换年份：', d.replace(2018))
print('替换年份+月份+天数：', d.replace(2018, 5, 2))
print('自0001-01-01开始的第几天：', d.toordinal())
print('今天是星期几(0表示星期一)：', d.weekday())
print('今天是星期几(1表示星期一)：', d.isoweekday())
print('YYYY-MM-DD格式的日期字符串：', d.isoformat())
print('指定格式的日期字符串：', d.strftime('%Y/%m/%d'))
```

以上实例输出结果如下：

```powershell
最大日期： 9999-12-31
最小日期： 0001-01-01
今天日期： 2020-10-28
今天年份： 2020
今天月份： 10
今天天数： 28
替换年份+月份： 2018-05-28
替换年份： 2018-10-28
替换年份+月份+天数： 2018-05-02
自0001-01-01开始的第几天： 737726
今天是星期几(0表示星期一)： 2
今天是星期几(1表示星期一)： 3
YYYY-MM-DD格式的日期字符串： 2020-10-28
指定格式的日期字符串： 2020/10/28
```

## datetime.time

###### 描述

处理时分秒这种具体时间。

###### 语法

```python
datetime.time(hour, [minute[, second, [microsecond[, tzinfo]]]])
```

###### 参数

- hour -- [0, 23]
- minute -- [0, 59]
- second -- [0, 59]
- microsecond -- [0, 1000000]
- tzinfo -- timezone类实例

###### 返回值

`datetime.time` 类对象。

###### 实例

```python
import datetime

print('最大时间：', datetime.time.max)
print('最小时间：', datetime.time.min)
t = datetime.time(12, 15, 40, 6666)
print('datetime.time对象-时：', t.hour)
print('datetime.time对象-分：', t.minute)
print('datetime.time对象-秒：', t.second)
print('datetime.time对象-微秒：', t.microsecond)
print('HH:MM:SS格式的时间字符串：', t.strftime('%H:%M:%S'))
print('HH:MM:SS.%f格式的时间字符串：', t.strftime('%H:%M:%S.%f'))
```

以上实例输出结果如下：

```powershell
最大时间： 23:59:59.999999
最小时间： 00:00:00
datetime.time对象-时： 12
datetime.time对象-分： 15
datetime.time对象-秒： 40
datetime.time对象-微秒： 6666
HH:MM:SS格式的时间字符串： 12:15:40
HH:MM:SS.%f格式的时间字符串： 12:15:40.006666
```

## datetime.datetime

###### 描述

日期时间类，你可以理解为 `datetime.time` 和 `datetime.date` 的组合类。

###### 语法

```python
datetime.datetime(year, month, day, hour=0, minute=0, second=0, microsecond=0, tzinfo=None)
```

###### 参数

- year -- [最小年份, 最大年份]
- month -- [1, 12]
- day -- [1, 指定年份的月份中的天数]
- hour -- [0, 23]
- minute -- [0, 59]
- second -- [0, 59]
- microsecond -- [0, 1000000]
- tzinfo -- timezone类实例

###### 返回值

`datetime.datetime` 类对象。

###### 实例

```python
from datetime import datetime, timezone

print('当前的日期时间：', datetime.today())
print('指定时区的当前的日期时间：', datetime.now(timezone.utc))
print('世界统一时间(UTC)的当前的日期时间：', datetime.utcnow())
dt = datetime.now()
print('当前年份（其他参考datetime.date）：', dt.year)
print('当前小时（其他参考datetime.time）：', dt.hour)
print('以/分隔日期时间：', dt.isoformat(sep='/'))
print('以 分隔日期时间：', dt.isoformat(sep=' '))
print('指定格式的日期时间字符串：', dt.strftime('%Y-%m-%d %H:%M:%S.%f'))
```

以上实例输出结果如下：

```powershell
当前的日期时间： 2020-10-28 11:16:42.363164
指定时区的当前的日期时间： 2020-10-28 03:16:42.363164+00:00
世界统一时间(UTC)的当前的日期时间： 2020-10-28 03:16:42.364187
当前年份（其他参考datetime.date）： 2020
当前小时（其他参考datetime.time）： 11
以/分隔日期时间： 2020-10-28/11:16:42.364187
以 分隔日期时间： 2020-10-28 11:16:42.364187
指定格式的日期时间字符串： 2020-10-28 11:16:42.364187
```

## datetime.timedelta

###### 描述

两个不同时间之间的差值，可以对 `datetime.date`、`datetime.time` 和 `datetime.datetime` 对象做算术运算。

###### 语法

```python
datetime.timedelta(days=0, seconds=0, microseconds=0, milliseconds=0, hours=0, weeks=0)
```

###### 返回值

两个日期时间之间的运算结果。

###### 实例

```python
import datetime

print('一年包含的总秒数：', datetime.timedelta(365).total_seconds())
dt = datetime.datetime.now()
print('3天后：', dt + datetime.timedelta(3))
print('3天前：', dt + datetime.timedelta(-3))
print('3小时后：', dt + datetime.timedelta(hours=3))
print('3小时前：', dt + datetime.timedelta(hours=-3))
print('3小时30秒后：', dt + datetime.timedelta(hours=3, seconds=30))
dt2 = dt + datetime.timedelta(hours=10)
td = dt2 - dt
print('当前与10小时后相差：', td)
print('当前与10小时后相差多少秒：', td.seconds)
```

以上实例输出结果如下：

```powershell
一年包含的总秒数： 31536000.0
3天后： 2020-10-31 11:29:41.105240
3天前： 2020-10-25 11:29:41.105240
3小时后： 2020-10-28 14:29:41.105240
3小时前： 2020-10-28 08:29:41.105240
3小时30秒后： 2020-10-28 14:30:11.105240
当前与10小时后相差： 10:00:00
当前与10小时后相差多少秒： 36000
```
