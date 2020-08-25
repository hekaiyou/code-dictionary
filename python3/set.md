# Python3 集合 {docsify-ignore}

## add()

###### 描述

给集合添加元素，如果添加的元素在集合中已存在，则不执行任何操作。

###### 语法

```python
set.add(elmnt)
```

###### 参数

- elmnt -- 必需，要添加的元素

###### 实例

```python
fruits = {"apple", "banana", "cherry"}
fruits.add("orange") 
print(fruits)
fruits.add("apple")
print(fruits)
```

以上实例输出结果如下：

```powershell
{'apple', 'orange', 'cherry', 'banana'}
{'apple', 'orange', 'cherry', 'banana'}
```

## clear()

###### 描述

移除集合中的所有元素。

###### 语法

```python
set.clear()
```

###### 实例

```python
fruits = {"apple", "banana", "cherry"}
fruits.clear()
print(fruits)
```

以上实例输出结果如下：

```powershell
set()
```

## clear()

###### 描述

拷贝一个集合。

###### 语法

```python
set.copy()
```

###### 实例

```python
fruits = {"apple", "banana", "cherry"}
x = fruits.copy()
print(x)
```

以上实例输出结果如下：

```powershell
{'apple', 'cherry', 'banana'}
```

## difference()

###### 描述

返回集合的差集，即返回的集合元素包含在第一个集合中，但不包含在第二个集合（方法的参数）中。

###### 语法

```python
set.difference(set)
```

###### 参数

- set -- 必需，用于计算差集的集合

###### 返回值

一个新的集合。

###### 实例

```python
x = {"apple", "banana", "cherry"}
y = {"google", "microsoft", "apple"}
z = x.difference(y)
print(z)
```

以上实例输出结果如下：

```powershell
{'banana', 'cherry'}
```

## difference_update()

###### 描述

移除两个集合中都存在的元素，与 `difference()` 方法的区别在于 `difference()` 方法返回一个移除相同元素的新集合，而 `difference_update()` 方法是直接在原来的集合中移除元素，没有返回值。

###### 语法

```python
set.difference_update(set)
```

###### 参数

- set -- 必需，用于计算差集的集合

###### 实例

```python
x = {"apple", "banana", "cherry"}
y = {"google", "microsoft", "apple"}
x.difference_update(y)
print(x)
```

以上实例输出结果如下：

```powershell
{'cherry', 'banana'}
```

## discard()

###### 描述

移除指定的集合元素，该方法不同于 `remove()` 方法，因为 `remove()` 方法在移除一个不存在的元素时会发生错误，而 `discard()` 方法不会。

###### 语法

```python
set.discard(value)
```

###### 参数

- value -- 必需，要移除的元素

###### 实例

```python
fruits = {"apple", "banana", "cherry"}
fruits.discard("banana")
print(fruits)
```

以上实例输出结果如下：

```powershell
{'apple', 'cherry'}
```

## intersection()

###### 描述

返回两个或更多集合中都包含的元素，即交集。

###### 语法

```python
set.intersection(set1, set2 ... etc)
```

###### 参数

- set1 -- 必需，要查找相同元素的集合
- set2 -- 可选，其他要查找相同元素的集合，可以使用多个逗号隔开

###### 返回值

一个新的集合。

###### 实例

```python
x = {"apple", "banana", "cherry"}
y = {"google", "w3xue", "apple"}
z = x.intersection(y)
print(z)
```

以上实例输出结果如下：

```powershell
{'apple'}
```
