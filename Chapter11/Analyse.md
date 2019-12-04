# 第1节：性能分析

代码优化能够让程序运行更快，它是在不改变程序运行结果的情况下使得程序的运行效率更高，根据 80/20 原则，实现程序的重构、优化、扩展以及文档相关的事情通常需要消耗 80% 的工作量。优化通常包含两方面的内容：减小代码的体积，提高代码的运行效率。

 

定位程序性能瓶颈

对代码优化的前提是需要了解性能瓶颈在什么地方，程序运行的主要时间是消耗在哪里，对于比较复杂的代码可以借助一些工具来定位，python 内置了丰富的性能分析工具，如 profile,cProfile 与 hotshot 等。其中 Profiler 是 python 自带的一组程序，能够描述程序运行时候的性能，并提供各种统计帮助用户定位程序的性能瓶颈。Python 标准模块提供三种 profilers:cProfile,profile 以及 hotshot。

profile 的使用非常简单，只需要在使用之前进行 import 即可。具体实例如下：

清单 8. 使用 profile 进行性能分析

```python
import profile

def profileTest():

  Total =1;

  for i in range(10):

​    Total=Total*(i+1)

​    print Total

  return Total

if __name__ == "__main__":

  profile.run("profileTest()")
```

程序的运行结果如下：

图 1. 性能分析结果

图 1. 性能分析结果

其中输出每列的具体解释如下：

 

ncalls：表示函数调用的次数；

tottime：表示指定函数的总的运行时间，除掉函数中调用子函数的运行时间；

percall：（第一个 percall）等于 tottime/ncalls；

cumtime：表示该函数及其所有子函数的调用运行的时间，即函数开始调用到返回的时间；

percall：（第二个 percall）即函数运行一次的平均时间，等于 cumtime/ncalls；

filename:lineno(function)：每个函数调用的具体信息；

如果需要将输出以日志的形式保存，只需要在调用的时候加入另外一个参数。如 profile.run("profileTest()","testprof")。

 

对于 profile 的剖析数据，如果以二进制文件的时候保存结果的时候，可以通过 pstats 模块进行文本报表分析，它支持多种形式的报表输出，是文本界面下一个较为实用的工具。使用非常简单：

import pstats

p = pstats.Stats('testprof')

p.sort_stats("name").print_stats()

其中 sort_stats() 方法能够对剖分数据进行排序， 可以接受多个排序字段，如 sort_stats('name', 'file') 将首先按照函数名称进行排序，然后再按照文件名进行排序。常见的排序字段有 calls( 被调用的次数 )，time（函数内部运行时间），cumulative（运行的总时间）等。此外 pstats 也提供了命令行交互工具，执行 python – m pstats 后可以通过 help 了解更多使用方式。

 

对于大型应用程序，如果能够将性能分析的结果以图形的方式呈现，将会非常实用和直观，常见的可视化工具有 Gprof2Dot，visualpytune，KCacheGrind 等，读者可以自行查阅相关官网，本文不做详细讨论。

 

Python 性能优化工具

Python 性能优化除了改进算法，选用合适的数据结构之外，还有几种关键的技术，比如将关键 python 代码部分重写成 C 扩展模块，或者选用在性能上更为优化的解释器等，这些在本文中统称为优化工具。python 有很多自带的优化工具，如 Psyco，Pypy，Cython，Pyrex 等，这些优化工具各有千秋，本节选择几种进行介绍。

 