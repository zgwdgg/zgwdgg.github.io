# 准备工作

# Python运行环境
> 以Python语言编写的程序，要能正确的运行，需要安装Python软件包。

大部分Linux/Unix系列的操作系统已经包含了Python软件，但本课程的学习大部分在Windows中进行，需要单独安装Python软件。

### 1 下载

你可以访问官网的链接 [Windows版本](https://www.python.org/downloads/windows/) 选择合适的文件进行下载。

目前Python主要版本是Python 3，在选择具体版本时，尽量选择最新的稳定版。

如下图所示，点击链接下载64位的安装文件。

![下载示意图](https://uinx1983.github.io/img/image-20211219140759903.png)

### 2 安装

接下来就根据提示完成，注意下图里红框处打上勾，然后点击`install now`。

![安装示意图](https://uinx1983.github.io/img/setup-path.png)

注意！如果安装的是老版本，没有上图所示的操作，需要手动配置系统`环境变量`：
1. 右键点击`计算机`，选择属性。
2. 接着的界面中选择`高级系统设置`。
3. 打开的窗口中点击`环境变量`按钮
4. 在下方的窗口中，选择变量`PATH`，双击打开。
5. 在弹出的窗口中，更改值，在最后添加Python的安装路径，注意前面有个`分号`！如下图所示：
![环境变量配置](https://uinx1983.github.io/img/path-setup.png)
6. 如果是windows 10，则是点击新建按钮，添加Python的安装路径，前面没有`分号`！如下图所示：
![环境变量配置-win10](https://uinx1983.github.io/img/path-setup-win10.png)
### 3 验证

安装完成后，在windows系统中，你可以打开命令提示符，输入命令`python -V`进行验证，屏幕会显示当前python版本号。

```sh
C:\Users\huanglei>python -V
Python 3.8.6
```



# 编程工具

python能适应从简单到复杂的各种场景，根据不同的情况，你也可以选择不同的编程工具或环境。

### 1 交互模式

> 交互模式常用于学习基本语法或函数。

在命令提示符中，直接输入命令`python`进入python交互模式，出现提示符`>>>`。

```python
C:\Users\huanglei>python
Python 3.8.6 (tags/v3.8.6:db45529, Sep 23 2020, 15:52:53) [MSC v.1927 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>>
```

在python提示符后，可以输入程序代码，回车后会执行代码。可以看到一行代码的结束可以是`;`，也可以不用结束符。

```python
>>> print("这是打印函数");
这是打印函数
>>> 1+2
3
```



### 2 文本编辑器

> 文本编辑器最大好处是所有操作系统都自带

虽然windows自带了文本编辑器，但是并不推荐使用它，因为windows 7及之前版本的默认字符编码不是utf-8，对中文的支持并不友好。

建议使用如[sublime-text](http://www.sublimetext.com/)、[Notepad++ ](https://notepad-plus-plus.org/) 等流行的文本编辑器

### 3 集成编程环境（IDE）

> 如果需要更方便的编程，IDE是更好的选择，IDE集成了文件管理、排错、控制台等多种功能

根据需要选择：
- Python自带的 IDLE
- 专业的 [PyCharm](https://www.jetbrains.com/pycharm/)
- 通用的 [VSCode](https://code.visualstudio.com/)

### 4 其他

有些python编程环境集成了许多有用的库，方便我们学习图表、大数据、人工智能等内容，比如 [Jupyter Notebooks](https://jupyter.org/) 





