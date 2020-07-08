### capitalize()

##### 描述

将字符串的第一个字母变成大写，其他字母变小写。

##### 语法

```python
str.capitalize()
```

##### 返回值

该方法返回一个首字母大写的字符串。

##### 实例

```python
str = "this is string example from you....wow!!!"
print("str.capitalize(): ", str.capitalize())
```

以上实例输出结果如下：

```powershell
str.capitalize():  This is string example from you....wow!!!
```

### center(width, fillchar)

##### 描述

返回一个指定的宽度 `width` 居中的字符串，`fillchar` 为填充的字符，默认为空格。

##### 语法

```python
str.center(width[, fillchar])
```

##### 参数

- width -- 字符串的总宽度
- fillchar -- 填充字符

##### 返回值

返回一个指定的宽度 `width` 居中的字符串，如果 `width` 小于字符串宽度直接返回字符串，否则使用 `fillchar` 去填充。

##### 实例

```python
str = "[www.you.com]"
print("str.center(40, '*'): ", str.center(40, '*'))
```

以上实例输出结果如下：

```powershell
str.center(40, '*'):  ************[www.you.com]************
```

### count(str, beg=0, end=len(string))

##### 描述

统计字符串里某个字符出现的次数，可选参数为在字符串搜索的开始与结束位置。

##### 语法

```python
str.count(sub, start=0, end=len(string))
```

##### 参数

- sub -- 搜索的子字符串
- start -- 字符串开始搜索的位置，默认为第一个字符，第一个字符索引值为0
- end -- 字符串中结束搜索的位置，字符中第一个字符的索引为0，默认为字符串的最后一个位置

##### 返回值

返回子字符串在字符串中出现的次数。

##### 实例

```python
str="www.you.com"
sub='x'
print ("str.count('x'): ", str.count(sub))
sub='w'
print ("str.count('w', 0, 10): ", str.count(sub, 0, 10))
```

以上实例输出结果如下：

```powershell
str.count('y'):  1
str.count('w', 0, 10):  3
```
