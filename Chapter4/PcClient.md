# 第5节：Pc客户端

Python PyInstaller安装和使用教程

在创建了独立应用（自包含该应用的依赖包）之后，还可以使用 PyInstaller 将 [Python](http://c.biancheng.net/python/) 程序生成可直接运行的程序，这个程序就可以被分发到对应的 Windows 或 Mac OS X 平台上运行。

## 安装 PyInstalle

Python 默认并不包含 PyInstaller 模块，因此需要自行安装 PyInstaller 模块。

安装 PyInstaller 模块与安装其他 Python 模块一样，使用 pip 命令安装即可。在命令行输入如下命令：

pip install pyinstaller

强烈建议使用 pip 在线安装的方式来安装 PyInstaller 模块，不要使用离线包的方式来安装，因为 PyInstaller 模块还依赖其他模块，pip 在安装 PyInstaller 模块时会先安装它的依赖模块。

运行上面命令，应该看到如下输出结果：

Successfully installed pyinstaller-x.x.x

其中的 x.x.x 代表 PyInstaller 的版本。

在 PyInstaller 模块安装成功之后，在 Python 的安装目录下的 Scripts(D:\Python\Python36\Scripts) 目录下会增加一个 pyinstaller.exe 程序，接下来就可以使用该工具将 Python 程序生成 EXE 程序了。

## PyInstaller生成可执行程序

PyInstaller 工具的命令语法如下：

pyinstaller 选项 Python 源文件

不管这个 Python 应用是单文件的应用，还是多文件的应用，只要在使用 pyinstaller 命令时编译作为程序入口的 Python 程序即可。

PyInstaller工具是跨平台的，它既可以在 Windows平台上使用，也可以在 Mac OS X 平台上运行。在不同的平台上使用 PyInstaller 工具的方法是一样的，它们支持的选项也是一样的。

下面先创建一个 app 目录，在该目录下创建一个 [app.py](http://app.py/) 文件，文件中包含如下代码： 

1. from say_hello import * 
2. **def** main(): 
3. **print**('程序开始执行')
4. **print**(say_hello('孙悟空'))
5. \# 增加调用main()函数
6. **if** __name__ == '__main__': 
7. main()

接下来使用命令行工具进入到此 app 目录下，执行如下命令：

pyinstaller -F [app.py](http://app.py/) 

执行上面命令，将看到详细的生成过程。当生成完成后，将会在此 app 目录下看到多了一个 dist 目录，并在该目录下看到有一个 app.exe 文件，这就是使用 PyInstaller 工具生成的 EXE 程序。

在命令行窗口中进入 dist 目录下，在该目录执行 app.exe ，将会看到该程序生成如下输出结果：



程序开始执行 

孙悟空，您好！

由于该程序没有图形用户界面，因此如果读者试图通过双击来运行该程序，则只能看到程序窗口一闪就消失了，这样将无法看到该程序的输出结果。

在上面命令中使用了-F 选项，该选项指定生成单独的 EXE 文件，因此，在 dist 目录下生成了一个单独的大约为 6MB 的 app.exe 文件（在 Mac OS X 平台上生成的文件就叫 app，没有后缀）；与 -F 选项对应的是 -D 选项（默认选项），该选项指定生成一个目录（包含多个文件）来作为程序。

下面先将 PyInstaller 工具在 app 目录下生成的 build、dist 目录删除，并将 app.spec 文件也删除，然后使用如下命令来生成 EXE 文件。

pyinstaller -D [app.py](http://app.py/) 

执行上面命令，将看到详细的生成过程。当生成完成后，将会在 app 目录下看到多了一个 dist 目录，并在该目录下看到有一个 app 子目录，在该子目录下包含了大量 .dll 文件和 .pyz 文件，它们都是 app.exe 程序的支撑文件。在命令行窗口中运行该 app.exe 程序，同样可以看到与前一个 app.exe 程序相同的输出结果。

PyInstaller 不仅支持 -F、-D 选项，而且也支持如表 1 所示的常用选项。

| -h，--help                  | 查看该模块的帮助信息                                         |
| --------------------------- | ------------------------------------------------------------ |
| -F，-onefile                | 产生单个的可执行文件                                         |
| -D，--onedir                | 产生一个目录（包含多个文件）作为可执行程序                   |
| -a，--ascii                 | 不包含 Unicode 字符集支持                                    |
| -d，--debug                 | 产生 debug 版本的可执行文件                                  |
| -w，--windowed，--noconsolc | 指定程序运行时不显示命令行窗口（仅对 Windows 有效）          |
| -c，--nowindowed，--console | 指定使用命令行窗口运行程序（仅对 Windows 有效）              |
| -o DIR，--out=DIR           | 指定 spec 文件的生成目录。如果没有指定，则默认使用当前目录来生成 spec 文件 |
| -p DIR，--path=DIR          | 设置 Python 导入模块的路径（和设置 PYTHONPATH 环境变量的作用相似）。也可使用路径分隔符（Windows 使用分号，[Linux](http://c.biancheng.net/linux_tutorial/) 使用冒号）来分隔多个路径 |
| -n NAME，--name=NAME        | 指定项目（产生的 spec）名字。如果省略该选项，那么第一个脚本的主文件名将作为 spec 的名字 |

在表 1 中列出的只是 PyInstaller 模块所支持的常用选项，如果需要了解 PyInstaller 选项的详细信息，则可通过 pyinstaller -h 来查看。

下面再创建一个带图形用户界面，可以访问 [MySQL](http://c.biancheng.net/mysql/) 数据库的应用程序。

在 app 当前所在目录再创建一个 dbapp 目录，并在该目录下创建 Python 程序，其中 [exec_select.py](http://exec_select.py/) [程序负责查询数据，main.py](http://xn--,main-361js5zq7dz3gn16co92bwddrb.py/) 程序负责创建图形用户界面来显示查询结果。 