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