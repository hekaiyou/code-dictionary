# Python3 Django库 {docsify-ignore}

这个第三方库最初被设计用于具有快速开发需求的新闻类站点，目的是要实现简单快捷的网站开发。通过 `pip install Django` 命令下载 [wxPython](https://pypi.org/project/Django/) 库。

## 常用命令

查看 Django 是否安装，且安装的是哪个版本：

```powershell
python -m django --version
```

创建 Django 项目，创建时要避免使用 Python 或 Django 的内部保留字来命名你的项目。具体地说，要得避免使用像 django（会和 Django 自己产生冲突）或 test（会和 Python 的内置组件产生冲突）这样的名字。命令如下：

```powershell
django-admin startproject [项目名称]
```

启动 Django 自带的用于开发的简易服务器，它是一个用纯 Python 写的轻量级的 Web 服务器。要注意的是，**千万不要**将这个服务器用于和生产环境相关的任何地方，因为这个服务器只是为了开发而设计的。命令如下：

```powershell
python manage.py runserver
python manage.py runserver 8080
python manage.py runserver 0:8000
python manage.py runserver 0.0.0.0:8000
```

创建 Django 应用，项目和应用有什么区别？应用是一个专门做某件事的网络应用程序，项目则是一个网站使用的配置和应用的集合，项目可以包含很多个应用，应用可以被很多个项目使用。命令如下：

```powershell
python manage.py startapp [应用名称]
```

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

文件上传字段，此字段的默认表单控件是 `ClearableFileInput`。需要注意，`FileField` 不支持 `primary_key` 参数，如果使用该参数，则会引发错误。

在模型中使用 `FileField` 或 `ImageField` 需要执行几个步骤：

1. 在 `setting` 文件中，需要定义：`setting: MEDIA_ROOT` 作为 Django 存储上传文件目录的完整路径。（为了提高性能，这些文件不会储存在数据库中）定义：`setting: MEDIA_URL` 作为该目录的基本公共 URL，确保该目录能够被 Web 服务器的用户写入
2. 将 `FileField` 或 `ImageField` 添加到模型中，定义 `upload_to` 参数，以指定 `MEDIA_ROOT` 的子目录以用于上传的文件
3. 存储在数据库中的所有文件路径都是相对于 `MEDIA_ROOT` 目录的，Django 提供了便捷 `url` 属性。例如，如果 `ImageField` 名为 `mug_shot`，则可以使用 `{{ object.mug_shot.url }}` 在模板中获取图像的绝对路径。

例如 `MEDIA_ROOT` 设置为 `/home/media`，而 `upload_to` 设置为 `photos/%Y/%m/%d`。`upload_to` 的 `%Y/%m/%d` 部分为 `strftime()` 格式；`%Y` 是四位数的年份，`%m` 是两位数的月份，`%d` 是两位数的日期。如果在2020年9月2日上传文件，该文件将保存在目录 `/home/media/photos/2020/09/02` 中。

如果要检索上传的文件在磁盘上的文件名或文件的大小，可以分别使用 `name` 和 `size` 属性。可以使用 `url` 属性获取上传文件的相对URL。

请注意，每当处理上传的文件时，都应密切注意上传文件的位置以及文件的类型，以免出现安全漏洞。验证所有上传的文件，以确保文件符合条件。例如，如果盲目地让某人未经验证将文件上传到 Web 服务器的文档目录，那么某人可以上传 CGI 或 PHP 脚本并通过访问站点上的 URL 来执行该脚本。还要注意，即使上传的 HTML 文件也可以由浏览器执行（尽管不能由服务器执行），但它也会构成等同于 XSS 或 CSRF 攻击的安全威胁。

`FileField` 实例在数据库中创建为 `varchar` 列，默认最大长度为 100 个字符。与其他字段一样，可以使用 `max_length` 参数更改最大长度。

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

##### FilePathField

特殊的 `CharField` 类型，其内容仅限于文件系统上某个目录中的文件名。有一些特殊的参数，其中第一个是必需的。例如：大多数网站在插入图片时，先上传大尺寸图时，再自动生成一张缩略图，然后网页中插入缩略图，并把地址指向大尺寸的图。

```python
img = models.ImageField(upload_to='screenshots')
thumb = models.FilePathField(path='screenshots/thumb')
```

###### FilePathField.path

必需的，目录的绝对文件系统路径，应从中获取此 `FilePathField` 的选择，例如：`/home/images`。`path` 也可以是可调用的，例如在运行时动态设置路径的函数：

```python
import os
from django.db import models
from django.conf import settings

def images_path():
    return os.path.join(settings.LOCAL_FILE_DIR, 'images')

class MyModel(models.Model):
    file = models.FilePathField(path=images_path)
```

###### FilePathField.match

可选的，`FilePathField` 将用于过滤文件名的正则表达式（字符串）。请注意，正则表达式仅应用于基本文件名，而不是完整路径。例如：`foo.*\.txt$`，它将与名为 `foo23.txt` 的文件匹配，但与 `bar.txt` 或 `foo23.png` 的文件不匹配。

###### FilePathField.recursive

可选的，`True` 或 `False`，默认值为 `False`，指定是否应包含所有子目录的路径。

###### FilePathField.allow_files

可选的，`True` 或 `False`，默认值为 `True`，指定是否应包含指定位置的文件，这个或 `allow_folders` 必须有一个为 `True`。

###### FilePathField.allow_folders

可选的，`True` 或 `False`，默认值为 `False`，指定是否应包含指定位置的文件夹。 这个或 `allow_files` 必须有一个为 `True`。

一个潜在的难题是，`match` 适用于基本文件名，而不是完整路径。因此，此示例：

```python
FilePathField(path="/home/images", match="foo.*", recursive=True)
```

将匹配 `/home/images/foo.png` 但不匹配 `/home/images/foo/bar.png`，因为 `match` 项适用于基本文件名（`foo.png` 和 `bar.png`）。`FilePathField` 实例在数据库中创建为 `varchar` 列，默认最大长度为 100 个字符，与其他字段一样，可以使用 `max_length` 参数更改最大长度。

##### FloatField

浮点数，在 Python 中由 `float` 实例表示，当 `localize` 为 `False` 时，此字段的默认表单控件为 `NumberInput`，否则为 `TextInput`。

```python
name = models.FloatField(default=0.0)
```

`FloatField` 类有时与 `DecimalField` 类混合在一起，尽管它们都代表实数，但它们代表的数字却有所不同。`FloatField` 内部使用 Python 的 `float` 类型，而 `DecimalField` 使用 Python 的 `Decimal` 类型。

##### ImageField

特殊的 `FileField` 类型，从 `FileField` 继承所有属性和方法，同时会验证上传的对象是否为有效的图像文件。需要注意，它依赖 `Pillow` 第三方库。

```python
name = models.ImageField(upload_to='images/%Y/%m')
```

除了可用于 `FileField` 的特殊属性外，`ImageField` 还有 `height` 和 `width` 属性。为了方便查询这些属性，`ImageField` 有两个额外的可选参数：

- ImageField.height_field : 每次保存模型实例时，都会更新图像的高度
- ImageField.width_field : 每次保存模型实例时，都会更新图像的宽度

`ImageField` 实例在数据库中创建为 `varchar` 列，默认最大长度为 100 个字符。与其他字段一样，您可以使用 `max_length`参数更改最大长度。此字段的默认表单控件是 `ClearableFileInput`。

##### IntegerField

整数，在 Django 支持的所有数据库中，-2147483648 到 2147483647 之间的值都是安全的。它使用 `MinValueValidator` 和 `MaxValueValidator` 根据默认数据库支持的值来验证输入。

```python
name = models.IntegerField(default=0)
```

当 `localize` 为 `False` 时，此字段的默认表单控件为 `NumberInput`，否则为 `TextInput`。

##### GenericIPAddressField

字符串格式的 IPv4 或 IPv6 地址（例如 `192.0.2.30` 或 `2a02:42fe::4`），此字段的默认表单控件是 `TextInput`。

- GenericIPAddressField.protocol : 将有效输入限制为指定的协议，接受的值为 both（默认）、IPv4 或 IPv6，匹配不区分大小写
- GenericIPAddressField.unpack_ipv4 : 解压缩 IPv4 映射的地址，如 ::ffff:192.0.2.1，如果启用此选项，则该地址将解压缩为 192.0.2.1，默认设置为禁用，只能在 protocol 设置为 both 时使用

```python
name = models.GenericIPAddressField(protocol='IPv4')
```

IPv6 地址规范化遵循 `RFC 4291#section-2.2` 第2.2节，包括使用该节第 3 段中建议的 IPv4 格式，例如 `::ffff:192.0.2.0`，例如，将 `2001:0::0:01` 标准化为 `2001::1`，并将 `::ffff:0a0a:0a0a` 标准化为 `::ffff:10.10.10.10`。同时，所有字符都将转换为小写。

##### JSONField

用于存储 JSON 编码数据的字段，在 Python 中，数据以其 Python 本机格式表示：字典、列表、字符串、数字、布尔值和 None。（数据库要求：MariaDB 10.2.7+、MySQL 5.7.8+、Oracle、PostgreSQL、SQLite 3.9.0+）

```python
name = models.JSONField(default={})
```

如果为该字段提供 `default` 值，请确保它是一个不变的对象（例如字符串），或者是每次都返回一个新的可变对象（例如字典或函数）的可调用对象。提供可变的默认对象（例如 `default={}` 或 `default=[]`）在所有模型实例之间共享一个对象。

###### JSONField.encoder

可选的 `json.JSONEncoder` 子类，用于序列化标准 JSON 序列化程序不支持的数据类型（例如 `datetime.datetime` 或 `UUID`），具体可以使用 `DjangoJSONEncoder` 类。（默认为 `json.JSONEncoder`）

###### JSONField.decoder

可选的 `json.JSONDecoder` 子类，用于反序列化从数据库检索的值，该值将采用自定义编码器选择的格式（通常是字符串）。（默认为 `json.JSONDecoder`）

反序列化时需要考虑不确定输入类型的情况，例如，冒着返回一个日期时间的风险，该日期时间实际上是一个字符串，恰好与为日期时间选择的格式相同。

##### PositiveIntegerField

正整数字段，类似于 `IntegerField`，但必须为正数或零（0）。在 Django 支持的所有数据库中，0 到 2147483647 之间的值都是安全的，出于向后兼容的原因，可接受值为 0。

```python
name = models.PositiveIntegerField(default=1)
```

##### PositiveBigIntegerField

较大的正整数字段，类似于 `PositiveIntegerField`，但仅允许在特定点（与数据库有关）下的值。在 Django 支持的所有数据库中，0 到 9223372036854775807 的值都是安全的。

```python
name = models.PositiveBigIntegerField()
```

##### PositiveSmallIntegerField

较小的正整数字段，似于 `PositiveIntegerField`，但仅允许在特定点（与数据库有关）下的值。在 Django 支持的所有数据库中，0 到 32767 的值都是安全的。

```python
name = models.PositiveSmallIntegerField()
```

##### SlugField

`Slug` 是一个语义，是某个事物的简短标签，仅包含字母、数字、下划线或连字符。它们通常在 URL 中使用，例如有一个关于文章的模型，有两个字段，分别是 `title`（标题） 和 `slug`（短网址）：

```python
class Article(models.Model):
    title = models.CharField(max_length=100)
    slug = models.SlugField(max_length=40)
```

这时候存入模型的一条信息，`title="The song of ice and fire"`，如果想用文章的标题作为 URL 进行访问，完整的标题可能是：`www.xxx.com/article/The song of ice and fire`，但是 URL 是不能出现空格的，因此空格会被转变成 `%20`，最后网址得到 `www.xxx.com/article/The%20song%20of%20ice%20and%20fire`，我们不希望出现这么多难看的 `%20`，而是希望用短横线 `-` 替代空格，得到 `www.xxx.com/article/the-song-of-ice-and-fire`。

而 Django 的 `django.utils.text` 提供了一个 `slugify` 方法叫，可以把刚才的文章标题 `The song of ice and fire` 做两个转变：

1. 全部转化成小写字母
2. 空格部分替换成短横线 -

因为这种转变主要用于做 URL 拼接，所以我们把这种结果都统一放在 `SlugField` 字段里面，用以构建语义化的 URL 网址。

##### SmallAutoField

较小的自增 `id`，与 `AutoField` 相似，但仅允许值处于一定限制（与数据库有关）之下。从 1 到 32767 的值在 Django 支持的所有数据库中都是安全的。

```python
id = models.SmallAutoField(primary_key=True)
```

##### SmallIntegerField

较小的整数，类似于 `IntegerField`，但仅允许在特定点（与数据库有关）下的值。在 Django 支持的所有数据库中，从 -32768 到 32767 的值都是安全的。

```python
name = models.SmallIntegerField(default=0)
```

##### TextField

大文本字段，此字段的默认表单控件是 `Textarea`，不建议使用 `max_length` 属性，如果有需要可以使用 `CharField` 类型。

```python
name = models.TextField()
```

##### TimeField

时间字段，在 Python 中用 `datetime.time` 实例表示，接受与 `DateField` 相同的参数。此字段的默认表单控件为 `TimeInput`。

```python
name_1 = models.TimeField(auto_now=True)
```

##### URLField

特殊的 `CharField` 类型，用于存储 URL，由 `URLValidator` 验证。此字段的默认表单控件是 `URLInput`，像所有 `CharField` 子类一样，`URLField` 采用可选的 `max_length` 参数。如果未指定 `max_length`，则使用默认值 200。

```python
name = models.URLField()
```

##### UUIDField

UUID 类型，用于存储通用唯一标识符的字段，使用 Python 的 `UUID` 类。在 PostgreSQL 上使用时，它存储在 `uuid` 数据类型中，否则存储在 `char(32)` 中。通用唯一标识符是 `AutoField` 的优秀替代品，数据库不会为您生成 UUID，因此建议使用 `default` 参数。

```python
import uuid
from django.db import models

class MyUUIDModel(models.Model):
    id = models.UUIDField(primary_key=True, default=uuid.uuid4, editable=False)
```

##### ForeignKey

关联关系字段，多对一的关系。需要两个位置参数：被关联的类 和 `on_delete` 选项。

```python
name = models.ForeignKey('myapp.Manufacturer', on_delete=models.CASCADE)
```

如果要创建一个递归关系（一个与其自身有多对一关系的对象）则使用：

```python
models.ForeignKey('self', on_delete=models.CASCADE)
```

如果需要在尚未定义的模型上创建关系，则可以使用模型的名称，而不是模型对象本身：

```python
from django.db import models

class Car(models.Model):
    manufacturer = models.ForeignKey(
        'Manufacturer',
        on_delete=models.CASCADE,
    )

class Manufacturer(models.Model):
    pass
```

要引用在另一个应用中定义的模型，可以显式指定带有完整应用标签的模型。例如，如果 `Manufacturer` 模型是在另一个称为 `production` 的应用程序中定义的，则需要使用：

```python
class Car(models.Model):
    manufacturer = models.ForeignKey(
        'production.Manufacturer',
        on_delete=models.CASCADE,
    )
```

在解决两个应用之间的循环导入依赖关系时，这种称为惰性关系的引用可能会很有用。数据库索引是在 `ForeignKey` 上自动创建的。可以通过将 `db_index` 设置为 `False` 来禁用它。如果要创建外键以保持一致性而不是联接，或者要创建替代索引（例如部分或多列索引），则可能要避免索引的开销。

在幕后，Django 在字段名称后附加 `_id` 以创建其数据库列名称。除非编写自定义 SQL，否则您的代码永远不必处理数据库列名，您只要处理模型对象的字段名称。

#### 字段选项

## 实例

### 配置JWT认证

先通过 `pip install djangorestframework` 命令下载 [Django REST framework](https://pypi.org/project/djangorestframework/) 库，再通过 `pip install djangorestframework-simplejwt` 命令下载 [Django REST framework Simple JWT](https://pypi.org/project/djangorestframework-simplejwt/) 库。它们提供了 JWT 的 Django 应用。

#### 配置与编码

在 `settings.py` 文件里加入以下内容，以支持 JWT 认证：

```python
REST_FRAMEWORK = {
    'DEFAULT_AUTHENTICATION_CLASSES': [
        'rest_framework_simplejwt.authentication.JWTAuthentication'
    ],
}
```

在某个应用的 `views.py` 文件下，写一个测试用的视图。

```python
from rest_framework.views import APIView
from rest_framework import permissions
from rest_framework.response import Response
from rest_framework_simplejwt import authentication

class AutoTestView(APIView):
    permission_classes = [permissions.IsAuthenticated]
    authentication_classes = (authentication.JWTAuthentication,)

    def get(self, request, *args, **kwargs):
        print('authenticate: ', request.successful_authenticator.authenticate(request))
        print('authenticate_header: ', request.successful_authenticator.authenticate_header(request))
        print('get_header: ', request.successful_authenticator.get_header(request))
        print('get_raw_token: ', request.successful_authenticator.get_raw_token(request.successful_authenticator.get_header(request)))
        print('get_validated_token: ', request.successful_authenticator.get_validated_token(request.successful_authenticator.get_raw_token(request.successful_authenticator.get_header(request))))
        print('get_user: ', request.successful_authenticator.get_user(request.successful_authenticator.get_validated_token(request.successful_authenticator.get_raw_token(request.successful_authenticator.get_header(request)))))
        print('www_authenticate_realm: ', request.successful_authenticator.www_authenticate_realm)
        return Response('O get K')

    def post(self, request, *args, **kwargs):
        return Response('O post K')
```

在 `urls.py` 文件下导入 JWT 的两个视图，以及我们的测试视图的路由：

```python
...
from rest_framework_simplejwt.views import (TokenObtainPairView, TokenRefreshView)
from django.conf.urls import url
from foundation import views as foundation_views

urlpatterns = [
    ...
    url(r'^firmware/auth/token/obtain/$', TokenObtainPairView.as_view(), name='obtain_token'),
    url(r'^firmware/auth/token/refresh/$', TokenRefreshView.as_view(), name='refresh_token'),
    url(r'^firmware/auth/token/test/$', foundation_views.AutoTestView.as_view(), name='test_token'),
]
```

#### 使用示例

获取 Token：

![django_djangorestframeworksimplejwt_1](image/django_djangorestframeworksimplejwt_1.png)

通过 Token 获取视图信息：

![django_djangorestframeworksimplejwt_3](image/django_djangorestframeworksimplejwt_3.png)

通过 `refresh` 刷新 Token：

![django_djangorestframeworksimplejwt_2](image/django_djangorestframeworksimplejwt_2.png)
