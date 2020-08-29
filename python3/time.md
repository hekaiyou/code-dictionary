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
secs = time.mktime( t )
print("time.mktime(t): %f" %  secs)
print("asctime(localtime(secs)): %s" % time.asctime(time.localtime(secs)))
```

以上实例输出结果如下：

```powershell
time.mktime(t): 1455699818.000000
asctime(localtime(secs)): Wed Feb 17 17:03:38 2016
```
