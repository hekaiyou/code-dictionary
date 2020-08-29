# Python3 时间 {docsify-ignore}

## center(width, fillchar)

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
