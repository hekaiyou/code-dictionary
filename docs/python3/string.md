# Python3 字符串 {docsify-ignore}

### capitalize()

###### 描述

将字符串的第一个字母变成大写，其他字母变小写。

###### 语法

```python
str.capitalize()
```

###### 返回值

一个首字母大写的字符串。

###### 实例

```python
str = "this is string example from you....wow!!!"
print("str.capitalize(): ", str.capitalize())
```

以上实例输出结果如下：

```powershell
str.capitalize():  This is string example from you....wow!!!
```

### center(width, fillchar)

###### 描述

一个指定的宽度 `width` 居中的字符串，`fillchar` 为填充的字符，默认为空格。

###### 语法

```python
str.center(width[, fillchar])
```

###### 参数

- width -- 字符串的总宽度
- fillchar -- 填充字符

###### 返回值

一个指定的宽度 `width` 居中的字符串，如果 `width` 小于字符串宽度直接返回字符串，否则使用 `fillchar` 去填充。

###### 实例

```python
str = "[www.you.com]"
print("str.center(40, '*'): ", str.center(40, '*'))
```

以上实例输出结果如下：

```powershell
str.center(40, '*'):  ************[www.you.com]************
```

### count(str, beg=0, end=len(string))

###### 描述

统计字符串里某个字符出现的次数，可选参数为在字符串搜索的开始与结束位置。

###### 语法

```python
str.count(sub, start=0, end=len(string))
```

###### 参数

- sub -- 搜索的子字符串
- start -- 字符串开始搜索的位置，默认为第一个字符，第一个字符索引值为0
- end -- 字符串中结束搜索的位置，字符中第一个字符的索引为0，默认为字符串的最后一个位置

###### 返回值

子字符串在字符串中出现的次数。

###### 实例

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

### bytes.decode(encoding="utf-8", errors="strict")

###### 描述

以指定的编码格式解码 `bytes` 对象，默认编码为 `utf-8`。

###### 语法

```python
bytes.decode(encoding="utf-8", errors="strict")
```

###### 参数

- encoding -- 要使用的编码，如"UTF-8"
- errors -- 设置不同错误的处理方案，默认为'strict'，意为编码错误引起一个UnicodeError。其他可能的值有'ignore'、'replace'、'xmlcharrefreplace'、'backslashreplace'以及通过codecs.register_error()注册的任何值

###### 返回值

解码后的字符串。

###### 实例

```python
str = "you示例"
str_utf8 = str.encode("UTF-8")
str_gbk = str.encode("GBK")
print(str)
print("UTF-8 编码：", str_utf8)
print("GBK 编码：", str_gbk)
print("UTF-8 解码：", str_utf8.decode('UTF-8','strict'))
print("GBK 解码：", str_gbk.decode('GBK','strict'))
```

以上实例输出结果如下：

```powershell
you示例
UTF-8 编码： b'you\xe7\xa4\xba\xe4\xbe\x8b'
GBK 编码： b'you\xca\xbe\xc0\xfd'
UTF-8 解码： you示例
GBK 解码： you示例
```

### encode(encoding='UTF-8', errors='strict')

###### 描述

以指定的编码格式编码字符串，`errors` 参数可以指定不同的错误处理方案。

###### 语法

```python
str.encode(encoding='UTF-8', errors='strict')
```

###### 参数

- encoding -- 要使用的编码，如: UTF-8
- errors -- 设置不同错误的处理方案，默认为'strict'，意为编码错误引起一个UnicodeError。其他可能的值有'ignore'、'replace'、'xmlcharrefreplace'、'backslashreplace'以及通过codecs.register_error()注册的任何值

###### 返回值

编码后的字符串，它是一个 `bytes` 对象。

###### 实例

```python
str = "you示例"
str_utf8 = str.encode("UTF-8")
str_gbk = str.encode("GBK")
print(str)
print("UTF-8 编码：", str_utf8)
print("GBK 编码：", str_gbk)
print("UTF-8 解码：", str_utf8.decode('UTF-8','strict'))
print("GBK 解码：", str_gbk.decode('GBK','strict'))
```

以上实例输出结果如下：

```powershell
you示例
UTF-8 编码： b'you\xe7\xa4\xba\xe4\xbe\x8b'
GBK 编码： b'you\xca\xbe\xc0\xfd'
UTF-8 解码： you示例
GBK 解码： you示例
```
