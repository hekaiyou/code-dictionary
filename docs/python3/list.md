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
