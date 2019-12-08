# 第3节：编译相关优化

Psyco

psyco 是一个 just-in-time 的编译器，它能够在不改变源代码的情况下提高一定的性能，Psyco 将操作编译成有点优化的机器码，其操作分成三个不同的级别，有"运行时"、"编译时"和"虚拟时"变量。并根据需要提高和降低变量的级别。运行时变量只是常规 Python 解释器处理的原始字节码和对象结构。一旦 Psyco 将操作编译成机器码，那么编译时变量就会在机器寄存器和可直接访问的内存位置中表示。同时 python 能高速缓存已编译的机器码以备今后重用，这样能节省一点时间。但 Psyco 也有其缺点，其本身运行所占内存较大。目前 psyco 已经不在 python2.7 中支持，而且不再提供维护和更新了，对其感兴趣的可以参考 http://psyco.sourceforge.net/ 

Pypy

PyPy 表示 "用 Python 实现的 Python"，但实际上它是使用一个称为 RPython 的 Python 子集实现的，能够将 Python 代码转成 C， .NET， Java 等语言和平台的代码。PyPy 集成了一种即时 (JIT) 编译器。和许多编译器，解释器不同，它不关心 Python 代码的词法分析和语法树。 因为它是用 Python 语言写的，所以它直接利用 Python 语言的 Code Object.。 Code Object 是 Python 字节码的表示，也就是说， PyPy 直接分析 Python 代码所对应的字节码 ,，这些字节码即不是以字符形式也不是以某种二进制格式保存在文件中， 而在 Python 运行环境中。目前版本是 1.8. 支持不同的平台安装，windows 上安装 Pypy 需要先下载 https://bitbucket.org/pypy/pypy/downloads/pypy-1.8-win32.zip，然后解压到相关的目录，并将解压后的路径添加到环境变量 path 中即可。在命令行运行 pypy，如果出现如下错误："没有找到 MSVCR100.dll, 因此这个应用程序未能启动，重新安装应用程序可能会修复此问题"，则还需要在微软的官网上下载 VS 2010 runtime libraries 解决该问题。具体地址为 http://www.microsoft.com/download/en/details.aspx?displaylang=en&id=5555