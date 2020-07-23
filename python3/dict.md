# Python3 字典 {docsify-ignore}

## radiansdict.clear()

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

## radiansdict.copy()

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
