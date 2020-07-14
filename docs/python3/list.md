# Python3 列表 {docsify-ignore}

## len(list)

###### 描述

返回列表元素个数。

###### 语法

```python
len(list)
```

###### 参数

- list -- 要计算元素个数的列表

###### 返回值

列表元素个数。

###### 实例

```python
list1 = ['Google', 'You', 'Taobao']
print(len(list1))
list2 = list(range(5))
print(len(list2))
```

以上实例输出结果如下：

```powershell
3
5
```

## max(list)

###### 描述

返回列表元素中的最大值。

###### 语法

```python
max(list)
```

###### 参数

- list -- 要返回最大值的列表

###### 返回值

列表元素中的最大值。

###### 实例

```python
list1, list2 = ['Google', 'You', 'Taobao'], [456, 700, 200]
print("list1 最大元素值: ", max(list1))
print("list2 最大元素值: ", max(list2))
```

以上实例输出结果如下：

```powershell
list1 最大元素值:  You
list2 最大元素值:  700
```

## min(list)

###### 描述

返回列表元素中的最小值。

###### 语法

```python
min(list)
```

###### 参数

- list -- 要返回最小值的列表

###### 返回值

列表元素中的最小值。

###### 实例

```python
list1, list2 = ['Google', 'You', 'Taobao'], [456, 700, 200]
print("list1 最小元素值: ", min(list1))
print("list2 最小元素值: ", min(list2))
```

以上实例输出结果如下：

```powershell
list1 最小元素值:  Google
list2 最小元素值:  200
```

## list(seq)

###### 描述

将元组转换为列表。（元组与列表是非常类似的，区别在于元组的元素值不能修改，元组是放在括号中，列表是放于方括号中。）

###### 语法

```python
list(seq)
```

###### 参数

- list -- 要转换为列表的元组

###### 返回值

列表。

###### 实例

```python
aTuple = (123, 'Google', 'You', 'Taobao')
list1 = list(aTuple)
print("列表元素: ", list1)
str = "Hello World"
list2 = list(str)
print("列表元素: ", list2)
```

以上实例输出结果如下：

```powershell
列表元素:  [123, 'Google', 'You', 'Taobao']
列表元素:  ['H', 'e', 'l', 'l', 'o', ' ', 'W', 'o', 'r', 'l', 'd']
```

## list.append(obj)

###### 描述

在列表末尾添加新的对象。

###### 语法

```python
list.append(obj)
```

###### 参数

- obj -- 添加到列表末尾的对象

###### 返回值

无返回值，但是会修改原来的列表。

###### 实例

```python
list1 = ['Google', 'You', 'Taobao']
list1.append('Baidu')
print("更新后的列表: ", list1)
```

以上实例输出结果如下：

```powershell
更新后的列表:  ['Google', 'You', 'Taobao', 'Baidu']
```

## list.count(obj)

###### 描述

统计某个元素在列表中出现的次数。

###### 语法

```python
list.count(obj)
```

###### 参数

- obj -- 列表中统计的对象

###### 返回值

元素在列表中出现的次数。

###### 实例

```python
aList = [123, 'Google', 'You', 'Taobao', 123]
print("123 元素个数: ", aList.count(123))
print("You 元素个数: ", aList.count('You'))
```

以上实例输出结果如下：

```powershell
123 元素个数:  2
You 元素个数:  1
```

## list.extend(seq)

###### 描述

在列表末尾一次性追加另一个序列中的多个值（用新列表扩展原来的列表）。

###### 语法

```python
list.extend(seq)
```

###### 参数

- seq -- 元素列表

###### 返回值

没有返回值，但会在已存在的列表中添加新的列表内容。

###### 实例

```python
list1 = ['Google', 'You', 'Taobao']
list2 = list(range(5))
list1.extend(list2)
print("扩展后的列表：", list1)
```

以上实例输出结果如下：

```powershell
扩展后的列表： ['Google', 'You', 'Taobao', 0, 1, 2, 3, 4]
```

## list.index(obj)

###### 描述

从列表中找出某个值第一个匹配项的索引位置。

###### 语法

```python
list.index(obj)
```

###### 参数

- obj -- 查找的对象

###### 返回值

查找对象的索引位置，如果没有找到对象则抛出异常。

###### 实例

```python
list1 = ['Google', 'You', 'Taobao']
print('You 索引值为', list1.index('You'))
print('Taobao 索引值为', list1.index('Taobao'))
```

以上实例输出结果如下：

```powershell
You 索引值为 1
Taobao 索引值为 2
```

## list.insert(index, obj)

###### 描述

将指定对象插入列表的指定位置。

###### 语法

```python
list.insert(index, obj)
```

###### 参数

- index -- 对象obj需要插入的索引位置
- obj -- 要插入列表中的对象

###### 返回值

没有返回值，但会在列表指定位置插入对象。

###### 实例

```python
list1 = ['Google', 'You', 'Taobao']
list1.insert(1, 'Baidu')
print('列表插入元素后为: ', list1)
```

以上实例输出结果如下：

```powershell
列表插入元素后为:  ['Google', 'Baidu', 'You', 'Taobao']
```

## list.pop(obj=list[-1])

###### 描述

移除列表中的一个元素（默认最后一个元素），并且返回该元素的值。

###### 语法

```python
list.pop(obj=list[-1])
```

###### 参数

- obj -- 可选参数，要移除列表元素的对象

###### 返回值

从列表中移除的元素对象。

###### 实例

```python
list1 = ['Google', 'You', 'Taobao']
list1.pop()
print("列表现在为: ", list1)
list1.pop(1)
print("列表现在为: ", list1)
```

以上实例输出结果如下：

```powershell
列表现在为 :  ['Google', 'You']
列表现在为 :  ['Google']
```

## list.remove(obj)

###### 描述

移除列表中某个值的第一个匹配项。

###### 语法

```python
list.remove(obj)
```

###### 参数

- obj -- 列表中要移除的对象

###### 返回值

没有返回值，但是会移除列表中的某个值的第一个匹配项。

###### 实例

```python
list1 = ['Google', 'You', 'Taobao', 'Baidu']
list1.remove('Taobao')
print("列表现在为: ", list1)
list1.remove('Baidu')
print("列表现在为: ", list1)
```

以上实例输出结果如下：

```powershell
列表现在为 :  ['Google', 'You', 'Baidu']
列表现在为 :  ['Google', 'You']
```

## list.reverse()

###### 描述

反向列表中元素。

###### 语法

```python
list.reverse()
```

###### 返回值

没有返回值，但是会对列表的元素进行反向排序。

###### 实例

```python
list1 = ['Google', 'You', 'Taobao', 'Baidu']
list1.reverse()
print("列表反转后: ", list1)
```

以上实例输出结果如下：

```powershell
列表反转后:  ['Baidu', 'Taobao', 'You', 'Google']
```

## list.sort([func])

###### 描述

对原列表进行排序，如果指定参数，则使用比较函数指定的比较函数。

###### 语法

```python
list.sort([func])
```

###### 参数

- func -- 可选参数, 如果指定了该参数会使用该参数的方法进行排序

###### 返回值

没有返回值，但是会对列表的对象进行排序。

###### 实例

```python
list1 = ['Google', 'You', 'Taobao', 'Baidu']
list1.sort()
print("列表排序后: ", list1)
```

以上实例输出结果如下：

```powershell
列表排序后:  ['Baidu', 'Google', 'You', 'Taobao']
```

## list.clear()

###### 描述

清空列表，类似于 `del a[:]`。

###### 语法

```python
list.clear()
```

###### 实例

```python
list1 = ['Google', 'You', 'Taobao', 'Baidu']
list1.clear()
print("列表清空后: ", list1)
```

以上实例输出结果如下：

```powershell
列表清空后:  []
```

## list.copy()

###### 描述

复制列表，类似于 `a[:]`。

###### 语法

```python
list.copy()
```

###### 返回值

复制后的新列表。

###### 实例

```python
list1 = ['Google', 'You', 'Taobao', 'Baidu']
list2 = list1.copy()
print("list2 列表: ", list2)
```

以上实例输出结果如下：

```powershell
list2 列表:  ['Google', 'You', 'Taobao', 'Baidu']
```
