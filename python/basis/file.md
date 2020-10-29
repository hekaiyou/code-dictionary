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
fo = open("Test.txt", "r")
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
fo = open("Test.txt", "r+")
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

## file.readline([size])

###### 描述

从文件读取整行，包括 *\n* 字符，如果指定了一个非负数的参数，则返回指定大小的字节数，包括 *\n* 字符。

###### 语法

```python
fileObject.readline()
```

###### 参数

- size -- 从文件中读取的字节数

###### 返回值

从字符串中读取的字节。

###### 实例

```python
fo = open("Test.txt", "r+")
print("文件名为: ", fo.name)
line = fo.readline()
print("读取第一行 %s" % (line))
line = fo.readline(3)
print("读取的字符串为: %s" % (line))
fo.close()
```

以上实例输出结果如下：

```powershell
文件名为:  Test.txt
读取第一行 这是第一行
读取的字符串为: 这是第
```

## file.readlines([sizehint])

###### 描述

读取所有行（直到结束符 EOF）并返回列表，若给定 `sizeint>0`，返回总和大约为 `sizeint` 字节的行，实际读取值可能比 `sizhint` 较大，因为需要填充缓冲区。如果碰到结束符 EOF 则返回空字符串。

###### 语法

```python
fileObject.readlines(sizehint)
```

###### 参数

- sizehint -- 从文件中读取的字节数

###### 返回值

包含所有的行的列表。

###### 实例

```python
fo = open("Test.txt", "r+")
print("文件名为: ", fo.name)
line = fo.readlines()
print("读取的数据为: %s" % (line))
line = fo.readlines(2)
print("读取的数据为: %s" % (line))
fo.close()
```

以上实例输出结果如下：

```powershell
文件名为:  Test.txt
读取的数据为: ['这是第一行\n', '这是第二行\n', '这是第三行\n', '这是第四行\n']
读取的数据为: []
```

## file.seek(offset[, whence])

###### 描述

移动文件读取指针到指定位置。

###### 语法

```python
fileObject.seek(offset[, whence])
```

###### 参数

- offset -- 开始的偏移量，也就是代表需要移动偏移的字节数
- whence -- 可选，默认值为0，给offset参数一个定义，表示要从哪个位置开始偏移；0代表从文件开头开始算起，1代表从当前位置开始算起，2代表从文件末尾算起

###### 实例

```python
fo = open("Test.txt", "r+")
print("文件名为: ", fo.name)
line = fo.readline()
print("读取的数据为: %s" % (line))
fo.seek(0, 0)
line = fo.readline()
print("读取的数据为: %s" % (line))
fo.close()
```

以上实例输出结果如下：

```powershell
文件名为:  Test.txt
读取的数据为: 这是第一行

读取的数据为: 这是第一行
```

## file.tell()

###### 描述

返回文件的当前位置，即文件指针当前位置。

###### 语法

```python
fileObject.tell(offset[, whence])
```

###### 返回值

文件的当前位置。

###### 实例

```python
fo = open("Test.txt", "r+")
print("文件名为: ", fo.name)
line = fo.readline()
print("读取的数据为: %s" % (line))
pos = fo.tell()
print("当前位置: %d" % (pos))
fo.close()
```

以上实例输出结果如下：

```powershell
文件名为:  Test.txt
读取的数据为: 这是第一行

当前位置: 6
```

## file.truncate([size])

###### 描述

用于截断文件，如果指定了可选参数 `size`，则表示截断文件为 `size` 个字符，如果没有指定 `size`，则重置到当前位置。

###### 语法

```python
fileObject.truncate([size])
```

###### 参数

- size -- 可选，如果存在则文件截断为size字节

###### 实例

```python
fo = open("Test.txt", "r+")
print("文件名为: ", fo.name)
line = fo.readline()
print("读取行: %s" % (line))
fo.truncate()
line = fo.readlines()
print("读取行: %s" % (line))
fo.close()
```

以上实例输出结果如下：

```powershell
文件名为:  Test.txt
读取行: 这是第一行

读取行: ['这是第二行\n', '这是第三行\n', '这是第四行\n']
```

## file.write(str)

###### 描述

用于向文件中写入指定字符串，但是在文件关闭前或缓冲区刷新前，字符串内容存储在缓冲区中，这时你在文件中是看不到写入的内容的。

###### 语法

```python
fileObject.write([str])
```

###### 参数

- str -- 要写入文件的字符串

###### 实例

```python
fo = open("Test.txt", "r+")
print("文件名为: ", fo.name)
str = "这是第五行"
fo.seek(0, 2)
line = fo.write(str)
fo.seek(0,0)
for index in range(6):
    line = next(fo)
    print("文件行号 %d - %s" % (index, line))
fo.close()
```

以上实例输出结果如下：

```powershell
文件名为:  Test.txt
文件行号 0 - 这是第一行
文件行号 1 - 这是第二行
文件行号 2 - 这是第三行
文件行号 3 - 这是第四行
文件行号 4 - 这是第五行
```

## file.writelines(sequence)

###### 描述

用于向文件中写入一序列的字符串，这一序列字符串可以是由迭代对象产生的，如一个字符串列表，换行需要制定换行符 `\n`。

###### 语法

```python
fileObject.writelines([str])
```

###### 参数

- str -- 要写入文件的字符串序列

###### 实例

```python
fo = open("Test.txt", "w")
print("文件名为: ", fo.name)
seq = ["这是第一行\n", "这是第二行"]
fo.writelines(seq)
fo.close()
```

以上实例输出结果如下：

```powershell
文件名为:  Test.txt
```
