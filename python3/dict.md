# Python3 字典 {docsify-ignore}

## dict.clear()

###### 描述

删除字典内所有元素。

###### 语法

```python
dict.clear()
```

###### 实例

```python
dict = {'Name': 'Zara', 'Age': 7}
print("字典长度: %d" %  len(dict))
dict.clear()
print("字典删除后长度: %d" %  len(dict))
```

以上实例输出结果如下：

```powershell
字典长度: 2
字典删除后长度: 0
```

## dict.copy()

###### 描述

返回一个字典的浅复制，即只复制指向字典对象的指针，而不复制对象本身，新旧对象还是共享同一块内存。

###### 语法

```python
dict.copy()
```

###### 返回值

一个字典的浅复制。

###### 实例

```python
dict1 = {'Name': 'You', 'Age': 7, 'Class': 'First'}
dict2 = dict1.copy()
print("新复制的字典为: ", dict2)
```

以上实例输出结果如下：

```powershell
新复制的字典为:  {'Age': 7, 'Name': 'You', 'Class': 'First'}
```

## dict.fromkeys()

###### 描述

创建一个新字典，以序列 `seq` 中元素做字典的键，`value` 为字典所有键对应的初始值。

###### 语法

```python
dict.fromkeys(seq[, value]))
```

###### 参数

- seq -- 字典键值列表
- value -- 可选参数，设置键序列（seq）的值

###### 返回值

一个新字典。

###### 实例

```python
tuple1 = ('name', 'age', 'sex')
dict1 = dict.fromkeys(tuple1)
print("新的字典为: %s" % str(dict1))
dict1 = dict.fromkeys(tuple1, 10)
print("新的字典为: %s" % str(dict1))
```

以上实例输出结果如下：

```powershell
新的字典为: {'name': None, 'age': None, 'sex': None}
新的字典为: {'name': 10, 'age': 10, 'sex': 10}
```
