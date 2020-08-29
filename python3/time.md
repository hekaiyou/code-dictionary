# Python3 时间 {docsify-ignore}

## time.perf_counter()

###### 描述

以浮点数计算的秒数返回当前的 CPU 时间，用来衡量不同程序的耗时，比 `time.time()` 更有用。

需要注意，在不同的系统上含义的不同，在 UNIX 系统上，它返回的是 “进程时间”，它是用秒表示的浮点数（时间戳）。而在 Windows 中，第一次调用，返回的是进程运行的实际时间，而第二次之后的调用是自第一次调用以后到现在的运行时间。（实际上是以 WIN32 上 `QueryPerformanceCounter()` 为基础，它比毫秒表示更为精确）

###### 语法

```python
time.perf_counter()
```

###### 返回值

1. 在第一次调用的时候，返回的是程序运行的实际时间
2. 以第二次之后的调用，返回的是自第一次调用后，到这次调用的时间间隔
3. 在 win32 系统下，这个函数返回的是真实时间（WallTime），而在 Unix/Linux 下返回的是 CPU 时间

###### 实例

```python
import time

def procedure():
    time.sleep(2.5)

t0 = time.perf_counter()
procedure()
print(time.perf_counter() - t0)
t0 = time.time()
procedure()
print(time.time() - t0)
```

以上实例输出结果如下：

```powershell
2.503497
2.5198497772216797
```

## time.mktime(t)

###### 描述

执行与 `gmtime()`、`localtime()` 相反的操作，它接收 `struct_time` 对象作为参数，返回用秒数来表示时间的浮点数。如果输入的值不是一个合法的时间，将触发 `OverflowError` 或 `ValueError` 异常。

###### 语法

```python
time.mktime(t)
```

###### 参数

- t -- 结构化的时间或者完整的9位元组元素

###### 返回值

用秒数来表示时间的浮点数。

###### 实例

```python
import time
t = (2016, 2, 17, 17, 3, 38, 1, 48, 0)
secs = time.mktime(t)
print("time.mktime(t): %f" %  secs)
print("asctime(localtime(secs)): %s" % time.asctime(time.localtime(secs)))
```

以上实例输出结果如下：

```powershell
time.mktime(t): 1455699818.000000
asctime(localtime(secs)): Wed Feb 17 17:03:38 2016
```

## time.tzset()

###### 描述

根据环境变量TZ重新初始化时间相关设置（**仅Unix/Linux环境可用**），标准TZ环境变量格式如下：

```python
std offset [dst [offset [,start[/time], end[/time]]]]
```

- std/dst -- 三个或者多个时间的缩写字母。传递给 `time.tzname`
- offset -- 距UTC的偏移，格式：`[+|-]hh[:mm[:ss]] {h=0-23, m/s=0-59}`
- start[/time], end[/time] -- DST开始生效时的日期，格式为 `m.w.d` — 代表日期的月份、周数和日期。`w=1` 指月份中的第一周，而 `w=5` 指月份的最后一周。`start` 和 `end` 可以是以下格式之一
 - Jn -- 儒略日 `n (1 <= n <= 365)`，闰年日（2月29）不计算在内
 - n -- 儒略日 `(0 <= n <= 365)`，闰年日（2月29）计算在内
 - Mm.n.d -- 日期的月份、周数和日期。`w=1` 指月份中的第一周，而 `w=5` 指月份的最后一周
 - time -- （可选）DST开始生效时的时间（24小时制），默认值为 02:00（指定时区的本地时间）

###### 语法

```python
time.tzset()
```

###### 实例

```python
import os
import time
os.environ['TZ'] = 'EST+05EDT,M4.1.0,M10.5.0'
time.tzset()
print(time.strftime('%X %x %Z'))
os.environ['TZ'] = 'AEST-10AEDT-11,M10.5.0,M3.5.0'
time.tzset()
print(time.strftime('%X %x %Z'))
```

以上实例输出结果如下：

```powershell
23:25:45 04/06/16 EDT
13:25:45 04/07/16 AEST
```

## time.timezone

###### 描述

当地时区（未启动夏令时）距离格林威治的偏移秒数，`>0`-美洲、`<=0`大部分欧洲，亚洲，非洲）。

###### 语法

```python
time.timezone
```

###### 实例

```python
import time
print("当地时区与格林威治的偏移: ", time.timezone)
```

以上实例输出结果如下：

```powershell
当地时区与格林威治的偏移:  -28800
```

## time.tzname

###### 描述

包含一对根据情况的不同而不同的字符串，分别是带夏令时的本地时区名称，和不带的。

###### 语法

```python
time.tzname
```

###### 实例

```python
import time
print("本地时区名称: ", time.tzname)
```

以上实例输出结果如下：

```powershell
本地时区名称:  ('中国标准时间', '中国夏令时')
```

## time.altzone

###### 描述

返回格林威治西部的夏令时地区的偏移秒数，如果该地区在格林威治东部会返回负值（如西欧，包括英国），对夏令时启用地区才能使用。

###### 语法

```python
time.altzone
```

###### 实例

```python
import time
print("time.altzone %d " % time.altzone)
```

以上实例输出结果如下：

```powershell
time.altzone -32400
```

## time.asctime([tupletime])

###### 描述

接受时间元组并返回一个可读的形式为 `Sat Aug 29 17:36:50 2020`（*2020年29月8日 周六17时36分50秒*）的24个字符的字符串。

###### 语法

```python
time.asctime([tupletime])
```

###### 实例

```python
import time
t = time.localtime()
print("time.asctime(t): %s " % time.asctime(t))
```

以上实例输出结果如下：

```powershell
time.asctime(t): Sat Aug 29 17:36:50 2020
```

## time.ctime([secs])

###### 描述

相当于 `asctime(localtime(secs))`，未给参数相当于 `asctime()`。

###### 语法

```python
time.ctime([secs])
```

###### 实例

```python
import time
print("time.ctime(): %s" % time.ctime())
```

以上实例输出结果如下：

```powershell
time.ctime(): Sat Aug 29 23:08:54 2020
```

## time.gmtime([secs])

###### 描述

接收时间戳（1970纪元后经过的浮点秒数）并返回格林威治天文时间下的时间元组 `t`，须注意 `t.tm_isdst` 始终为0。

###### 语法

```python
time.gmtime([secs])
```

###### 实例

```python
import time
print("gmtime:", time.gmtime(1455508609.34375))
```

以上实例输出结果如下：

```powershell
gmtime: time.struct_time(tm_year=2016, tm_mon=2, tm_mday=15, tm_hour=3, tm_min=56, tm_sec=49, tm_wday=0, tm_yday=46, tm_isdst=0)
```

## time.localtime([secs])

###### 描述

接收时间戳（1970纪元后经过的浮点秒数）并返回当地时间下的时间元组 `t`，这里的 `t.tm_isdst` 可取0或1，取决于当地当时是不是夏令时。

###### 语法

```python
time.localtime([secs])
```

###### 实例

```python
import time
print("localtime(): ", time.localtime(1455508609.34375))
```

以上实例输出结果如下：

```powershell
localtime():  time.struct_time(tm_year=2016, tm_mon=2, tm_mday=15, tm_hour=11, tm_min=56, tm_sec=49, tm_wday=0, tm_yday=46, tm_isdst=0)
```

## time.sleep(secs)

###### 描述

推迟调用线程的运行。

###### 语法

```python
time.sleep(secs)
```

###### 参数

- secs -- 推迟秒数

###### 实例

```python
import time
print("开始: %s" % time.ctime())
time.sleep(5)
print("结束: %s" % time.ctime())
```

以上实例输出结果如下：

```powershell
开始: Sat Aug 29 23:19:01 2020
结束: Sat Aug 29 23:19:06 2020
```

## time.strftime(fmt[, tupletime])

###### 描述

返回以可读字符串表示的当地时间，格式由 `fmt` 决定。

###### 语法

```python
time.strftime(fmt[, tupletime])
```

###### 参数

- fmt -- 字符串格式
- tupletime -- 时间元组

###### 返回值

以可读字符串表示的当地时间，格式由 `fmt` 决定。

###### 实例

```python
import time
print(time.strftime("%Y-%m-%d %H:%M:%S", time.localtime()))
```

以上实例输出结果如下：

```powershell
2020-08-29 23:25:28
```

## time.strptime(str, fmt)

###### 描述

根据 `fmt` 的格式把一个时间字符串解析为时间元组。

###### 语法

```python
time.strptime(str, fmt)
```

###### 参数

- str -- 时间字符串
- fmt -- 字符串格式

###### 返回值

一个时间元组。

###### 实例

```python
import time
struct_time = time.strptime("30 Nov 00", "%d %b %y")
print("返回元组: ", struct_time)
```

以上实例输出结果如下：

```powershell
返回元组:  time.struct_time(tm_year=2000, tm_mon=11, tm_mday=30, tm_hour=0, tm_min=0, tm_sec=0, tm_wday=3, tm_yday=335, tm_isdst=-1)
```

## time.time()

###### 描述

返回当前时间的时间戳（1970纪元后经过的浮点秒数）。

###### 语法

```python
time.time()
```

###### 返回值

当前时间的时间戳。

###### 实例

```python
import time
print(time.time())
```

以上实例输出结果如下：

```powershell
1598715132.0319996
```
