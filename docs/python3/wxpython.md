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

## 控件

#### Button

该控件仅包含一个文本字符串，用来触发某个动作。

```python
class Example(wx.Frame):
    def __init__(self, *args, **kw):
        super(Example, self).__init__(*args, **kw)
        self.InitUI()

    def InitUI(self):
        pnl = wx.Panel(self)
        # 创建一个 Close 按键，点击 Close 即可关闭应用
        cbtn = wx.Button(pnl, label='Close', pos=(20, 30))
        # 按钮的文本标签以及它在面板上的位置
        cbtn.Bind(wx.EVT_BUTTON, self.OnClose)
        self.SetSize((250, 200))
        self.SetTitle('wx.Button')
        self.Centre()
        self.Show(True)

    def OnClose(self, e):
        # 调用 Close() 函数来关闭应用
        self.Close(True)
```

#### ToggleButton

该控件也是一种按钮，但它有两个状态：点击和非点击状态。通过点击按键可以在两种状态中切换，在特定场景中，这一功能将非常适用。

```python
class Example(wx.Frame):
    """
    创建了红色、绿色和蓝色的 Toggle button 和一个 Panel，
    点击 toggle button的时候，可以改变 Panel 的颜色。
    """
    def __init__(self, *args, **kw):
        super(Example, self).__init__(*args, **kw)
        self.InitUI()

    def InitUI(self):
        pnl = wx.Panel(self)
        self.col = wx.Colour(0, 0, 0)
        # 创建一个 wx.ToggleButton 控件
        rtb = wx.ToggleButton(pnl, label='red', pos=(20, 25))
        gtb = wx.ToggleButton(pnl, label='green', pos=(20, 60))
        btb = wx.ToggleButton(pnl, label='blue', pos=(20, 100))
        # 创建一个 Panel，颜色设置为 self.col
        self.cpnl = wx.Panel(pnl, pos=(150, 20), size=(110, 110))
        self.cpnl.SetBackgroundColour(self.col)
        # 点击 rtb 触发这个 button 的时候 ToggleRed() 会被调用
        rtb.Bind(wx.EVT_TOGGLEBUTTON, self.ToggleRed)
        gtb.Bind(wx.EVT_TOGGLEBUTTON, self.ToggleGreen)
        btb.Bind(wx.EVT_TOGGLEBUTTON, self.ToggleBlue)
        self.SetSize((300, 200))
        self.SetTitle('Toggle buttons')
        self.Centre()
        self.Show(True)

    def ToggleRed(self, e):
        """对 rtb 按钮是否被按下做出反应，来改变特定面板的颜色"""
        obj = e.GetEventObject()
        isPressed = obj.GetValue()
        green = self.col.Green()
        blue = self.col.Blue()
        if isPressed:
            self.col.Set(255, green, blue)
        else:
            self.col.Set(0, green, blue)
        self.cpnl.SetBackgroundColour(self.col)
        self.cpnl.Refresh()

    def ToggleGreen(self, e):
        obj = e.GetEventObject()
        isPressed = obj.GetValue()
        red = self.col.Red()
        blue = self.col.Blue()
        if isPressed:
            self.col.Set(red, 255, blue)
        else:
            self.col.Set(red, 0, blue)
        self.cpnl.SetBackgroundColour(self.col)
        self.cpnl.Refresh()

    def ToggleBlue(self, e):
        obj = e.GetEventObject()
        isPressed = obj.GetValue()
        red = self.col.Red()
        green = self.col.Green()
        if isPressed:
            self.col.Set(red, green, 255)
        else:
            self.col.Set(red, green, 0)
        self.cpnl.SetBackgroundColour(self.col)
        self.cpnl.Refresh()
```

#### StaticLine

该控件在窗口上展示一个简单的直线，可以是竖直或水平的。

```python
class Example(wx.Frame):
    def __init__(self, *args, **kw):
        super(Example, self).__init__(*args, **kw)
        self.InitUI()

    def InitUI(self):
        font = wx.Font(10, wx.DEFAULT, wx.NORMAL, wx.BOLD)
        heading = wx.StaticText(self, label='The Central Europe', pos=(130, 15))
        heading.SetFont(font)
        wx.StaticLine(self, pos=(25, 50), size=(300, 1))
        wx.StaticText(self, label='Slovakia', pos=(25, 80))
        wx.StaticText(self, label='Hungary', pos=(25, 100))
        wx.StaticText(self, label='Poland', pos=(25, 120))
        wx.StaticText(self, label='5 445 000', pos=(250, 80))
        wx.StaticText(self, label='10 014 000', pos=(250, 100))
        wx.StaticText(self, label='38 186 000', pos=(250, 120))
        wx.StaticLine(self, pos=(25, 160), size=(300, 1))
        tsum = wx.StaticText(self, label='164 336 000', pos=(240, 180))
        sum_font = tsum.GetFont()
        sum_font.SetWeight(wx.BOLD)
        tsum.SetFont(sum_font)
        btn = wx.Button(self, label='Close', pos=(140, 210))
        btn.Bind(wx.EVT_BUTTON, self.OnClose)
        self.SetSize((360, 280))
        self.SetTitle('wx.StaticLine')
        self.Centre()
        self.Show(True)

    def OnClose(self, e):
        self.Close(True)
```

#### StaticText

该控件在窗口上展示展示一行或多行的只读文本。

```python
class Example(wx.Frame):
    def __init__(self, *args, **kw):
        super(Example, self).__init__(*args, **kw)
        self.InitUI()

    def InitUI(self):
        # 要在 wx.StaticText 展示的字符串
        txt1 = '''第一段第1行
第一段第2行 体现居中效果
第一段第3行'''
        txt2 = '''第二段第1行
第二段第2行
第二段第3行 体现居中效果'''
        pnl = wx.Panel(self)
        vbox = wx.BoxSizer(wx.VERTICAL)
        # 创建 wx.StaticText 控件，文字居中展示
        st1 = wx.StaticText(pnl, label=txt1, style=wx.ALIGN_CENTRE)
        st2 = wx.StaticText(pnl, label=txt2, style=wx.ALIGN_CENTRE)
        vbox.Add(st1, flag=wx.ALL, border=5)
        vbox.Add(st2, flag=wx.ALL, border=5)
        pnl.SetSizer(vbox)
        self.SetSize((220, 180))
        self.SetTitle('wx.StaticText')
        self.Centre()
        self.Show(True)
```

#### StaticBox

该控件是一个装饰控件，被用来逻辑上将一组控件包括起来。必须在它所包含的控件创建之前创建，且那些被包含的控件是 `wx.StaticBox` 的兄弟控件而非子控件。

```python
class Example(wx.Frame):
    def __init__(self, *args, **kw):
        super(Example, self).__init__(*args, **kw)
        self.InitUI()

    def InitUI(self):
        pnl = wx.Panel(self)
        wx.StaticBox(pnl, label='个人信息', pos=(5, 5), size=(240, 170))
        wx.CheckBox(pnl, label='男', pos=(15, 30))
        wx.CheckBox(pnl, label='已婚', pos=(15, 55))
        wx.StaticText(pnl, label='年龄', pos=(15, 95))
        wx.SpinCtrl(pnl, value='1', pos=(55, 90), size=(60, -1), min=1, max=120)
        btn = wx.Button(pnl, label='Ok', pos=(90, 185), size=(60, -1))
        btn.Bind(wx.EVT_BUTTON, self.OnClose)
        self.SetSize((270, 250))
        self.SetTitle('Static box')
        self.Centre()
        self.Show(True)

    def OnClose(self, e):
        self.Close(True)
```

#### ComboBox

该控件是由一行文本域、一个带有下拉箭头图标的按钮和一个列表框所构成的。当你按下按钮时，将出现一个列表框，用户只可选择其中的一个选项。

```python
class Example(wx.Frame):
    def __init__(self, *args, **kw):
        super(Example, self).__init__(*args, **kw)
        self.InitUI()

    def InitUI(self):
        pnl = wx.Panel(self)
        # 被选择的选项将会显示在文本标签上
        distros = ['Ubuntu', 'Arch', 'Fedora', 'Debian', 'Mint']
        # 单选框将包含以上列表的字符串
        # 创建 wx.ComboBox，通过 choices 参数传入一个字符串列表，wx.CB_READONLY 使得列表的字符串只读，即不可编辑
        cb = wx.ComboBox(pnl, pos=(50, 30), choices=distros, style=wx.CB_READONLY)
        self.st = wx.StaticText(pnl, label='', pos=(50, 140))
        # 当从单选框选择一个选项时，wx.EVT_COMBOBOX 事件将被触发，绑定 OnSelect() 来处理该事件
        cb.Bind(wx.EVT_COMBOBOX, self.OnSelect)
        self.SetSize((250, 230))
        self.SetTitle('wx.ComboBox')
        self.Centre()
        self.Show(True)

    def OnSelect(self, e):
        i = e.GetString()
        self.st.SetLabel(i)
```

#### CheckBox

该控件只有两个状态：打开或关闭，它有一个框和文本标签组成，文本标签可以设置为放在框的左边或者右边。当 `wx.CheckBox` 被选择之后，框里将出现一个对号√。

```python
class Example(wx.Frame):
    """通过一个 wx.CheckBox 控件来决定是否显示或隐藏窗口的标题"""
    def __init__(self, *args, **kw):
        super(Example, self).__init__(*args, **kw)
        self.InitUI()

    def InitUI(self):
        pnl = wx.Panel(self)
        # wx.CheckBox 控件的构造函数
        cb = wx.CheckBox(pnl, label='显示标题', pos=(20, 20))
        # 由于窗口的标题应该是被默认显示的，所以通过 SetValue() 方法默认选择 wx.CheckBox
        cb.SetValue(True)
        # 当点击 wx.CheckBox 控件时，wx.EVT_CHECKBOX 事件将被触发，将其绑定至事件处理器 ShowOrHideTitle() 函数
        cb.Bind(wx.EVT_CHECKBOX, self.ShowOrHideTitle)
        self.SetSize((270, 120))
        self.SetTitle('wx.CheckBox')
        self.Centre()
        self.Show(True)

    def ShowOrHideTitle(self, e):
        """通过 wx.CheckBox 的状态来决定是否隐藏或显示窗口的标题"""
        sender = e.GetEventObject()
        isChecked = sender.GetValue()
        if isChecked:
            self.SetTitle('wx.CheckBox')
        else:
            self.SetTitle('')
```

![wxpython-checkbox](wxpython-checkbox.png)

## 对话框

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

## 表格

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
