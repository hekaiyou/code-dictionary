# Python3 小手册

## 字符串

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

- width -- 字符串的总宽度。
- fillchar -- 填充字符。

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
