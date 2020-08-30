# Python3 元组 {docsify-ignore}

## len(tuple)

###### 描述

计算元组元素个数。

###### 语法

```python
len(tuple)
```

###### 实例

```python
tuple1 = ('Google', 'You', 'Taobao')
x = len(tuple1)
print(x)
```

以上实例输出结果如下：

```powershell
3
```

## max(tuple)

###### 描述

返回元组中元素最大值。

###### 语法

```python
max(tuple)
```

###### 实例

```python
tuple2 = ('5', '4', '8')
x = max(tuple2)
print(x)
```

以上实例输出结果如下：

```powershell
8
```

## min(tuple)

###### 描述

返回元组中元素最小值。

###### 语法

```python
min(tuple)
```

###### 实例

```python
tuple2 = ('5', '4', '8')
x = min(tuple2)
print(x)
```

以上实例输出结果如下：

```powershell
4
```

## tuple(seq)

###### 描述

将列表转换为元组。

###### 语法

```python
tuple(seq)
```

###### 实例

```python
list1 = ['Google', 'Taobao', 'You', 'Baidu']
tuple1 = tuple(list1)
print(tuple1)
```

以上实例输出结果如下：

```powershell
('Google', 'Taobao', 'You', 'Baidu')
```

## tuple.index(obj)

###### 描述

从元组中找出某个对象第一个匹配项的索引位置，如果这个对象不在元组中会报一个异常。

###### 语法

```python
tuple.index(obj[,start=0[,end=len(tuple)]])
```

###### 参数

- obj -- 指定检索的对象

###### 实例

```python
T = ('Google', 'You', 'Taobao')
print(T.index('Taobao'))
print(T.index('Google', 1))
```

以上实例输出结果如下：

```powershell
2
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: tuple.index(x): x not in tuple
```

## tuple.count(obj)

###### 描述

统计某个元素在元组中出现的次数。

###### 语法

```python
tuple.count(obj)
```

###### 参数

- obj -- 元组中统计的对象

###### 实例

```python
T = (123, 'Google', 'You', 'Taobao', 123)
print("123 元素个数: ", T.count(123))
print("You 元素个数: ", T.count('You'))
```

以上实例输出结果如下：

```powershell
123 元素个数:  2
You 元素个数:  1
```
