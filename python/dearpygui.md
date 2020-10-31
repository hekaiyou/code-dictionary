# Python3 DearPyGui库 {docsify-ignore}

这个第三方库用于开发跨平台的 GUI 应用程序，于2020年9月发布，通过对 [Dear ImGui](https://www.worldlink.com.cn/en/osdir/imgui.html) 的包装，使它与众不同（相比其他的 Python GUI 框架）。**DearPyGui** 在后台使用 C++ 的 Bloat-free 立即模式图形用户界面，能够实现灵活的动态界面。而且，**DearPyGui** 不使用系统平台的窗口控件，而是使用计算机的显卡来绘制窗口控件，因此能支持所有系统平台。

先确保你的 Python 版本在 *3.7* 以上，再通过 `pip install dearpygui` 命令下载 [DearPyGui](https://pypi.org/project/dearpygui/) 库。

## 基础

### 第一份代码

![dearpygui_hellodearpygui](image/dearpygui/dearpygui_hellodearpygui.png)

```python
from dearpygui.core import *
from dearpygui.simple import *

def save_callback(sender, data):
    print("保存点击")

with window("Example Window"):
    add_text("Hello, Dear PyGui")
    add_button("Save", callback=save_callback)
    add_input_text("string", default_value="Quick brown fox")
    add_slider_float("float", default_value=0.283, max_value=1)

start_dearpygui()
```

### 窗口结构

相比于其他 Python GUI 框架，使用 **DearPyGui** 非常简单，比如通过 `show_documentation()` 方法可以查看文档，不过要注意，**DearPyGui** 项目的代码最终必须以 `start_dearpygui()` 方法结束。

```python
from dearpygui.core import *
from dearpygui.simple import *

show_documentation()

start_dearpygui()
```

![dearpygui_showdocumentation](image/dearpygui/dearpygui_showdocumentation.png)

一个 **DearPyGui** 应用程序由 *可视区域（viewport）*、*窗口（windows）* 和 *控件（widgets）* 组成，*可视区域（viewport）* 是应用程序的主窗口，通过调用 `start_dearpygui()` 方法创建。下面通过 `show_about()` 方法打开 “关于” 窗口，以演示 *可视区域（viewport）* 与 *窗口（windows）* 之间的关系。

```python
from dearpygui.core import *
from dearpygui.simple import *

show_documentation()
show_about()

start_dearpygui()
```

![dearpygui_showabout](image/dearpygui/dearpygui_showabout.png)

Dear PyGui 由 `dearpygui.core` 和 `dearpygui.simple` 两个包组成。`dearpygui.core` 包含 **DearPyGui** 的核心功能，其他所有的功能都建立在它之上；`dearpygui.simple` 包含一些简单的封装和基于 `dearpygui.core` 创建的实用功能，提供了更为简单、友好的调用方式。

### 开发者工具

Dear PyGui 包含常用的开发人员工具，下面会打开 **Debug** 窗口、**Logger** 窗口和 **Metrics** 窗口。

```python
from dearpygui.core import *
from dearpygui.simple import *

show_debug()
show_metrics()
show_logger()

start_dearpygui()
```

![dearpygui_showdebug](image/dearpygui/dearpygui_showdebug.png)

### 内置日志记录

日志记录 **Logger** 是内置开发者工具之一，可以通过命令 `show_logger()`方法访问，**Logger** 有 *6* 个日志级别：

- Trace —— 低级的日志
- Debug —— 开发过程中的细粒度日志
- Info —— 感兴趣或重要的粗粒度日志
- Warning —— 潜在错误或提示信息
- Error —— 错误和异常信息
- Off —— 关闭所有日志记录

可以结合下面的栗子来理解 *6* 个日志级别的区别。

```python
from dearpygui.core import *

show_logger()
set_log_level(mvTRACE)
log("Trace Message")
log_debug("Debug Message")
log_info("Info Message")
log_warning("Warning Message")
log_error("Error Message")

start_dearpygui()
```

![dearpygui_showlogger](image/dearpygui/dearpygui_showlogger.png)

## 控件与窗口

通常，控件在添加时都需要使用对应的 `add_***` 方法，同时也必须有一个唯一的 `name`，默认情况下，`name` 会被当成 `label` 使用（视具体控件而定），因此，如果我们要改变 `label`，可以通过下面两种方式：

- 使用 `##` 进行字符拼接，左边的字符串为要显示的名称，右边则为隐藏名称
- 通过设置 `label` 参数的值，显式设置要显示的名称

还有一些控件（下面以 `same_line` 为栗）是自动生成 `name` 的，在这些控件方法中，`name` 是可选参数，如果我们需要在以后引用这个控件，就可以填写这个 `name` 参数。

```python
from dearpygui.core import *
from dearpygui.simple import *

with window("Tutorial"):
    add_button("Apply")
    add_same_line(spacing=10)
    add_button("Apply##1")
    add_same_line(spacing=10, name="sameline1")
    add_button("Apply2", label="Apply")
    add_spacing(count=5, name="spacing1")
    add_button("Apply##3")

start_dearpygui()
```

![dearpygui_namelabel](image/dearpygui/dearpygui_namelabel.png)

Dear PyGui 的容器即 *窗口（windows）* 用于保存控件，创建方法如下：

- 由 `add_window()` 方法启动窗口并在结束调 `end()` 方法
- 使用 `dearpygui.simple` 包和相应的窗口管理器（推荐）

包 `dearpygui.simple` 中相应的窗口上下文管理器将自动调用 `end()` 方法，这样代码就可以折叠起来，便于管理代码的层次结构。

```python
from dearpygui.core import *

add_window("Tutorial")
add_text("This is some text on window 1")
end()

from dearpygui.simple import *

with window("Tutorial##2"):
    add_text("This is some text on window 2")

start_dearpygui()
```

![dearpygui_addwindow](image/dearpygui/dearpygui_addwindow.png)
