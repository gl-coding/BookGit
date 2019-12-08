# 第1节：开发环境

#Anaconda

### 1.Anaconda是什么？

简单来说，Anaconda是Python的包管理器和环境管理器。
先来解决一个初学者都会问的问题：我已经安装了Python，那么为什么还需要Anaconda呢？原因有以下几点：

1. Anaconda附带了一大批常用数据科学包，它附带了conda、Python和 150 多个科学包及其依赖项。因此你可以用Anaconda立即开始处理数据。
2. 管理包。
    Anaconda 是在 conda（一个包管理器和环境管理器）上发展出来的。在数据分析中，你会用到很多第三方的包，而conda（包管理器）可以很好的帮助你在计算机上安装和管理这些包，包括安装、卸载和更新包。
3. 管理环境。
    为什么需要管理环境呢？比如你在A项目中用到了Python2，而新的项目要求使用Python3，而同时安装两个Python版本可能会造成许多混乱和错误。这时候conda就可以帮助你为不同的项目建立不同的运行环境。还有很多项目使用的包版本不同，比如不同的pandas版本，不可能同时安装两个pandas版本。你要做的应该是在项目对应的环境中创建对应的pandas版本。这时候conda就可以帮你做到。

### 2.Anaconda安装及配置

**1. 下载**

- 直接在官网下载安装包，官网地址[https://www.anaconda.com/download/](https://link.jianshu.com?t=https%3A%2F%2Fwww.anaconda.com%2Fdownload%2F)。不推荐，因为尤其的慢，而且通常是安装到一半就错误，如果您网速快随您（嘻嘻），安装相应版本就好，比如你是py3就安装3.选择适合你系统的安装包进行下载，下载完成后直接安装。
- Anaconda 安装包还可以到
   华镜像上]([https://mirrors.tuna.tsinghua.edu.cn/anaconda/archive/](https://link.jianshu.com?t=https%3A%2F%2Fmirrors.tuna.tsinghua.edu.cn%2Fanaconda%2Farchive%2F))下载安装，优点是下载速度快。

> 下载后直接点击安装，无脑点击下一步，选择你的安装路径，我的安装路径为D:\Anaconda3，然后耐心等待，等到安装完成。

**2. 测试是否安装正确**

- 

  

   在cmd命令下输入conda info看到如下图表示你已安装成功！ 

  ![img](https:////upload-images.jianshu.io/upload_images/1594655-61a6fd8e7bbd6bf5.png?imageMogr2/auto-orient/strip|imageView2/2/w/649/format/webp)

  image.png

- 如果提示conda不是内容命令，说明您在安装时未勾选配置环境变量的选项。接下来手动配置系统环境变量

**3.环境变量配置**
 将以下路径添加到系统环境变量中
 D:\ProgramData\Anaconda3;
 D:\ProgramData\Anaconda3\Scripts;
 D:\ProgramData\Anaconda3\Library\mingw-w64\bin;
 D:\ProgramData\Anaconda3\Library\usr\bin;
 D:\ProgramData\Anaconda3\Library\bin;

**4. 设置Anaconda镜像，加速下载包**
 使用conda install 包名 安装需要的Python非常方便，但是官方的服务器在国外，因此下载速度很慢，国内清华大学提供了Anaconda的仓库镜像，我们只需要配置Anaconda的配置文件，添加清华的镜像源，然后将其设置为第一搜索渠道即可cmd命令行下分别执行以下命令：

```csharp
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/c
conda config --set show_channel_urls yes
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge/`
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/msys2/
```

配置完后可以测试一下，安装第三方包明显神速了，哈哈哈

### 3. 包管理

安装Anaconda之后，我们就可以很方便的管理安装包（安装，卸载，更新）。
 **1. 安装包**
 conda 的包管理功能和pip 是一样的，当然你选择pip 来安装包也是没问题的。

```bash
1.  #安装 matplotlib   
2. conda install matplotlib
```

**2. 卸载包**

```csharp
1. # 删除包  
2. conda remove matplotlib  
```

**3. 更新包**

```bash
1. # 包更新  
2. conda update matplotlib  
```

**4. 查询已经安装的包**

```php
1. # 查看已安装的包  
2. conda list   
```

### 4.环境管理

conda 可以为你不同的项目建立不同的运行环境。

**1. 创建python2.7版本的环境**

```bash
#创建python2.7版本的环境
conda create -n python27 python=2.7
```

上面的命令中，python27是设置环境的名称（-n是指该命令后面的python27是你要创建环境的名称）
 注意：创建环境时，可以指定要安装在环境中的Python版本。当你同时使用 Python 2.x 和 Python 3.x 中的代码时这很有用。
 **2. 进入环境**

```bash
#进入我刚创建的python27环境
conda activate python27
```

进入之后，你可以在终端提示符中看到环境名称(python27)。当然，当你进入环境后，可以用conda list 查看环境中默认的安装包。

![img](https:////upload-images.jianshu.io/upload_images/1594655-b1cbd767feea2de3.png?imageMogr2/auto-orient/strip|imageView2/2/w/367/format/webp)

**3. 离开环境**

```bash
#离开当前环境
deactivate
```

**4. 共享环境**
 共享环境非常有用，它能让其他人安装你代码中使用的所有包，并确保这些包的版本正确。比如你开发了一个系统，你要提交给项目部署系统的人来部署你的项目，但是他们并不知道你当时开发时使用的是哪个python版本，以及使用了哪些包和包的版本。这怎么办呢？你可以在你当前的环境的终端中使用:

```bash
#将你当前的环境保存到文件中包保存为YAML文件
conda env export > environment.yaml  
```

将你当前的环境保存到文件中包保存为YAML文件（包括Pyhton版本和所有包的名称）。命令的第一部分 conda env export 用于输出环境中的所有包的名称（包括 Python 版本）。你在终端中上可以看到导出的环境文件路径。在 GitHub 上共享代码时，最好同样创建环境文件并将其包括在代码库中。这能让其他人更轻松地安装你的代码的所有依赖项。

导出的环境文件，在其他电脑环境中如何使用呢？
 首先在conda中进入你的环境，比如conda activate python27。然后在使用以下命令更新你的环境：

```bash
#其中-f表示你要导出文件在本地的路径，所以/path/to/environment.yml要换成你本地的实际路径  
conda env update -f=/path/to/environment.yml  
```

对于不使用conda 的用户，我们通常还会使用以下命令将一个 txt文件导出并包括在其中:

```css
pip freeze > environment.txt   
```

然后我将该文件包含在项目的代码库中，其他项目成员即使在他的电脑上没有安装conda也可以使用该文件来安装和我一样的开发环境：
 他在自己的电脑上进入python命令环境，然后运行以下命令就可以安装该项目需要的包：

```css
1. #其中C:\Users\Microstrong\enviroment.txt是该文件在你电脑上的实际路径。  
2. pip install -r C:\Users\Microstrong\enviroment.txt  
```

**5. 列出环境**
 有时候会忘记自己创建的环境名称，这时候用 conda env list 就可以列出你创建的所有环境。

![img](https:////upload-images.jianshu.io/upload_images/1594655-ddac0fbb474b5295.png?imageMogr2/auto-orient/strip|imageView2/2/w/492/format/webp)


 你会看到环境的列表，而且你当前所在环境的旁边会有一个星号。默认的环境（即当你不在选定环境中时使用的环境）名为 base。

**6. 删除环境**
 如果你不再使用某个环境，可以使用以下命令。

```csharp
1. #删除指定的环境（在这里环境名为 python27）。  
2. conda env remove -n python27  
```

### 安装问题总结

**1.failed to create anacoda menu。！！创建菜单失败。**
 解决办法：安装过程中一直忽略忽略直到安装成功。这个时候你打开你的开始菜单你会发现你并不能找到有关anaconda的任何不要慌。
 打开CMD，运行一下代码：

```bash
python .\Lib\_nsis.py mkmenus #出现很多sucessfully就对了
```

![img](https:////upload-images.jianshu.io/upload_images/1594655-636b426595d2f7e7.png?imageMogr2/auto-orient/strip|imageView2/2/w/616/format/webp)

**2.conda不是系统内部命令。**
 解决办法：将上述**3.环境变量配置**中提到的软件安装路径添加到系统环境变量中。
 **3.明明我添加了环境变量，还是提示“conda”不是系统内部命令。**
 打开CMD上面还显示C:\Anaconda3\Scripts\activate.bat'is not recognized as an internal or external command,operable program or batch file.
 解决办法：查到以下资料，解决了我的问题。这是Anaconda3的bug，将在后续版本中修复。请先安装最新版的Miniconda3。

#代码编辑—Vscode

一、什么是vscode**
    Visual Studio Code (简称 VS Code / VSC) 是一款免费开源的现代化轻量级代码编辑器，支持几乎所有主流的开发语言的语法高亮、智能代码补全、自定义热键、括号匹配、代码片段、代码对比 Diff、GIT 等特性，支持插件扩展，并针对网页开发和云端应用开发做了优化。软件跨平台支持 Win、Mac 以及 Linux。

vscode 官网： https://code.visualstudio.com/

三、Vscode下载
下载地址：https://code.visualstudio.com/Download

可下载.zip解压版，下载解压后即可使用。【其是用electron打包的】

也可下载安装版可执行程序，安装后很多东西都不需要你自己配置了。

四、汉化vscode
按f1 搜索 Configore Display Language 设置 zh-cn 关闭软件重启。

注意：
如果重启后还是英文的，那么在商店查看已安装的插件，把中文插件Chinese(simplified) 重新安装一遍，然后重启软件即可。

七、基本使用
1.直接拖入项目文件夹进入软件
    方式一： 拖入工作区（这样的话，会保留当前以及打开的项目文件夹）

    方式二： 拖入工作区右边的窗口，这样的话会让拖入的窗口覆盖掉原本以及打开的窗口

（这时vscode会问你是否保存一个文件，用来保存原本工作区信息，以便下次打开此文件）

备注：对于左侧的文件夹可以直接使用快捷键复制粘贴等。
2.在vscode里面创建项目文件夹

3.格式化代码
在代码里面右键菜单，会弹出相应的格式化等功能选项，也有定义引用查找等菜单。

4.在浏览器中打开网页

1.以file文件协议形式打开文件

安装插件：Open HTML in Default Browser
1
特点

用默认浏览器打开 HTML 文件
在资源管理器中，HTML 文件右键显示 在浏览器中打开 菜单
在编辑器中，HTML 文件右键显示
在浏览器中打开 菜单 可以同时打开多个页面
我们在工作区项目上右键菜单就能看到在资源管理器中打开文件的选项

2.以服务器形式打开文件
方式一：
    安装live server 插件，点击重新加载或者重启vscode，然后鼠标右键就可以在服务器上打开，
这种模式打开会自动刷新页面。
方式二：
    1.按下快捷键：Ctrl+` 打开命令行终端，执行cnpm install live-server -g

    2.安装好后每次要运行只需要打开终端后执行一下live-server即可
    
    3.使用live-server是把整个网站打开到服务器上的。不管你当前定位到哪一个目录，他打开的都是默认的首页文件，如：index.html
    
    4.如果你根目录下全是文件夹，或者没有index.html等默认首页文件，那么服务器就会显示一些文件夹让你选择。

如：

    5.如果要关闭live-server那么只需要在控制台执行以下ctrl+c，然后输入y确认下即可关闭。
    6.Live-server可以在任意项目根目录下，打开终端窗口，然后输入live-server即可让当前项目在服务器上打开执行
    7.在以服务器打开的模式下，我们更改了文件内容后只要保存下，浏览器就会自动的刷新，而不需要我们显式的在浏览器里面刷新。

方式三：
    也可以安装http server插件，安装完成后按下f1,然后输入http会看到下面两个选项，选择with current file那个能够创建一个服务器运行当前文件。另外一个会找当前目录下的index.html,然后打开它。

选择一个后，会再让你选择在浏览器里面打开还是vscode里面打开。

其他
    你也可以全局安装此模块【cnpm install http-server -g 】
安装到全局后：在终端里面输入hs就可以使用。

八、插件安装
安装与卸载

安装： 在左边最下面是哪个图标点击搜索插件进行安装即可。
卸载： 同样的地方找到插件，然后进行卸载即可。
    如果安装了某个插件后无法看到效果，那么请重启下vscode，或者重新加载
常用插件：

HTML Boilerplate
    通过使用 HTML 模版插件，你就摆脱了为 HTML 新文件重新编写头部和正文标签的苦恼。你只需在空文件中输入 html，选中html:5即可生成一个新的网页文件，也可以输入一个感叹号

browser-plus
在编辑器内预览HTML
    通过开启端口(10086)监听当前打开项目的根目录，在编辑器内预览网站，省去了频繁切换浏览器、编辑器看页面效果，修改代码后自动刷新页面。
使用方法
Window Ctrl+F1 ，默认10086端口预览网页

CSS Peek
    使用此插件，你可以追踪至样式表中 CSS 类和 ids 定义的地方。当你在 HTML 文件中右键单击选择器时，选择“ Go to Definition 和 Peek definition ”选项，它便会给你发送样式设置的 CSS 代码。

Color Info
    这个便捷的插件，将为你提供你在 CSS 中使用颜色的相关信息。你只需在颜色上悬停光标，就可以预览色块中色彩模型的（HEX、 RGB、HSL 和 CMYK）相关信息了。

Auto Close Tag
    自动闭合HTML/XML标签

Auto Rename Tag
    自动完成另一侧标签的同步修改

HTML Snippets
    智能提示HTML标签，以及标签含义JavaScript(ES6) code snippetsES6语法智能提示，以及快速输入，不仅仅支持.js，还支持.ts，.jsx，.tsx，.html，.vue，省去了配置其支持各种包含js代码文件的时间

Path Intellisense
    自动提示文件路径，支持各种快速引入文

jQuery Code Snippets
　　jQuery代码智能提示

Icon Fonts
    这是一个能够在项目中添加图标字体的插件。该插件支持超过 20 个热门的图标集，包括了 Font Awesome、Ionicons、Glyphicons 和 Material Design Icons。

自动编译less文件为css文件：
    安装插件 Easy LESS，保存自动编译，不需要配置（默认编译到当前目录下）
    如果需要编译为不同文件名的css文件，那么在less文件的最上面加上一行注释即可：// out: new-file.css

# jupyter notebook

什么是Jupyter notebook?

> jupyter Notebook（此前被称为 IPython notebook）是一个交互式笔记本，支持运行 40 多种编程语言。 Jupyter Notebook 的本质是一个 Web 应用程序，便于创建和共享文学化程序文档，支持实时代码，数学方程，可视化和 markdown。 用途包括：数据清理和转换，数值模拟，统计建模，机器学习等等

jupyternotebook

可以单独运行某段代码，及markdown文字记录格，如流程式编程，你可以分开一小功能代码单独运行测试。若是需要展示数据图片，更是方便。



##现记录下其安装与使用：

1.安装：

1.1老版本Anacodna需自己安装Jupyter

安装Jupyter Notebook的**先决条件**：已经安装了python（python 2.7 或者是python3.3）

具体的安装方法：

官方建议利用Anaconda安装Jupyter

安装完成Anaconda后，如果该Anaconda并不自带Jupyter Noterbook，那么，打开cmd，输入：conda install jupyter

1.2 pip安装： pip install jupyter notebook?



### 2.使用：

2.1启动：CMD中输入 ： jupyter notebook
 运行之后，会自动打开其网页的界面，在每一行中编辑python代码或文字，测试运行就可以了。

2.2模式切换 当前cell侧边为蓝色时，表示此时为命令模式，按Enter切换为编辑模式 当前cell侧边为绿色时，表示此时为编辑模式，按Esc切换为命令模式

2.3 快捷键
 命令模式快捷键 H
 显示快捷键帮助 F
 查找和替换 P
 打开命令面板 Ctrl-Enter
 运行当前cell Shift-Enter
 运行当前cell并跳转到下一cell Alt-Enter
 运行当前cell并在下方新建cell Y
 把当前cell内容转换为代码形式 M
 把当前cell内容转换为markdown形式 1~6
 把当前cell内容设置为标题1~6格式 Shift+上下键
 按住Shift进行上下键操作可复选多个cell A
 在上方新建cell B
 在下方新建cell X/C/Shift-V/V
 剪切/复制/上方粘贴/下方粘贴 双击D
 删除当前cell Z
 撤销删除 S
 保存notebook L
 为当前cell的代码添加行编号 Shift-L
 为所有cell的代码添加行编号 Shift-M
 合并所选cell或合并当前cell和下方的cell 双击I
 停止kernel 双击0
 重启kernel

2.4编辑模式快捷键 Tab
 代码补全 Ctrl-A
 全选 Ctrl-Z
 撤销 Ctrl-Home
 将光标移至cell最前端 Ctrl-End
 将光标移至cell末端

2.5 鼠标操作工具栏cell

![img](https:////upload-images.jianshu.io/upload_images/2381238-628821cf5d691b3c.png?imageMogr2/auto-orient/strip|imageView2/2/w/1200/format/webp)

工具栏cell.png

3 Jupyter Notebook插入图片的4种方法

3.1 MD标记法:
 ! [#ps: 用此法路径务必是右斜杠] (img/python.png)

*前面有”!”符号，无论windows还是linux图片路径都是右斜杠“/”*