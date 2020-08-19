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
