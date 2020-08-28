# Python3 数学 {docsify-ignore}

## abs(x)

###### 描述

返回数字的绝对值。

###### 语法

```python
abs(x)
```

###### 参数

- x -- 数值表达式，可以是整数、浮点数、复数

###### 返回值

数字 `x` 的绝对值，如果参数是一个复数，则返回它的大小。

###### 实例

```python
print("abs(-40): ", abs(-40))
print("abs(100.10): ", abs(100.10))
```

以上实例输出结果如下：

```powershell
abs(-40):  40
abs(100.10):  100.1
```

## ceil(x)

###### 描述

返回一个大于或等于 `x` 的的最小整数。

###### 语法

```python
import math
math.ceil(x)
```

###### 参数

- x -- 数值表达式

###### 返回值

一个大于或等于 `x` 的的最小整数。

###### 实例

```python
import math
print("math.ceil(-45.17): ", math.ceil(-45.17))
print("math.ceil(100.12): ", math.ceil(100.12))
print("math.ceil(100.72): ", math.ceil(100.72))
print("math.ceil(math.pi): ", math.ceil(math.pi))
```

以上实例输出结果如下：

```powershell
math.ceil(-45.17):  -45
math.ceil(100.12):  101
math.ceil(100.72):  101
math.ceil(math.pi):  4
```

## exp(x)

###### 描述

返回 `x` 的指数。

###### 语法

```python
import math
math.exp(x)
```

###### 参数

- x -- 数值表达式

###### 返回值

数值 `x` 的指数。

###### 实例

```python
import math
print("math.exp(-45.17): ", math.exp(-45.17))
print("math.exp(100.12): ", math.exp(100.12))
print("math.exp(100.72): ", math.exp(100.72))
print("math.exp(math.pi): ", math.exp(math.pi))
```

以上实例输出结果如下：

```powershell
math.exp(-45.17):  2.4150062132629406e-20
math.exp(100.12):  3.0308436140742566e+43
math.exp(100.72):  5.522557130248187e+43
math.exp(math.pi):  23.140692632779267
```

## fabs(x)

###### 描述

返回数字的绝对值，类似于 `abs()` 函数，但是有两点区别：

- `abs()` 是内置函数，`fabs()` 函数在 `math` 模块中定义
- `fabs()` 函数只对浮点型跟整型数值有效，`abs()` 还可以运用在复数中。

###### 语法

```python
import math
math.fabs(x)
```

###### 参数

- x -- 数值表达式

###### 返回值

数字的绝对值。

###### 实例

```python
import math
print("math.fabs(-45.17): ", math.fabs(-45.17))
print("math.fabs(100.12): ", math.fabs(100.12))
print("math.fabs(100.72): ", math.fabs(100.72))
print("math.fabs(math.pi): ", math.fabs(math.pi))
```

以上实例输出结果如下：

```powershell
math.fabs(-45.17):  45.17
math.fabs(100.12):  100.12
math.fabs(100.72):  100.72
math.fabs(math.pi):  3.141592653589793
```

## floor(x)

###### 描述

返回数字的下舍整数，小于或等于 `x`。

###### 语法

```python
import math
math.floor(x)
```

###### 参数

- x -- 数值表达式

###### 返回值

小于或等于 `x` 的整数。

###### 实例

```python
import math
print("math.floor(-45.17): ", math.floor(-45.17))
print("math.floor(100.12): ", math.floor(100.12))
print("math.floor(100.72): ", math.floor(100.72))
print("math.floor(math.pi): ", math.floor(math.pi))
```

以上实例输出结果如下：

```powershell
math.floor(-45.17):  -46
math.floor(100.12):  100
math.floor(100.72):  100
math.floor(math.pi):  3
```

## log(x)

###### 描述

返回 `x` 的自然对数。

###### 语法

```python
import math
math.log(x)
```

###### 参数

- x -- 数值表达式

###### 返回值

数值 `x` 的自然对数。

###### 实例

```python
import math
print("math.log(100.12): ", math.log(100.12))
print("math.log(100.72): ", math.log(100.72))
print("math.log(math.pi): ", math.log(math.pi))
```

以上实例输出结果如下：

```powershell
math.log(100.12):  4.6063694665635735
math.log(100.72):  4.612344389736092
math.log(math.pi):  1.1447298858494002
```

## log10(x)

###### 描述

返回以 10 为基数的 `x` 对数。

###### 语法

```python
import math
math.log10(x)
```

###### 参数

- x -- 数值表达式

###### 返回值

以 10 为基数的 `x` 对数。

###### 实例

```python
import math
print("math.log10(100.12): ", math.log10(100.12))
print("math.log10(100.72): ", math.log10(100.72))
print("math.log10(119): ", math.log10(119))
print("math.log10(math.pi): ", math.log10(math.pi))
```

以上实例输出结果如下：

```powershell
math.log10(100.12):  2.0005208409361854
math.log10(100.72):  2.003115717099806
math.log10(119):  2.0755469613925306
math.log10(math.pi):  0.49714987269413385
```

## max(x1, x2,...)

###### 描述

返回给定参数的最大值，参数可以为序列。

###### 语法

```python
max(x, y, z, ....)
```

###### 参数

- x -- 数值表达式
- y -- 数值表达式
- z -- 数值表达式

###### 返回值

给定参数的最大值。

###### 实例

```python
print("max(80, 100, 1000): ", max(80, 100, 1000))
print("max(-20, 100, 400): ", max(-20, 100, 400))
print("max(-80, -20, -10): ", max(-80, -20, -10))
print("max(0, 100, -400): ", max(0, 100, -400))
```

以上实例输出结果如下：

```powershell
max(80, 100, 1000):  1000
max(-20, 100, 400):  400
max(-80, -20, -10):  -10
max(0, 100, -400):  100
```

## min(x1, x2,...)

###### 描述

返回给定参数的最小值，参数可以为序列。

###### 语法

```python
min(x, y, z, ....)
```

###### 参数

- x -- 数值表达式
- y -- 数值表达式
- z -- 数值表达式

###### 返回值

给定参数的最小值。

###### 实例

```python
print("min(80, 100, 1000): ", min(80, 100, 1000))
print("min(-20, 100, 400): ", min(-20, 100, 400))
print("min(-80, -20, -10): ", min(-80, -20, -10))
print("min(0, 100, -400): ", min(0, 100, -400))
```

以上实例输出结果如下：

```powershell
min(80, 100, 1000):  80
min(-20, 100, 400):  -20
min(-80, -20, -10):  -80
min(0, 100, -400):  -400
```

## modf(x)

###### 描述

返回 `x` 的整数部分与小数部分，两部分的数值符号与 `x` 相同，整数部分以浮点型表示。

###### 语法

```python
import math
math.modf(x)
```

###### 参数

- x -- 数值表达式

###### 返回值

数值 `x` 的整数部分与小数部分。

###### 实例

```python
import math
print("math.modf(100.12): ", math.modf(100.12))
print("math.modf(100.72): ", math.modf(100.72))
print("math.modf(119): ", math.modf(119))
print("math.modf(math.pi): ", math.modf(math.pi))
```

以上实例输出结果如下：

```powershell
math.modf(100.12):  (0.12000000000000455, 100.0)
math.modf(100.72):  (0.7199999999999989, 100.0)
math.modf(119):  (0.0, 119.0)
math.modf(math.pi):  (0.14159265358979312, 3.0)
```

## pow(x, y[, z])

###### 描述

计算 `x` 的 `y` 次方，如果 `z` 存在，则再对结果进行取模，其结果等效于 `pow(x,y)%z`。

###### 语法

```python
pow(x, y[, z])
```

###### 参数

- x -- 数值表达式
- y -- 数值表达式
- z -- 数值表达式

###### 返回值

数值 `x` 的 `y` 次方的值，如果 `z` 存在，则再对结果进行取模。

###### 实例

```python
print("pow(100, 2): ", pow(100, 2))
```

以上实例输出结果如下：

```powershell
pow(100, 2):  10000
```

## math.pow(x, y)

###### 描述

返回 `x` 的 `y` 次方的值，与内置的 `pow()` 方法不同的是，内置的 `pow()` 方法把参数作为整型，而 `math` 模块则会把参数转换为 `float`。

###### 语法

```python
import math
math.pow(x, y)
```

###### 参数

- x -- 数值表达式
- y -- 数值表达式

###### 返回值

数值 `x` 的 `y` 次方的值。

###### 实例

```python
import math
print("math.pow(100, 2): ", math.pow(100, 2))
print("math.pow(100, -2): ", math.pow(100, -2))
print("math.pow(2, 4): ", math.pow(2, 4))
print("math.pow(3, 0): ", math.pow(3, 0))
```

以上实例输出结果如下：

```powershell
math.pow(100, 2):  10000.0
math.pow(100, -2):  0.0001
math.pow(2, 4):  16.0
math.pow(3, 0):  1.0
```

## round(x [,n])

###### 描述

返回浮点数 `x` 的四舍五入值。

###### 语法

```python
round(x[, n])
```

###### 参数

- x -- 数值表达式
- n -- 数值表达式

###### 返回值

浮点数 `x` 的四舍五入值。

###### 实例

```python
print("round(70.23456): ", round(70.23456))
print("round(56.659,1): ", round(56.659,1))
print("round(80.264, 2): ", round(80.264, 2))
print("round(100.000056, 3): ", round(100.000056, 3))
print("round(-100.000056, 3): ", round(-100.000056, 3))
```

以上实例输出结果如下：

```powershell
round(70.23456):  70
round(56.659,1):  56.7
round(80.264, 2):  80.26
round(100.000056, 3):  100.0
round(-100.000056, 3):  -100.0
```

## sqrt(x)

###### 描述

返回数字 `x` 的平方根。

###### 语法

```python
import math
math.sqrt(x)
```

###### 参数

- x -- 数值表达式

###### 返回值

数字 `x` 的平方根。

###### 实例

```python
import math
print("math.sqrt(100): ", math.sqrt(100))
print("math.sqrt(7): ", math.sqrt(7))
print("math.sqrt(math.pi): ", math.sqrt(math.pi))
```

以上实例输出结果如下：

```powershell
math.sqrt(100):  10.0
math.sqrt(7):  2.6457513110645907
math.sqrt(math.pi):  1.7724538509055159
```
