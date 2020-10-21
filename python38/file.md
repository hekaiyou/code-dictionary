# Python3 文件 {docsify-ignore}

## file.close()

###### 描述

关闭一个已打开的文件，关闭后的文件不能再进行读写操作，否则会触发 `ValueError` 错误，该方法允许调用多次。当 `file` 对象被引用到操作另外一个文件时，Python会自动关闭之前的 `file` 对象。

###### 语法

```python
file.close()
```

###### 实例

```python
fo = open("Test.txt", "wb")
print("文件名为: ", fo.name)
fo.close()
```

以上实例输出结果如下：

```powershell
文件名为:  Test.txt
```

## file.flush()

###### 描述

刷新缓冲区，即将缓冲区中的数据立刻写入文件，同时清空缓冲区，不需要是被动的等待输出缓冲区写入。一般情况下，文件关闭后会自动刷新缓冲区，但有时需要在关闭前刷新它。

###### 语法

```python
file.flush()
```

###### 实例

```python
fo = open("Test.txt", "wb")
print("文件名为: ", fo.name)
fo.flush()
fo.close()
```

以上实例输出结果如下：

```powershell
文件名为:  Test.txt
```

## file.fileno()

###### 描述

返回一个整型的文件描述符，可用于底层操作系统的 I/O 操作。

###### 语法

```python
fileObject.fileno()
```

###### 返回值

文件描述符。

###### 实例

```python
fo = open("Test.txt", "wb")
print("文件名为: ", fo.name)
fid = fo.fileno()
print("文件描述符为: ", fid)
fo.close()
```

以上实例输出结果如下：

```powershell
文件名为:  Test.txt
文件描述符为:  3
```

## file.isatty()

###### 描述

检测文件是否连接到一个终端设备，如果是返回 `True`，否则返回 `False`。

###### 语法

```python
fileObject.isatty()
```

###### 返回值

如果连接到一个终端设备返回 `True`，否则返回 `False`。

###### 实例

```python
fo = open("Test.txt", "wb")
print("文件名为: ", fo.name)
ret = fo.isatty()
print("返回值: ", ret)
fo.close()
```

以上实例输出结果如下：

```powershell
文件名为:  Test.txt
返回值:  False
```

## file.next()

###### 描述

通过迭代器调用 `__next__()` 方法返回下一项。在循环中，`next()` 方法会在每次循环中调用，该方法返回文件的下一行，如果到达结尾(EOF)，则触发 `StopIteration`。

###### 语法

```python
next(iterator[, default])
```

###### 返回值

返回文件下一行。

###### 实例

```python
fo = open("Test.txt", "wb")
print("文件名为: ", fo.name)
for index in range(5):
    line = next(fo)
    print("第 %d 行 - %s" % (index, line))
fo.close()
```

以上实例输出结果如下：

```powershell
文件名为:  Test.txt
第 0 行 - 这是第一行
第 1 行 - 这是第二行
第 2 行 - 这是第三行
第 3 行 - 这是第四行
第 4 行 - 这是第五行
```

## file.read([size])

###### 描述

从文件读取指定的字节数，如果未给定或为负则读取所有。

###### 语法

```python
fileObject.read()
```

###### 参数

- size -- 从文件中读取的字节数

###### 返回值

从字符串中读取的字节。

###### 实例

```python
fo = open("Test.txt", "wb")
print("文件名为: ", fo.name)
line = fo.read(10)
print("读取的字符串: %s" % (line))
fo.close()
```

以上实例输出结果如下：

```powershell
文件名为:  Test.txt
读取的字符串: 这是第一行
这是第二
```
