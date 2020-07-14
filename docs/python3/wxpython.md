# Python3 wxPython库 {docsify-ignore}

这个第三方库用于开发跨平台的 GUI 应用程序，可以轻松地创建健壮、功能强大的 GUI 程序。通过 `pip install wxPython` 命令下载 [wxPython](https://pypi.org/project/wxPython/) 库。

## Hello World

下面是业余版本的 **Hello World**：

```python
# 导入wxPython库
import wx

# 创建一个应用程序对象
app = wx.App()
# 创建一个框架
frm = wx.Frame(None, title="Hello World")
# 展示框架
frm.Show()
# 启动事件循环
app.MainLoop()
```

下面是专业版本的 **Hello World Pro**：

```python
import wx

class HelloWorldPro(wx.Frame):
    """
    Hello World Pro
    """

    def __init__(self, *args, **kw):
        # 确保父类的 __init__ 被调用
        super(HelloWorldPro, self).__init__(*args, **kw)
        # 在框架中创建一个面板
        pnl = wx.Panel(self)
        # 在上面放一个大号的静态文本
        st = wx.StaticText(pnl, label="Hello World Pro!")
        font = st.GetFont()
        font.PointSize += 10
        font = font.Bold()
        st.SetFont(font)
        # 创建一个大小调整器来管理子控件的布局
        sizer = wx.BoxSizer(wx.VERTICAL)
        sizer.Add(st, wx.SizerFlags().Border(wx.TOP | wx.LEFT, 25))
        pnl.SetSizer(sizer)
        # 创建菜单栏
        self.make_menu_bar()
        # 创建状态栏
        self.CreateStatusBar()
        self.SetStatusText("状态栏")

    def make_menu_bar(self):
        """
        菜单栏由菜单组成，菜单由菜单项组成。此方法将构建一组菜单，并绑定选择菜单项时要调用的处理函数。
        """

        # 使用 "Hello" 和 "退出" 项目创建 "文件" 菜单
        file_menu = wx.Menu()
        # 语法 "\t..." 定义了一个快捷键
        hello_item = file_menu.Append(-1, "&Hello...\tCtrl-H", "此菜单项在状态栏中显示的帮助信息")
        file_menu.AppendSeparator()
        # 使用 Stock ID 时，无需指定菜单项的标签
        # https://docs.wxpython.org/stock_items.html
        exit_item = file_menu.Append(wx.ID_EXIT)
        # 只有一个 "关于" 项目的 "帮助" 菜单
        help_menu = wx.Menu()
        about_item = help_menu.Append(wx.ID_ABOUT)
        # 制作菜单栏，然后向其中添加两个菜单
        menu_bar = wx.MenuBar()
        menu_bar.Append(file_menu, "&文件")
        menu_bar.Append(help_menu, "&帮助")
        # 将菜单栏移至框架
        self.SetMenuBar(menu_bar)
        # 将每个菜单项的处理函数与 EVT_MENU 事件关联
        self.Bind(wx.EVT_MENU, self.on_hello, hello_item)
        self.Bind(wx.EVT_MENU, self.on_exit, exit_item)
        self.Bind(wx.EVT_MENU, self.on_about, about_item)

    def on_exit(self, event):
        """关闭框架，终止应用程序。"""
        self.Close(True)

    def on_hello(self, event):
        """显示Hello对话框。"""
        wx.MessageBox("Hello World Pro!")

    def on_about(self, event):
        """显示关于对话框"""
        wx.MessageBox("这是一个wxPython的演示Demo", "关于Hello World Pro", wx.OK | wx.ICON_INFORMATION)

if __name__ == '__main__':
    # 创建应用和框架
    app = wx.App()
    frm = HelloWorldPro(None, title='Hello World Pro')
    # 显示框架并启动事件循环
    frm.Show()
    app.MainLoop()
```

## 常用对话框

常用对话框类和函数封装了常用对话框的需求，它们都是 `模态` 的，抓住了控制流，直到用户关闭对话框。

#### MessageDialog

该对话框显示单行或多行消息，并带有 `OK`、`Cancel`、`Yes` 和 `No` 按钮的选择。在 *Windows* 下，可以显示可选图标，例如感叹号或问号。

###### Demo 0

```python
dlg = wx.MessageDialog(None, '消息对话框内容', '标题信息', wx.OK)
dlg.ShowModal()
dlg.Destroy()
```

###### Demo 1

```python
dlg = wx.MessageDialog(None, '消息对话框内容', '标题信息', wx.YES_NO | wx.ICON_QUESTION)
if dlg.ShowModal() == wx.ID_YES:
    print('是')
dlg.Destroy()
```

#### ColourDialog

该对话框向用户显示颜色选择器，并返回颜色信息。

###### Demo 0

```python
dlg = wx.ColourDialog(self)
dlg.GetColourData().SetChooseFull(True)
if dlg.ShowModal() == wx.ID_OK:
    print(dlg.GetColourData().GetColour())
dlg.Destroy()
```

#### FontDialog

该对话框向用户显示字体选择器，并返回字体和颜色信息。

###### Demo 0

```python
dlg = wx.FontDialog(self, wx.FontData())
if dlg.ShowModal() == wx.ID_OK:
    print(dlg.GetFontData().GetChosenFont())
dlg.Destroy()
```

#### FileDialog

该对话框向用户弹出文件选择器框，在 *Windows* 和 *GTK 2.4+* 上，这是公共文件选择器对话框，在 *MacOS* 中，这是一个文件选择器框，功能有所减少。

###### Demo 0

```python
filesFilter = "Dicom (*.dcm)|*.dcm|" "All files (*.*)|*.*"
dlg = wx.FileDialog(self, message="选择单个文件", wildcard=filesFilter, style=wx.FD_OPEN)
if dlg.ShowModal() == wx.ID_OK:
    print(dlg.GetPath())
dlg.Destroy()
```

###### Demo 1

```python
filesFilter = "Dicom (*.dcm)|*.dcm|" "All files (*.*)|*.*"
dlg = wx.FileDialog(self, message="多文件选择", wildcard=filesFilter, style=wx.FD_OPEN | wx.FD_MULTIPLE)
if dlg.ShowModal() == wx.ID_OK:
    print(dlg.GetPaths())
dlg.Destroy()
```

###### Demo 2

```python
filesFilter = "Dicom (*.dcm)|*.dcm|" "All files (*.*)|*.*"
dlg = wx.FileDialog(self, message="保存文件", wildcard=filesFilter, style=wx.FD_SAVE)
if dlg.ShowModal() == wx.ID_OK:
    print(dlg.GetPath())
dlg.Destroy()
```

#### DirDialog

该对话框向用户显示一个目录选择器对话框，允许用户选择一个目录。

###### Demo 0

```python
dlg = wx.DirDialog(None, "选择一个目录:", style=wx.DD_DEFAULT_STYLE | wx.DD_NEW_DIR_BUTTON)
if dlg.ShowModal() == wx.ID_OK:
    print(dlg.GetPath())
dlg.Destroy()
```

#### TextEntryDialog

该对话框是一个带有文本输入字段的对话框，使用 `wx.TextEntryDialog.GetValue()` 获得用户输入的值。

###### Demo 0

```python
dlg = wx.TextEntryDialog(None, "请在下面文本框中输入内容:", "文本输入框标题", "默认内容")
if dlg.ShowModal() == wx.ID_OK:
    print(dlg.GetValue())
dlg.Destroy()
```

#### PasswordEntryDialog

该对话框是是一个带有密码输入字段的对话框，使用 `wx.TextEntryDialog.GetValue()` 获得用户输入的值。

###### Demo 0

```python
dlg = wx.PasswordEntryDialog(None, "请输入密码:", "密码输入框标题", "默认密码")
if dlg.ShowModal() == wx.ID_OK:
    print(dlg.GetValue())
dlg.Destroy()
```

#### SingleChoiceDialog

该对话框显示选项列表，以及 `OK` 和（可选）`Cancel`，用户可以选择其中之一，可以从对话框中获得索引，字符串或客户数据的选择。

###### Demo 0

```python
dlg = wx.SingleChoiceDialog(None, "请选择你喜欢的水果:", "列表选择框标题", ["苹果", "西瓜", "草莓"])
if dlg.ShowModal() == wx.ID_OK:
    print(dlg.GetStringSelection())
dlg.Destroy()
```

#### MultiChoiceDialog

该对话框显示选项列表，以及 `OK` 和（可选）`Cancel`，用户可以选择其中一个或多个。

###### Demo 0

```python
dlg = wx.MultiChoiceDialog(None, "请选择几种你喜欢的水果:", "列表多选框标题", ["苹果", "西瓜", "草莓"])
if dlg.ShowModal() == wx.ID_OK:
    print(dlg.GetSelections())
dlg.Destroy()
```

## 电子表格

使用 `Grid` 及其相关类可以显示和编辑表格数据，而且支持表单元格的自定义属性，从而可以完全自定义其外观，并使用单独的网格表（`GridTableBase` 派生）类进行数据管理，这意味着它可用于显示任意数量的数据。

```python
import wx
import wx.grid

class GridFrame(wx.Frame):
    def __init__(self, parent):
        wx.Frame.__init__(self, parent)
        # 创建一个 wxGrid 对象
        grid = wx.grid.Grid(self, -1)
        # 调用 CreateGrid 设置网格的尺寸（在此示例中为50行和8列）
        grid.CreateGrid(100, 10)
        # 设置单个行和列的大小（以像素为单位）
        grid.SetRowSize(0, 60)
        grid.SetColSize(0, 120)
        # 将网格单元格内容设置为字符串
        grid.SetCellValue(0, 0, 'wxGrid很好')
        # 指定某些单元格为只读
        grid.SetCellValue(0, 3, '这是只读的')
        grid.SetReadOnly(0, 3)
        # 为网格单元格内容指定颜色
        grid.SetCellValue(3, 3, '灰绿色')
        grid.SetCellTextColour(3, 3, wx.GREEN)
        grid.SetCellBackgroundColour(3, 3, wx.LIGHT_GREY)
        # 指定一些单元格将存储数字值而不是字符串，
        # 在这里，将网格列5设置为保留以6的宽度和2的精度显示的浮点值
        grid.SetColFormatFloat(5, 6, 2)
        grid.SetCellValue(0, 6, '3.1415')
        self.Show()

if __name__ == '__main__':
    app = wx.App(0)
    frame = GridFrame(None)
    app.MainLoop()
```
