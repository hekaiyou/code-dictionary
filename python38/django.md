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

### 使用数据

需要使用模型时，需要修改 `settings.py` 文件中的 `INSTALLED_APPS` 配置，该配置中添加包含 `models.py` 文件的模块名称。例如，若模型位于项目中的 `myapp.models` 模块，`INSTALLED_APPS` 应设置如下：

```python
INSTALLED_APPS = [
    #...
    'myapp',
    #...
]
```

当向 `INSTALLED_APPS` 添加新的应用或变更模型时，需要使用 `manage.py migrate` 与 `manage.py makemigrations` 命令。

#### makemigrations

该命令会在该项目的所有应用下建立 `migrations` 目录，并记录下所有的关于 `modes.py` 的改动（对数据库的改动），比如 `0001_initial.py` 文件。

```powershell
python manage.py makemigrations
```

#### migrate

该命令用于将改动内容作用到数据库文件，将数据库状态与当前的模型和迁移集同步。简单说就是将对数据库的更改，主要是数据表设计的更改，在数据库中真实执行。

```powershell
python manage.py migrate
```

### 字段

数据模型中最重要的是数据库的字段定义，字段在模型类属性中定义，定义字段名时应小心避免使用与模型API冲突的名称，如 `clean`、`save`、`delete` 等。

#### 字段类型

模型中每一个字段都应该是某个 `Field` 类的实例，Django 内置了数十种字段类型：

##### AutoField

默认情况下，Django 会给每一个模型添加下面的字段，这是一个自增的主键，一般用于 `id` 字段。

```python
id = models.AutoField(primary_key=True)
```

##### BigAutoField

自增列，一个64位的整数，非常类似于 `AutoField`，不同之处在于它保证可以容纳 1 到 9223372036854775807 之间的数字。当数据过多时可用 `BigAutoField` 代替 `AutoField` 类。

```python
id = models.BigAutoField(primary_key=True)
```

##### BigIntegerField

长整形，一个64位整数，非常类似于 `IntegerField`，不同之处在于它保证可以容纳从 -9223372036854775808 到 9223372036854775807 的数字，此字段的默认表单控件是 `NumberInput`。

```python
name = models.BigIntegerField()
```

##### BinaryField

二进制数据的字段，可以为其分配 `bytes`、`bytearray` 或 `memoryview`，高级用户使用的类型。

```python
name = models.BigIntegerField()
```

##### BooleanField

布尔类型，此字段的默认表单控件为 `CheckboxInput`，如果 `null=True`，则为 `NullBooleanSelect`。未定义 `Field.default` 时，`BooleanField` 的默认值为 `None`。

```python
name = models.BooleanField(default=True)
```

##### CharField

字符串类型，单行输入，用于较短的字符串，对于大量文本，请使用 `TextField`，此字段的默认表单控件是 `TextInput`。`CharField` 有一个额外的必需参数 `CharField.max_length`，设置字段的最大长度（以字符为单位）。

```python
name = models.CharField(max_length=250)
```

##### DateField

日期类型 `YYYY-MM-DD`，在 Python 中由 `datetime.date` 实例表示，有一些额外的可选参数：

- DateField.auto_now : 每次保存对象时都自动更新日期，通常用于 last_modified 字段。仅在调用 Model.save() 时自动更新，以其他方式，例如 QuerySet.update()，对字段进行更新时，该字段不会更新
- DateField.auto_now_add : 第一次创建时添加，之后的更新不再改变，通常用于创建时间戳

此字段的默认控件是 `DateInput`，管理后台添加了 “JavaScript日历” 和 “今天按钮”，包括一个附加的 `invalid_date` 错误消息密钥。参数 `auto_now_add`、`auto_now` 和 `default` 是互斥的，这些参数的任何组合都将导致错误。

```python
name_1 = models.DateField(auto_now=True)
name_2 = models.DateField(auto_now_add=True)
```

##### DateTimeField

日期和时间类型 `YYYY-MM-DD hh:mm:ss`，在 Python 中由 `datetime.datetime` 实例表示，采用与 `DateField` 相同的额外参数，该字段的默认表单控件是单个 `DateTimeInput`，管理后台有两个单独的 `TextInput` 控件。

```python
name_1 = models.DateTimeField(auto_now=True)
name_2 = models.DateTimeField(auto_now_add=True)
```

##### DecimalField

固定精度的十进制数，在 Python 中由 `Decimal` 实例表示，使用 `DecimalValidator` 验证输入，有两个必需的参数：

- DecimalField.max_digits : 数字中允许的最大位数，此数字必须大于或等于小数位数
- DecimalField.decimal_places : 小数位的最大位数

```python
# 最大数字 999 且保留 2 位小数
name_1 = models.DecimalField(max_digits=5, decimal_places=2)
# 最大数字 10亿 且保留 10 位小数
name_2 = models.DecimalField(max_digits=19, decimal_places=10)
```

当 `localize` 为 `False` 时，此字段的默认控件为 `NumberInput`，否则为 `TextInput`。

##### DurationField

时间段（两个时间的差值）类型，使用 `timedelta` 在 Python 中建模，在 PostgreSQL 上使用的数据类型是 `interval`，在 Oracle 上使用的数据类型是 `INTERVAL DAY(9) TO SECOND(6)`，否则将使用微秒级的 `bigint` 类型。

```python
name_1 = models.DurationField(default=timedelta())
```

需要注意，在除 PostgreSQL 以外的所有数据库上，直接使用 `DurationField` 的值进行算术运算时，结果不准确。

##### EmailField

特殊的 `CharField` 类型，使用 `EmailValidator` 检查该值是否为有效的电子邮箱地址。

```python
name_1 = models.EmailField(max_length=250)
```

##### FileField

文件上传字段。需要注意，`FileField` 不支持 `primary_key` 参数，如果使用该参数，则会引发错误。

###### FileField.upload_to

此属性可以设置上传目录和文件名，有两种方法进行设置。在这两种情况下，该值都将传递到 `Storage.save()` 方法。

如果指定字符串值或 `Path`，则它可能包含 `strftime()` 格式，该格式将替换为文件上传的日期/时间，以使上传的文件不会填满给定目录，例如：

```python
class MyModel(models.Model):
    # 文件将被上传到 MEDIA_ROOT/uploads_1
    upload_1 = models.FileField(upload_to='uploads_1/')
    # 文件将保存到 MEDIA_ROOT/uploads_2/2020/09/02
    upload_2 = models.FileField(upload_to='uploads_2/%Y/%m/%d/')
```

如果使用默认的 `FileSystemStorage`，则字符串值将附加到 `MEDIA_ROOT` 路径中，作为存储上传文件的目录。

属性 `upload_to` 也是可调用的，通过调用可获得上传路径、文件名，可调用对象必须接受两个参数，并返回 Unix 样式的路径，传递给存储系统。这两个参数是：

- instance : 定义 FileField 的模型实例，更准确地说，这是一个包含当前文件的特殊实例。通常，这个对象还没有在数据库中保存，若该对象用的是默认的 AutoField 字段，那它的 primary key 字段还可能没有值
- filename : 最初提供给文件的文件名，确定最终目标路径时，可以用也可以不用

```python
def user_directory_path(instance, filename):
    # 文件将被上传到 MEDIA_ROOT/user_<id>/<filename>
    return 'user_{0}/{1}'.format(instance.user.id, filename)

class MyModel(models.Model):
    upload = models.FileField(upload_to=user_directory_path)
```

###### FileField.storage

存储对象或返回存储对象的可调用对象，可以处理文件的存储和检索。使用前需新建 `storage.py` 文件：

```python
from django.core.files.storage import FileSystemStorage

class TestStorage(FileSystemStorage):
    from django.conf import settings
    # 初始化
    def __init__(self, location=settings.MEDIA_ROOT, base_url=settings.MEDIA_URL):
        super(TestStorage, self).__init__(location, base_url)
    # 重写 _save 方法
    def _save(self, name, content):
        # name 为上传文件名称
        import os, time, random
        # 文件扩展名
        ext = os.path.splitext(name)[1]
        # 文件目录
        d = os.path.dirname(name)
        # 定义/重写/合成文件名
        name = '自定义文件名'
        # 调用父类方法
        return super(TestStorage, self)._save(name, content)
```

然后在 `models.py` 文件中进行调用：

```python
name_1 = models.FileField(storage=TestStorage())
```
