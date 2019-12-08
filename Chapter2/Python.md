# 第1节：Python



##1.1输出与输入
一般编程语言的教程都从打印“Hello World!”开始，我们这里也不免俗套，从打印开始。 

print 打印Python 提供 print 方法来打印信息，下面打开 Python shell 来打印一些信息。 

Python shell 

```python
>>>print "hello", hello 
print "hello", hello 
```

调用 print 方法，用户双引号(" ")把需要打印输出的信息引起来就被输出了。可是，我给你什么 信息，你就打印什么，这个很无聊!那我们就打印点有意思的。让打印信息向你问好。 

Python shell 

```python
>>> name = "zhangsan"
>>> print "hello %s ,Nice to meet you!" %name 
hello zhangsan ,Nice to meet you!

>>> name = "Lisi"
>>> print "hello %s ,Nice to meet you!" %name 
hello Lisi ,Nice to meet you! 
```

虽然，我们两次的打印语句一样，但由于定义的变量 name 两次赋值不同，那么打印出的结果也不完 全相同。%s(string)只能打印字符串，如果想打印数字，那么就要使用%d(data)。 

Python shell 

```python
>>> age=27
>>> print "You are %d !" %age 
```


但是，有时候我们并不知道自己要打印的是什么类型的数据，那么可以用%r 来表示。 

Python shell 

```python
>>> n = 100
>>> print "You print is %r ." %n 
You print is 100 .

>>> n = "abc"
>>> print "You print is %r ." %n 
You print is 'abc' . 
```



##1.2 input 输入 

其实，上面的例子也没意思，打印的变量信息还不是我们事先定义好的。比如 name=“zhangsan”。 那我希望打印的信息在程序运行的过程中由用户输入来。Python 提供了 input 方法来接收用户输入的信息。 创建一个.py 文件保存。输入下面的内容: 

Python shell 

```python
pr.py 

#coding=utf-8

n = input("Enter any content:") 
print "Your input is %r " %n 
```

当运行到 input()时，则需要用户输入一些信息。print 将会把用户输入的内容 打印出来。 

##1.3raw_input 输入 

但 input()方法比较矫情，要求用户输入的数据类型一定正确，比如字符串一定要加引号，如何不加将 会报错。 

Python shell 

```python
>>> ================================ RESTART ================================ >>>
Enter any content:I this year 5 years old 

Traceback (most recent call last):
File "C:/Users/fnngj/Desktop/pr.py", line 2, in <module> 

n = input("Enter any content:") File "<string>", line 1 

  I this year 5 years old

SyntaxError: invalid syntax

```

那么我们可以使用 raw_input()方法，它倒是没那么矫情(任何类型的输入它都可以接收)，用户输 入什么就是什么。 

你可以将 input()方法替换为 raw_input()再来运行输入一个不加引号的字符串，看看会不会还抛类 型错误。 

##1.4 引号与注释

引号与注释 在 Python 当中，不区分单引号('')与双引号("")，也就是说单、双引号都可以表示一个字符串。 

Python shell 

```python
>>> print "hello"

hello

>>> print 'world'

world
```

可以嵌套使用，但不能交叉使用。

Python shell 

```python
>> print "你说:'你好'" 你说:'你好'
print '我说:"今天天气不错"' 我说:"今天天气不错"

>> print "你笑了笑'离开了" 。'
SyntaxError: invalid syntax 
```

##注释

再来看看注释，基本上每种语言都会分单行注释和多行注释。Python 的单注释用井号(#)表示。 

Python shell 

```python
print "hell world" #打印 hello world       

多行注释用三对引号表示，不分单、双引号。

xx.py 

""" 

我们实现一个伟大的程序 那么是 print 一行数据 ^_^ """ 

'''

This is a

Multi line comment

'''
```

## 字符串

字符串是一组`不可修改的序列`，通常用单引号`''`或者双引号`""`包围组成。

```python
# 字符串的表示
name = 'Joe'
name = "Joe"
```

------

## 转译字符

在字符串里边，一些字符有隐藏的功能，可以用`\`这个符号召唤。

```python
>>> print('a\nb') # \n 换行 | windows系统换行是 \r\n
a
b

>>> print('a\tb') # \t 制表符
a	b 

>>> print('\\') # \ 本身也要转译
\

>>> print('\'\"') # 单引号双引号也需要转译
'"
```

------

## 格式化

`格式化`是常见的字符串拼装形式。`使用格式`'占位符1 占位符2' % (字符串1, 字符串2)

```python
# 占位符
# %d 整数
# %f 浮点数
# %x 十六进制
# %s 字符串 | 如果不想那么严谨，所有类型都能有 %s 表示

>>> print('hello %s' % 'word')
hello world

>>> print('%s %s' % ('hello', 'world'))
hello world
```

------

## 字符合并

```python
>>> 'a' + 'b'
ab 
```

------

## 切片

`切片`是Python赋予`序列`的独特能力，我们前面说过，字符串是一组`不可修改的序列`。

```python
# 序列
# 'abcde'
# '01234'

# 按照这个序列索引取值的行为，就是切片。
>>> 'abcde'[0]
'a'
>>> 'abcde'[1:3]
'bc'

# 不可变性质
>>> 'abc'[0] = 'b' # (不能直接修改字符串的值)
"TypeError: 'str' object does not support item assignment"
```

------

## 字符串操作

比较常用的一些。

```python
# 长度
>>> len('abc')
3

# 分解
>>> 'a,b,c'.split(',') # (当你需要把字符串变成列表的时候）
['a', 'b', 'c']

# 连接
>>> ','.join('abc') 
'a,b,c'

# 首字母大写
>>> 'abc'.capitalize()
Abc

# 大写
>>> 'abc'.upper()
ABC

# 小写
>>> 'ABC'.lower()
abc

# 大小写转换
>>> 'AbC'.swapcase()
aBc

# 检测开头字符
>>> 'abc'.startswith('a')
True

# 检测结尾字符
>>> 'abc'.endswith('a')
False

# 字符首次出现的位置 （序列索引，从0开始）
>>> 'cc'.find('c')
0

# 字符最后出现的位置
>>> 'cc'.rfind('c')
1

# 次数
>>> 'cc'.count('c')
2

# 替换
>>> 'a'.replace('a','b',100) # 把a替换成b，第三个参数100指：最多替换100个a
b
```

## 数字类型

Python的数字类型中又分为两类，`整型`和`浮点型`。

```python
>>> type(1)
# <class 'int'> 整型

>>> type(1.1)
# <class 'float'> 浮点型

>>> int(1.1)
1 # 浮点型转整型
```

## 数字运算

在Python中常用的数字运算表达方法。

```python
>>> 1+1
2 # 加

>>> 1-1
0 # 减

>>> 1*2
2 # 乘

>>> 1 / 2
0.5 # 除

>>> 10 // 3 
3 # 整除

>>> 10 % 3 
1 # 余数 

>>> 2e2 
200  # 10的倍数 | 2 * 10 *10

>>> 2**3
8 # 次方 | 2 * 2 * 2
```

## 列表

列表是一组`可以修改的序列`，可以存放`任何`数据类型。

```python
>>> type([])
# <class 'list'> 列表用 [] 表示

# 定义列表
>>> l = [1,'a',{},[],True]
>>> print(l)
[1,'a',{},[],True]
```

------

## 切片

由于列表是`序列`的性质，所以支持切片。

```python
>>> [1,2,3][0]
1

>>> [1,2,3][-1]
3

>>> [1,2,3][0:2]
[1,2]

>>> [1,[1,2,3]][1][1]
2
```

------

## 列表操作

比较常用的一些。

```python
# 长度
>>> len([1,2,3])
3

# 连接
>>> ''.join(['a','b','c']) # (当你需要把列表变成字符串的时候）
abc

# 末尾插入
>>> l = [1,2]
>>> l.append(3)
>>> l
[1,2,3]

# 插入指定位置
>>> l = [1,2,3]
>>> l.insert(2, 'a')
>>> l
[1, 2, 'a', 3]

# 获取并删除
>>> l = [1,2,3]
>>> ll = l.pop(0) # 不指定位置默认弹出最后一位
>>> l
[2,3]
>>> ll
1

# 位置
>>> [1,2,3].index(1)
0

# 数字排序
>>> l = [1,3,2]
>>> l.sort()
>>> l
[1,2,3]

# 合并
>>> l = [1,2]
>>> l.extend([3])
>>> l
[1,2,3]
```



## 元组

元组是一个更加`安全的列表`。元组跟列表很像，只是定义好了以后，里面的数据就不能修改。

```python
>>> type(())
# <class 'tuple'> 元组用 () 表示

# 定义元组
>>> t = (1,'a',{},[],True)
>>> print(t)
(1,'a',{},[],True)

# 歧义
>>> t = (1,) # 当元组只有一位时后面跟上逗号，避免歧义
```

------

## 切片

元组也是一个`序列`。

```python
>>> [1,2,3][0]
1

>>> (1,2,3)[-1]
3

>>> (1,2,3)[0:2]
(1,2)

>>> (1,[1,2,3])[1][1]
2
```

------

## 元组操作

`列表`中不改变对象值的方法，大部分都被`元组`继承。

```python
# 长度
>>> len((1,2,3))
3

# 索引位置
>>> (1,2,3).index(1)
0
```



## 布尔值

布尔值是状态的表示，只要两种状态，`True`表示真、`False`为假。

------

## None

`None`是Python一个特殊的对象，表示什么也没有。

------

## 常量

通常一种语言，有`变量`和`常量`两种量，相对于变量可以随便赋值修改，常量就是定义就不改动，经常用于一些程序初始配置。但是`Python`是没有常量的。我们可以自我约定，大写的变量就是常量，定义就不修改。













##2 分支与循环

Python 的设计哲学就是简单，没那么花里胡哨的东西，分支一般就用 if..else..语句，循环一般就 用 for 语句。 

##2.1 if 语句
来个写个无聊有 if...else...语句: 

Python shell 

```python
>>> if 2 > 3:
>>>   	print 2
>>> else: print 3 
```

如果 2 大于 3 打印 2，否则打印 3。果然很无聊，那么下面练习一个不是那么无聊的例子，多分支语 句。 

```python
xx.py 

results = 72 
if results >= 90: print u'优秀' 

elif results >= 70: print u'良好' 

elif results >= 60 : print u'及格' 

else: print u'不及格' 
```

根据分数划分成四个级别“优秀”、“良好”、“及格”、“不及格”，那么 72 分属于哪个级别， 练习一下吧。 



##2.2 for 语句 循环一个字符串中的每一个字符。 

```python
strings = "hello world"

for 1 in req strings:
		print 1

打印结果: 

\>>> ================================ RESTART ================================ >>> h e 

l l o 
w o r l d 

xx.py 

for i in range(1,10):

		print i  

循环数字，循环数字要借助 range()函数。 


打印结果: 

\>>> ================================ RESTART ================================ >>> 1 2 

3 4 5 6 7 8 9 


xx.py 

for i in range(1,10,2):

		print i

打印结果: 

\>>> ================================ RESTART ================================ >>> 1 3 

5 7 9   

如果我只想打印 1 到 10 之间的奇数: 

range(start，end，scan)

range()函数，start 表示开始位置，end 表示结束位置，scan 表示每一次循环的步长。 

```



## 3 数组与字典 

在我们的自动化脚本里除了字符串与数字外，用到最多的就是数组与字典了，所以，我们来熟悉一下 

这种数据存储的概念。 

##3.1 数组 
  数组用中括号([])表示，里面的每一个元素用逗号(,)隔开。 

Python shell 

```python
shuzu = [1,2,3,'a',5] 
print shuzu
[1, 2, 3, 'a', 5]
print shuzu[0] 
1
print shuzu[4]
5
```

需要注意的是，数组下标是从 0 开始的。 

##3.2 字典
字典以花括号({})表示，里面的元素是成对出现的，一个 key 对应一个 value;一对元素用冒号(:) 分割;不同对元素用逗号(,)分开。 

Python shell 

```python
	>>> zidian = {"username":"password",'man':'woman',1:2} 
	>>> zidian.keys()
	>>>   ['username', 1, 'man']

  >>> zidian.values() 

	['password', 2, 'woman']

  >>> zidian.items()
  >>>   [('username', 'password'), (1, 2), ('man', 'woman')] 
```

字典里的每一对元素准确的来说是键值对，一个键(key)对应一个值(value)。keys()函数可以输 出所有键的值;values()函数可以输出所有值的值;items()函数输出一对键值的值。  

##4 函数
  在 Python 当中通过 def 关键字来定义函数，下面来定义一个函数。 

Python shell 

```python
def add(a,b):
		print a+b
    
add(3,5)
8
```

创建一个 add()，这个函数接收两个参数 a,b，通过 print 打印 a+b 的结果。调用 add()函数，并且传 两个参数 3，5 给 add()函数。 

更多的情况下，add()函数不会直接打印结果，而是将处理结果通过 return 关键字返回。 

Python shell 

```python
def add(a,b):
	return a+b
add(3,5)
8
```

有时候我们在调用 add()函数的时候不想传参，那么可以为 add()函数设置默认参数。 

Python shell 

```python
def add(a=1,b=2):
  	return a+b
add()
3
add(3,5)
8
如果调用时不传参，那么 add()函数就使用默认参数进行计算。如果传参则计算参数的值。 
```

##5 类与方法 
在面向对象编程的世界里一切皆为对象，那么抽象的一组对象就是类。例如，汽车就是一个类，张三 

家的奇瑞汽车就是一个具体的对象。在 Python 中用 class 关键字来创建类。 

```python
xx.py 
class A():
  	def add(self,a,b):
				return a+b 
count = A()
print count.add(3,5)

打印结果: 

>>> ================================ RESTART ================================ >>> 
>>> 45 
```

创建了一个 A()类，在类下面创建了一个 add()方法。方法的创建同样使用关键字 def，维一不同的是 方法必须有一个且必须是第一个默认参数 self，但是这个参数不用传值。 

```python
xx.py 
class A:
  	def add(self,a,b):
				return a+b 

class B(A):
  	def sub(self,a,b):
				return a-b 

count = B()
print count.add(4,5)

打印结果: 

>>> ================================ RESTART ================================ >>>
>>> 8 
```

用 count 变量来等于 B 类，因为 B 类继承了 A 类，所以 B 类自然也拥有了 add()方法，所以 count 可 以调用 add()方法。 

当然，学到这里你会产生很多疑问，为什么要写类里面包含方法，用函数不是更简单么?还有那个 self 非要写出来，但看上去又没什么用。当然，类有很多特性，比如，上面所介绍的类的继承。 

##. 异常 

Python 用异常对象(exception object)来表示异常情况。遇到错误后，会引发异常。如果异常对象 并未被处理或捕捉，程序就会用所谓的 回溯(Traceback， 一种错误信息)终止执行。 

在实际的脚本开发中，有时间程序并不会像我们设计它时那样工作，它也有“生病”的时候，那么我 们可以通过异常处理机制，有预见性地获得这些病症，并开出药方。比如，对一个正常人，大冬天的洗冷 水澡，那么就有可能感冒，我们可以事先在洗冷水澡时准备好感冒药，假如真感冒了，就立刻吃药。 

3.6.1 认识异常 下面来看看程序在执行时所抛的异常。 

Python Shell 

```python
>>>print "hello", hello 
```

再来运行程序,因为我们用 except 接收了这个 IOError 错误。所以“异常了!”的信息会被打印出来。 假如我不是打开一个文件，而是输出一个没有定义的变量呢? 

abnormal.py 

```python
try:
  print aa 
except IOError:
  print "异常了!" 

打印结果: 

>>> ================================ RESTART ================================ >>> Traceback (most recent call last): 

File "F:\project\count.py", line 12, in <module> print aa 

NameError: name 'aa' is not defined 
```

不是已经通过 except 去接收异常了么?为什么错误又出现了，如果你细心查看错误信息会发现这一 次抛的是个 NameError 类型的错误，而我们的 except IOEerror 只能接收到 IO 类型的错误。这一次小明 

那么我们只需要换一个接收异常的类型就可以了。

abnormal.py 

```python
try:
  print aa 

except NameError:
  print "这是一个 name 异常!" 

打印结果: 

>>> ================================ RESTART ================================ >>>
>>>   这是一个 name 异常! 
```

 那么问题来了，我们一个操作怎么会抛出什么类型的错误呢?

知识延伸:

 异常的抛出机制:

1、如果在运行时发生异常，解释器会查找相应的处理语句(称为 handler). 2、要是在当前函数里没有找到的话，它会将异常传递给上层的调用函数，看看那里能不能处理。 3、如果在最外层(全局“main”)还是没有找到的话，解释器就会退出，同时打印出 traceback 以便 

让用户找到错误产生的原因。

 注意:虽然大多数错误会导致异常，但一个异常不一定代表错误，有时候它们只是一个警告，有时

候它们可能是一个终止信号，比如退出循环等。

在 Python 中所有的异常类都继承 Exception，所以我们可以使用它来接收所有的异常。 

abnormal.py 

```python
try:

  open("abc.txt",'r')

    print aa

except Exception:

print "异常了!" 

打印结果: 

\>>> ================================ RESTART ================================ >>>
异常了! 
```

从 Python2.5 版本之后，所有的异常类有了新的基类 BaseException，Exception 同样也继承 BaseException，所以我们也可以使用 BaseException 来接收所有的异常。 

abnormal.py 

```python
try: 
  open("abc.txt",'r')

    print aa

except BaseException: print "异常了!" 

打印结果: 

>>> ================================ RESTART ================================ >>>
>>>   异常了! 
```

那么对于上面例子，如果我在执行程序的当前目录下创建了 abc.txt，那么就不会报 IOError,如果定 义了 aa 变量，那么就不会报 NameError 错误。可问题是我自定义的 print 异常信息，并不能准确的告诉 是哪一行代码所引起的异常。那么何不让 Python 直接告诉我们呢。 

abnormal.py 

```python
try:

  open("abc.txt",'r')

    print aa

except BaseException,msg:

print msg 

打印结果: 

\>>> ================================ RESTART ================================ >>> [Errno 2] No such file or directory: 'abc.txt' 
```

我们在 BaseException 后面定义 msg 变量用于接收异常信息，通过 print 将其打印出来。 下面来认识一下 Python 中常见的异常:           

异常 

BaseException Exception AssertionError AttributeError IOError NameError IndexError IndentationError KeyboardInterrupt TypeError SyntaxError 

描述 

新的所有异常类的基类所有异常类的基类，但继承 BaseException 类assert 语句失败试图访问一个对象没有属性 输入输出异常，试图打一个不存的文件(包括其它情况)时引起 使用一个还未赋值对象的变量 在使用序列中不存在的所引进引发 语法错误，代码没有正确的对齐Ctrl+C 被按下，程序被强行终止传入的对象类型与要求不符Python 代码逻辑语法出错，不能执行 

import a,b 

project\count.py 

import sys

sys.path.append('\model')

from model import *

print pub.add(4,5)

现在我们用星号(*)表示导入 model 下面所有文件，这个所有具体包含什么由__init__.py 决定，因 为只 import 了 a 和 b 了。所以，在运行程序时会有下面的提示: 

Python Shell 

\>>> ================================ RESTART ================================ >>> Traceback (most recent call last): 

File "F:\project\count.py", line 5, in <module> print pub.add(4,5) 

NameError: name 'pub' is not defined 

##7 模组 

更通俗的讲叫包或模块，或统称为“头文件”，前面的练习中我们并没用到模块，但这也只是在练习 的时候，在实际的开发中我们不可能不用到系统所提供的方法，或第三方模块。如果，我们想实现与时间 有关功能那么就可以调用系统的 time 模块，如果我们想实现与文件和文件夹有关的操作，那么就要用到 os 模块。再比如我们通过极 selenium 实现的 web 自动化测试，那么 selenium 对于 Python 来说就是一个 模块。 

6.1 引用模块
  在 Python 语言中通过 from...import...的方式引用模块，下面引用 time 模块。 

```python
xx.py 
import time
print time.ctime()

打印结果: 

>>> ================================ RESTART ================================ >>>
>>> Tue Dec 09 22:35:57 2014 
```

在 time 模块下面有一个 ctime()方法获得当前时间，通过 print 将当前时间打印出来。当然，如果 我确定了只会用到 time 下面的 ctime()方法，那么可以这样: 

```python
xx.py 
from time import ctime 
print ctime()
打印结果: 

>>> ================================ RESTART ================================ >>>
>>>   Tue Dec 09 22:36:38 2014 
```

那么现在在使用的时候就不用告诉 Python ctime()方法是 time 模块所提供的了。但是有时候我们还 可能会用到 time 模块下面的 sleep()休眠方法;当然，我们还可以把 sleep()方法也导入进来。或许还会 用到其它方法呢，那么为什么不一次性把 time 模块下面的所有方法都引入进来呢。 

```python
xx.py 

#coding=utf-8

  from time import * 

print ctime() print "休息一两秒" sleep(2) print ctime() 

打印结果: 

\>>> ================================ RESTART ================================ >>> Tue Dec 09 22:47:35 2014
  休息一两秒 

Tue Dec 09 22:47:37 2014
```

星号“*”用于表示模块下面的所有方法。那么你一定很好奇，time 到底在哪儿?为什么 import 进来 就可以用了。这是 Python 语言所提供的核心方法，而且已经经过了编译，所以我们无法看到 ctime 到底 是如何实现的可以取到系统的当前时间，但是我们可以看到 Python 所安装的第三方模块。比如我们做自 动化所用到的 selenium 模块。 

学习安装了 selenium，那么你一定会在这个目录下找到 selenium 目录。 

6.2 模块调用 

下一个你所关心的问题，既然可调用系统模块，那么我可不可以自己创建一个模块，然后通过另一个 程序调用，当然是可以的，有谁见过一个软件项目是只有一个文件，它们一定是有结构地分散在不同的目 录和文件中。 

下面创建一个目录(project)，在目录下创建一个文件(pub.py),在文件中创建一个函数。 

```python
project\pub.py 

def add(a,b):
				print a+b

在相同的目录下再创建一个文件(count.py) 

project\count.py 
import pub
print pub.add(4,5)

打印结果: 

>>> ================================ RESTART ================================ >>>
9 
```


这样就实现了跨文件的函数调用。
           

知识延伸:如果你细心一定会发现在 project 目录下多了一个 pub.pyc 文件，那么这个.pyc 是什么?
pyc 是一种二进制文件，是由 py 文件经过编译后，生成的文件，是一种 byte code，py 文件变成 pyc 

文件后，加载的速度有所提高，而且 pyc 是一种跨平台的字节码，是由 Python 的虚拟机来执行的。 

6.3 跨目录模块调用 

现在的情况是 pub.py 和 count.py 两个文件同在一个目录下面，可以非常非常方便的调用。那么如果 被调用的文件与调用文件不在同一目录下面呢?调用文件目录如下: 

----project/model/pub.py----project/count.py

注意删除刚才调用时所生成的 pub.pyc 文件。

再来执行 count.py 文件 

```python
project\count.py 

import pub 

print pub.add(4,5)

打印结果: 

\>>> ================================ RESTART ================================ >>> 

Traceback (most recent call last):
  File "F:\project\count.py", line 1, in <module> 

import pub
  ImportError: No module named pub 
```

现在 Python 告诉我们，它找不到 pub 模块。那么 Python 是如何找模块的呢? 


知识延伸:
  要弄明白这个问题，首先要知道，Python 在执行 import 语句时，到底进行了什么操作，按照 Python的文档，它执行了如下操作:
  第 1 步，创建一个新的，空的 module 对象(它可能包含多个 module);
  第 2 步，把这个 module 对象插入 sys.module 中
  第 3 步，装载 module 的代码(如果需要，首先必须编译)
  第 4 步，执行新的 module 中对应的代码。
  在执行第 3 步时，首先要找到 module 程序所在的位置，搜索的顺序是: 当前路径 (以及从当前目录指定的 sys.path)，然后是 PythonPATH，然后是 Python 的安装设置相 

关的默认路径。正因为存在这样的顺序，如果当前路径或 PythonPATH 中存在与标准 module 同样的 module，则会覆盖标准 module。也就是说，如果当前目录下存在 xml.py，那么执行 import xml 时，导 入的是当前目录下的 module，而不是系统标准的 xml。 

了解了这些，我们就可以先构建一个 package，以普通 module 的方式导入，就可以直接访问此 package 中的各个 module 了。Python 中的 package 必须包含一个__init__.py 的文件。 

那么现在，我们就知道如何让 count.py 找到 pub.py 文件了，可以将...project/model/目录添加到 系统环境变量的 Path 下面，当然，这样做的确定是不够灵活。更灵活的方式是调用 Python 的 sys 模块来 实现。 

project\count.py 

```python
import sys

sys.path.append('\model')

from model import pub

print pub.add(4,5)
```

调用 sys 模块，把 model 目录通过 append()方法追加到系统环境变量 Path 下面。append()是一个非 常有用的方法，它通常用于向一个数据或集合尾部添加新的数据。注意“\model”是一个相对路径，如果 pub.py 在别的目录下面，那么就要用绝对路径了，如:append('D:\\project\\model')。 

现在来运行程序依然会告诉我们找不到 model,我们还需要在 model 目录下面创建一个__init__.py 文 件，内容可以为空。这个文件告诉 Python model 是可以被调用的一个模块。好了，现在可以正常运行 count.py 程序了。 

那么我们可以在__init__.py 目录下面放点什么呢?例如在 model 目录下有两三个文件(a.py、b.py、 c.py)打开__init__.py 文件: 



## 文件读写

程序运行时所产生的数据，是存储在内存里面的。当我们终止程序或者计算机被关机时，内存就被会清空，数据就被全部丢失。我们需要把有用的数据从内存迁移到磁盘等永久存储设备，`文件读写`就是一种迁移方式。

在`Python`中，文件的读写操作，由`open`这个内置模块实现。

------

## 读文件

```
r
>>> f = open('filename','r')
>>> f
<_io.TextIOWrapper name='main.py' mode='r' encoding='UTF-8'> # 文件对象

>>> f.read() # 读取所以内容
>>> f.read(size) # 读取指定内容
>>> f.readline() # 读取一行，并且把指针指向下一行
>>> f.readlines() # 以行为单位分割成一个列表
>>> f.close() # 关闭文件对象，释放资源

# readline 遍历
>>> while True:
>>>  line = f.readline()
>>>  if line:
>>>   print(line)
>>>  else:
>>>   break
>>> f.close()
'line1'
'line2'
'line3'
...

# readlines 遍历
>>> for line in f.readlines():
>>>  line.strip() # strip 字符串方法，去除两边空格 \n 换行符等..
>>> f.close()
'line1'
'line2'
'line3'
...
```

------

## 写文件

```
w
f = open('filename', 'w')
f.write('hello!')
f.close()

# 读文件时，如果文件不存在，会报错。而写文件时，如果文件不存在则创建它。
a
f = open('filename', 'a') # w 清空文件写入，a 追加到文件末尾写入
```

------

`r`只读，`w、a`只写，如果想要既可以读，又可以写，可以使用`r+、w+、a+`等模式。

------

## with

```
上下文管理器
>>> with open('filename', 'r') as f:
>>>  f.read()

# with 中代码块的内容执行完毕，自动调用 f.close() 释放资源
```

with 的实现，参考 - [上下文管理器](https://www.jmjc.tech/tutorial/python/sub-2)

------

## 字符编码

```
encoding
# open 默认针对文件内容解析的编码的 utf-8，我们可以自己指定编码
# ignore 忽略编码报错，即使乱码也强制读取

f = open('filename', 'r', encoding='gbk', errors='ignore')  
```

参考 - [字符编码](https://www.jmjc.tech/tutorial/python/sub-1)

------

## 二进制

```
rb、wb
# 读取图片、视频等非文本对象、需要用二进制读取

f = open('filename', 'rb') # wb 写入 byte 数据
f.read()
b'\0x1'
```

## OS 模块

`OS 模块`是跟`操作系统交互`的一个内置模块。比如获取操作系统名称，环境变量，新建一个目录，删除文件等类似操作。这个模块提供的能力，加上Python优秀的语法和类库，使得Python能具备`shell脚本`的`自动化运维`能力。

------

## 系统

```
# 平台
>>> os.name
'nt' # windows 操作系统
'posix' # 类 unix 操作系统

# 信息
>>> os.uname() # 类 unix 有效
"posix.uname_result(sysname='Darwin', nodename='jasondeMacBook.local', release='17.3.0', version='Darwin Kernel Version 17.3.0: Thu Nov  9 18:09:22 PST 2017; root:xnu-4570.31.3~1/RELEASE_X86_64', machine='x86_64')"

# 执行 shell 命令
>>> os.system('ls') # Linux
>>> os.system('cmd') # windows

# 环境变量
>>> os.environ
environ({........})

>>> os.environ.get('PATH')
'/Users/jason/Desktop/env3/bin:/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin:/Users/jason/Library/Android/sdk/tools:/Users/jason/Library/Android/sdk/platform-tools'
```

------

## 目录文件

```
# 当前路径
os.getcwd() 

# 列出当前目录
os.listdit(.) 

# 创建目录
os.mkdir('path') 

# 删除目录
os.rmdir('path') 

# 重命名文件
os.rename('a', 'b') 

# 删除文件
os.remove('a') 

# 文件复制 import shutil
shutil.copy('a', 'b') 

# 路径分割
os.path.split('path') 

# 文件扩展名
os.path.splitext('path') 

# 文件是否存在
os.path.exists('path') 

# 是否目录
os.path.isdir('path') 

# 是否文件
os.path.isfile('path') 

 # 修改时间
os.path.getmtime('path')

# 访问时间
os.path.getatime('path') 

# 创建时间
os.path.getctime('path') 

# 文件大小
os.path.getsize('path')
```



## 时间

计算机的时间记录从`1970年1月1日`开始，以每秒+1的速度持续累积。在我写这篇文章的时候，这个数字累积的值是 `1527669339`，我们把这个数字称为`Unix时间戳`。

------

## 时间戳

```
>>> import time
>>> time.time() # 当前日期的时间戳
>>> time.mktime(time.strptime('2017-8-13 00:00:00', '%Y-%m-%d %H:%M:%S')) # 自定义日期的时间戳
```

------

## 时间运算

```
>>> time.time() + (60 * 60 * 24) # + 1天
>>> time.time()  - (60 * 60 * 24 * 3) # - 3 天
```



## 摘要算法

摘要算法是`单向加密`的，也就是说你的`明文`通过摘要算法加密之后，是不能解密的。摘要算法的第二个特点密文是`固定长度`的，无论你的明文长度多少，加密之后都是一样的长度。之所以叫摘要算法，它算法的就是通过提取明文`重要的特征`。所以，两个不同的明文，使用了摘要算法之后，有可能出现他们的密文的一样，不过这个概率非常的低。

------

## md5

md5 是常见的摘要算法，不过现在单纯的 md5 加密已经很不安全，黑客通过 `撞库` 的方式，常见密码的 md5 值很容易就能查询得到。

```
>>> import hashlib
>>> md5 = hashlib.md5()
>>> md5.update('date'.encode('utf-8'))
>>> md5.hexdigest()

'ce5f6cc34fbf471fd55d186da4833805' # 得到了这串 32 位的字符，就是 'date' 的密文
```

------

## sha1

sha1 是比 md5 更安全一点的摘要，md5 的密文是 `32` 位，而 sha1 是 `40` 位，sha1 的升级版还有`sha256`和 `sha512`，版本越强密文越长，代价是速度越慢。

```
>>> import hashlib
>>> sha1 = hashlib.sha1()
>>> sha1.update('date'.encode('utf-8'))
>>> sha1.hexdigest()

'e927d0677c77241b707442314346326278051dd6' # 用法和 md5 一样
```



## base64

base64 其实不能归属密码领域，作用也不是用于加密，它是一种`编码算法`。数据要在操作系统上`显示`或者`传输`，数据的格式就必须符合操作系统的`字符集`，参考 - [Python 字符编码](https://www.jmjc.tech/tutorial/python/sub-1)。我们通过记事本打开一张图片，一整片的乱码。那是因为图片是`二进制`的格式，它既不是`ASCII 字符集`，也不是`unicode 字符集`，操作系统无法理解，所有不能正常显示，也不能转换成 `utf-8` 传输。`base64` 的用途就在这，它基于一套规则算法，把二进制的数据转换成字符串，让我们能显示或者传输二进制的数据。

```
# 编码
>>> base64.b64encode(b'/x01') # 想象它是一张图片，编码成 base64 之后，就能进行传输
b'L3gwMQ=='

# 解码
>>> base64.b64decode(b'L3gwMQ==') # 传输成功之后，在把解码回来变成一张图片
b'/x01'
```



## re模块

Python对`正则表达式`的支持，由`re`这个内置的模块实现。

------

## findall

以列表的形式返回匹配成功的文本。

```
>>> import re
>>> re.findall('a', 'a') # ['a']
>>> re.findall('a', 'aba') # ['a', 'a']
>>> re.findall('.', 'aba') # ['aba']
>>> re.findall('a{3}', 'aaaa') #['aaa']
>>> re.findall('\d\D', '1aa') # ['1a']
>>> re.findall('^a', 'ba') # []

# 参数（匹配规则，字符）
# 上篇我们介绍的语法，我们可以自己逐个试验，加深理解
```

------

## match

`match`匹配成功返回正则对象，失败返回`None`。

```
>>> r = re.match('a', 'aba')
>>> r
<_sre.SRE_Match object; span=(0, 1), match='a'>

>>> r = re.match('a', 'b')
>>> r is None
True
```

------

## search

`match`强制开头匹配，`search`的功能和`match`一样，但不强制开头匹配。

```
>>> r = re.match('a', 'ba')
>>> r is None
True

>>> r = re.search('a', 'ba')
>>> r
<_sre.SRE_Match object; span=(1, 2), match='a'>

>>> r = re.search('^a', 'ba') # ^ 开头匹配 | 这时 match 和 search 就一样了
```

------

## group

从`match`返回的正则对象`提取结果`。

```
>>> re.match('a(b)','ab').group() # () 括号是特别的标示，不会影响正则匹配
'ab'

>>> re.match('a(b)','ab').groups() # .groups() 可以只提取用括号标示的内容，这招非常有用！
'b'
```

------

## compile

```
预编译
>>> re.compile('\d')
>>> d.match('1').group()
1
>>> d.match('2').group()
2

# match 每次匹配都要编译一遍，如果一个正则表达式需要多次匹配，使用 compile 都执行效率会高些
```

------

对正则表达式的加深理解，可以在网上找些应用的例子，或者参考一下这本书 [正则表达式必知必会](https://book.douban.com/subject/2269648/)。