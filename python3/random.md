# Python3 随机数 {docsify-ignore}

## choice(seq)

###### 描述

返回一个列表，元组或字符串的随机项。

###### 语法

```python
import random
random.choice(seq)
```

###### 参数

- seq -- 可以是一个列表，元组或字符串

###### 返回值

随机项。

###### 实例

```python
import random
print("从 range(100) 返回一个随机数: ",random.choice(range(100)))
print("从列表中 [1, 2, 3, 5, 9]) 返回一个随机元素: ", random.choice([1, 2, 3, 5, 9]))
print("从字符串中 'You' 返回一个随机字符: ", random.choice('You'))
```

以上实例输出结果如下：

```powershell
从 range(100) 返回一个随机数:  13
从列表中 [1, 2, 3, 5, 9]) 返回一个随机元素:  5
从字符串中 'You' 返回一个随机字符:  o
```
