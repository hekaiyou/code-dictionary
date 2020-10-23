# Python3 系统 {docsify-ignore}

## os.getcwd()

###### 描述

返回当前工作目录。

###### 语法

```python
os.getcwd()
```

###### 返回值

当前进程的工作目录。

###### 实例

```python
import os
print("当前工作目录 : %s" % os.getcwd())
```

以上实例输出结果如下：

```powershell
当前工作目录 : C:\Users\hexiaoyou
```

## os.remove(path)

###### 描述

用于删除指定路径的文件如，果指定的路径是一个目录，将抛出 `OSError`。

###### 语法

```python
os.remove(path)
```

###### 参数

- path -- 要移除的文件路径

###### 实例

```python
import os, sys

print("目录为: %s" %os.listdir(os.getcwd()))
os.remove("Test.txt")
print("移除后: %s" %os.listdir(os.getcwd()))
```

以上实例输出结果如下：

```powershell
目录为: ['AirtestIDE.lnk', 'desktop.ini', 'PDMan.lnk', 'Postman.lnk', 'Test.txt']
移除后: ['AirtestIDE.lnk', 'desktop.ini', 'PDMan.lnk', 'Postman.lnk']
```

## os.rename(src, dst)

###### 描述

用于命名文件或目录，从 `src` 到 `dst`,如果 `dst` 是一个存在的目录，将抛出 `OSError`。

###### 语法

```python
os.rename(src, dst)
```

###### 参数

- src -- 要修改的目录名
- dst -- 修改后的目录名

###### 实例

```python
import os, sys

print("目录为: %s"%os.listdir(os.getcwd()))
os.rename("Test","Test2")
print("重命名后: %s" %os.listdir(os.getcwd()))
```

以上实例输出结果如下：

```powershell
目录为: ['AirtestIDE.lnk', 'desktop.ini', 'PDMan.lnk', 'Postman.lnk', 'Test']
重命名后: ['AirtestIDE.lnk', 'desktop.ini', 'PDMan.lnk', 'Postman.lnk', 'Test2']
```
