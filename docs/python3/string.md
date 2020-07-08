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

### endswith(suffix, beg=0, end=len(string))

###### 描述

判断字符串是否以指定后缀结尾，如果以指定后缀结尾返回 `True`，否则返回 `False`。可选参数 `start` 与 `end` 为检索字符串的开始与结束位置。

###### 语法

```python
str.endswith(suffix[, start[, end]])
```

###### 参数

- suffix -- 该参数可以是一个字符串或者是一个元素
- start -- 字符串中的开始位置
- end -- 字符中结束位置

###### 返回值

如果字符串含有指定的后缀返回 `True`，否则返回 `False`。

###### 实例

```python
Str='you example....wow!!!'
suffix='!!'
print(Str.endswith(suffix))
print(Str.endswith(suffix,17))
suffix='run'
print(Str.endswith(suffix))
print(Str.endswith(suffix, 0, 16))
```

以上实例输出结果如下：

```powershell
True
True
False
False
```

### expandtabs(tabsize=8)

###### 描述

把字符串中的tab符号('\t')转为空格，tab符号('\t')默认的空格数是8。

###### 语法

```python
str.expandtabs(tabsize=8)
```

###### 参数

- tabsize -- 指定转换字符串中的tab符号('\t')转为空格的字符数

###### 返回值

字符串中的tab符号('\t')转为空格后生成的新字符串。

###### 实例

```python
str = "this is\tstring example....wow!!!"
print("原始字符串: " + str)
print("替换 \\t 符号: " +  str.expandtabs())
print("使用16个空格替换 \\t 符号: " +  str.expandtabs(16))
```

以上实例输出结果如下：

```powershell
原始字符串: this is     string example....wow!!!
替换 \t 符号: this is string example....wow!!!
使用16个空格替换 \t 符号: this is         string example....wow!!!
```

### find(str, beg=0 end=len(string))

###### 描述

检测字符串中是否包含子字符串 `str`，如果指定 `beg`（开始）和 `end`（结束）范围，则检查是否包含在指定范围内，如果包含子字符串返回开始的索引值，否则返回-1。

###### 语法

```python
str.find(str, beg=0, end=len(string))
```

###### 参数

- str -- 指定检索的字符串
- beg -- 开始索引，默认为0
- end -- 结束索引，默认为字符串的长度

###### 返回值

如果包含子字符串返回开始的索引值，否则返回-1。

###### 实例

```python
str1 = "you example....wow!!!"
str2 = "exam"
print(str1.find(str2))
print(str1.find(str2, 3))
print(str1.find(str2, 7))
```

以上实例输出结果如下：

```powershell
4
4
-1
```

### index(str, beg=0, end=len(string))

###### 描述

检测字符串中是否包含子字符串 `str`，如果指定 `beg`（开始）和 `end`（结束）范围，则检查是否包含在指定范围内，该方法与 `find()` 方法一样，只不过如果 `str` 不在 `string` 中会报一个异常。

###### 语法

```python
str.index(str, beg=0, end=len(string))
```

###### 参数

- str -- 指定检索的字符串
- beg -- 开始索引，默认为0
- end -- 结束索引，默认为字符串的长度

###### 返回值

如果包含子字符串返回开始的索引值，否则抛出异常。

###### 实例

```python
str1 = "you example....wow!!!"
str2 = "exam"
print(str1.index(str2))
print(str1.index(str2, 3))
print(str1.index(str2, 7))
```

以上实例输出结果如下：

```powershell
4
4
Traceback (most recent call last):
  File "test.py", line 5, in <module>
    print (str1.index(str2, 7))
ValueError: substring not found
```

### isalnum()

###### 描述

检测字符串是否由字母和数字组成。

###### 语法

```python
str.isalnum()
```

###### 返回值

如果 `string` 至少有一个字符并且所有字符都是字母或数字则返回 `True`，否则返回 `False`。

###### 实例

```python
str = "you2020"
print(str.isalnum())
str = "www.you.com"
print(str.isalnum())
```

以上实例输出结果如下：

```powershell
True
False
```

### isalpha()

###### 描述

检测字符串是否只由字母组成。

###### 语法

```python
str.isalpha()
```

###### 返回值

如果字符串至少有一个字符并且所有字符都是字母则返回 `True`，否则返回 `False`。

###### 实例

```python
str = "example"
print(str.isalpha())
str = "you example....wow!!!"
print(str.isalpha())
```

以上实例输出结果如下：

```powershell
True
False
```

### isdigit()

###### 描述

检测字符串是否只由数字组成。

###### 语法

```python
str.isdigit()
```

###### 返回值

如果字符串只包含数字则返回 `True` 否则返回 `False`。

###### 实例

```python
str = "123456"; 
print(str.isdigit())
str = "you example....wow!!!"
print(str.isdigit())
```

以上实例输出结果如下：

```powershell
True
False
```

### islower()

###### 描述

检测字符串是否由小写字母组成。

###### 语法

```python
str.islower()
```

###### 返回值

如果字符串中包含至少一个区分大小写的字符，并且所有这些（区分大小写的）字符都是小写，则返回 `True`，否则返回 `False`。

###### 实例

```python
str = "You example....wow!!!"
print(str.islower())
str = "you example....wow!!!"
print(str.islower())
```

以上实例输出结果如下：

```powershell
False
True
```

### isnumeric()

###### 描述

检测字符串是否只由数字组成，这种方法是只针对 `unicode` 对象。

###### 语法

```python
str.isnumeric()
```

###### 返回值

如果字符串中只包含数字字符，则返回 `True`，否则返回 `False`。

###### 实例

```python
str = "you2020"  
print(str.isnumeric())
str = "23443434"
print(str.isnumeric())
```

以上实例输出结果如下：

```powershell
False
True
```

### isspace()

###### 描述

检测字符串是否只由空格组成。

###### 语法

```python
str.isspace()
```

###### 返回值

如果字符串中只包含空格，则返回 `True`，否则返回 `False`。

###### 实例

```python
str = "       " 
print(str.isspace())
str = "you example....wow!!!"
print(str.isspace())
```

以上实例输出结果如下：

```powershell
True
False
```

### istitle()

###### 描述

检测字符串中所有的单词拼写首字母是否为大写，且其他字母为小写。

###### 语法

```python
str.istitle()
```

###### 返回值

如果字符串中所有的单词拼写首字母是否为大写，且其他字母为小写则返回 `True`，否则返回 `False`。

###### 实例

```python
str = "This Is String Example...Wow!!!"
print(str.istitle())
str = "This is string example....wow!!!"
print(str.istitle())
```

以上实例输出结果如下：

```powershell
True
False
```

### isupper()

###### 描述

检测字符串中所有的字母是否都为大写。

###### 语法

```python
str.isupper()
```

###### 返回值

如果字符串中包含至少一个区分大小写的字符，并且所有这些(区分大小写的)字符都是大写，则返回 `True`，否则返回 `False`。

###### 实例

```python
str = "THIS IS STRING EXAMPLE....WOW!!!"
print(str.isupper())
str = "THIS is string example....wow!!!"
print(str.isupper())
```

以上实例输出结果如下：

```powershell
True
False
```

### join(seq)

###### 描述

将序列中的元素以指定的字符连接生成一个新的字符串。

###### 语法

```python
str.join(sequence)
```

###### 参数

- sequence -- 要连接的元素序列

###### 返回值

通过指定字符连接序列中元素后生成的新字符串。

###### 实例

```python
s1 = "-"
s2 = ""
seq = ("Y", "o", "u", "2", "3")
print(s1.join(seq))
print(s2.join(seq))
```

以上实例输出结果如下：

```powershell
Y-o-u-2-3
You23
```
