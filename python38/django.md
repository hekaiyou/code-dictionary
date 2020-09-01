# Python3 Django库 {docsify-ignore}

这个第三方库最初被设计用于具有快速开发需求的新闻类站点，目的是要实现简单快捷的网站开发。通过 `pip install Django` 命令下载 [wxPython](https://pypi.org/project/Django/) 库。

## 数据模型

模型在 `models.py` 文件中定义，通过 “对象关系映射器” 实现无需 SQL 语句的数据库模型设计，如下定义了一个 `Person` 模型类，拥有 `first_name` 和 `last_nam` 两个类属性：

```python
from django.db import models

class Person(models.Model):
    first_name = models.CharField(max_length=30)
    last_name = models.CharField(max_length=30)
```

通过对象关系映射器，上面的 `Person` 模型类会转成 SQL 语句，创建一个如下的数据库表：

```sql
CREATE TABLE myapp_person (
    "id" serial NOT NULL PRIMARY KEY,
    "first_name" varchar(30) NOT NULL,
    "last_name" varchar(30) NOT NULL
);
```
