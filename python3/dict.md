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

## dict.get(key, default=None)

###### 描述

返回指定键的值，如果值不在字典中则返回默认值。

###### 语法

```python
dict.get(key, default=None)
```

###### 参数

- key -- 字典中要查找的键
- default -- 如果指定键的值不存在时，返回该默认值值

###### 返回值

指定键的值，如果值不在字典中则返回默认值 `None`。

###### 实例

```python
dict1 = {'Name': 'You', 'Age': 27}
print("Age 值为: %s" % dict1.get('Age'))
print("Sex 值为: %s" % dict1.get('Sex', "NA"))
```

以上实例输出结果如下：

```powershell
Age 值为: 27
Sex 值为: NA
```

## key in dict

###### 描述

判断键是否存在于字典中，如果键在字典 `dict` 里返回 `True`，否则返回 `False`。

###### 语法

```python
key in dict
```

###### 参数

- key -- 要在字典中查找的键

###### 返回值

如果键在字典里返回 `True`，否则返回 `False`。

###### 实例

```python
dict1 = {'Name': 'You', 'Age': 7}
if 'Age' in dict1:
    print("键 Age 存在")
else:
	print("键 Age 不存在")
if 'Age' not in dict1:
    print("键 Age 不存在")
else:
    print("键 Age 存在")
```

以上实例输出结果如下：

```powershell
键 Age 存在
键 Age 存在
```

## dict.items()

###### 描述

以列表返回可遍历的键值对（`key`:`value`）元组数组。

###### 语法

```python
dict.items()
```

###### 返回值

可遍历的键值对（`key`:`value`）元组数组。

###### 实例

```python
dict1 = {'Name': 'You', 'Age': 7}
print("Value: %s" % dict1.items())
```

以上实例输出结果如下：

```powershell
Value: dict_items([('Name', 'You'), ('Age', 7)])
```

## dict.keys()

###### 描述

以列表返回一个字典所有的键。

###### 语法

```python
dict.keys()
```

###### 返回值

一个字典所有的键。

###### 实例

```python
dict = {'Name': 'You', 'Age': 7}
print("字典所有的键为: %s" % dict.keys())
```

以上实例输出结果如下：

```powershell
字典所有的键为: dict_keys(['Name', 'Age'])
```

## dict.setdefault(key, default=None)

###### 描述

和 `get()` 方法类似，如果键不已经存在于字典中，将会添加键并将值设为默认值。

###### 语法

```python
dict.setdefault(key, default=None)
```

###### 参数

- key -- 查找的键值
- default -- 键不存在时，设置的默认键值

###### 实例

```python
dict = {'Name': 'You', 'Age': 7}
print("Age 键的值为: %s" %  dict.setdefault('Age', None))
print("Sex 键的值为: %s" %  dict.setdefault('Sex', None))
print("新字典为：", dict)
```

以上实例输出结果如下：

```powershell
Age 键的值为: 7
Sex 键的值为: None
新字典为： {'Name': 'You', 'Age': 7, 'Sex': None}
```

## dict.update(dict2)

###### 描述

把字典 `dict2` 的键/值对更新到 `dict` 里。

###### 语法

```python
dict.update(dict2)
```

###### 参数

- dict2 -- 添加到指定字典dict里的字典

###### 实例

```python
dict1 = {'Name': 'You', 'Age': 7}
dict2 = {'Sex': 'female'}
dict1.update(dict2)
print("更新字典 dict1: ", dict1)
```

以上实例输出结果如下：

```powershell
更新字典 dict1:  {'Name': 'You', 'Age': 7, 'Sex': 'female'}
```

## dict.values()

###### 描述

以列表返回字典中的所有值。

###### 语法

```python
dict.values()
```

###### 返回值

字典中的所有值。

###### 实例

```python
dict1 = {'Sex': 'female', 'Age': 7, 'Name': 'Zara'}
print("字典所有值为: ",  list(dict1.values()))
```

以上实例输出结果如下：

```powershell
字典所有值为:  ['female', 7, 'Zara']
```
