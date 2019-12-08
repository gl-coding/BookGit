# 并发

##进程

　　进程（Process）是计算机中的是系统进行资源分配和调度的基本单位，是[操作系统](http://baike.baidu.com/view/880.htm)结构的基础。进程是一个具有独立功能的程序关于某个数据集合的一次运行活动。它可以申请和拥有系统资源，是一个动态的概念，是一个活动的实体。它不只是程序的[代码](http://baike.baidu.com/view/41.htm)，还包括当前的活动，通过[程序计数器](http://baike.baidu.com/view/178145.htm)的值和处理[寄存器](http://baike.baidu.com/view/6159.htm)的内容来表示。

　　进程的概念主要有两点：第一，进程是一个实体。每一个进程都有它自己的地址空间，一般情况下，包括[文本](http://baike.baidu.com/view/300107.htm)区域（text region）、数据区域（data region）和[堆栈](http://baike.baidu.com/view/93201.htm)（stack region）。文本区域存储处理器执行的代码；数据区域存储变量和进程执行期间使用的动态分配的内存；堆栈区域存储着活动过程调用的指令和本地变量。第二，进程是一个“执行中的程序”。程序是一个没有生命的实体，只有[处理](http://baike.baidu.com/view/989420.htm)器赋予程序生命时（操作系统执行之），它才能成为一个活动的实体，我们称其为[进程](http://baike.baidu.com/view/19746.htm)。

**阅读目录**

- [1. Process](http://www.cnblogs.com/kaituorensheng/p/4445418.html#_label0)
- [2. Lock](http://www.cnblogs.com/kaituorensheng/p/4445418.html#_label1)
- [3. Semaphore](http://www.cnblogs.com/kaituorensheng/p/4445418.html#_label2)
- [4. Event](http://www.cnblogs.com/kaituorensheng/p/4445418.html#_label3)
- [5. Queue](http://www.cnblogs.com/kaituorensheng/p/4445418.html#_label4)
- [6. Pipe](http://www.cnblogs.com/kaituorensheng/p/4445418.html#_label5)
- [7. Pool](http://www.cnblogs.com/kaituorensheng/p/4445418.html#_label6)

**序. multiprocessing**
python中的多线程其实并不是真正的多线程，如果想要充分地使用多核CPU的资源，在python中大部分情况需要使用多进程。Python提供了非常好用的多进程包multiprocessing，只需要定义一个函数，Python会完成其他所有事情。借助这个包，可以轻松完成从单进程到**并发执行**的转换。multiprocessing支持子进程、通信和共享数据、执行不同形式的同步，提供了Process、Queue、Pipe、Lock等组件。

### 1. Process

**创建进程的类**：Process([group [, target [, name [, args [, kwargs]]]]])，target表示调用对象，args表示调用对象的位置参数元组。kwargs表示调用对象的字典。name为别名。group实质上不使用。
**方法**：is_alive() 、join([timeout])、run()、start()、terminate()。其中，Process以start()启动某个进程。

is_alive()：判断该进程是否还活着

join([timeout])：主进程阻塞，等待子进程的退出， join方法要在close或terminate之后使用。

run():进程p调用start()时，自动调用run()

 

**属性**：authkey、daemon（要通过start()设置）、exitcode(进程在运行时为None、如果为–N，表示被信号N结束）、name、pid。其中daemon是父进程终止后自动终止，且自己不能产生新进程，必须在start()之前设置。

 

**例1.1：创建函数并将其作为单个进程**

```
import multiprocessing
import time

def worker(interval):
    n = 5
    while n > 0:
        print("The time is {0}".format(time.ctime()))  #输出时间的格式
        time.sleep(interval)
        n -= 1

if __name__ == "__main__":
    p = multiprocessing.Process(target = worker, args = (3,))
    p.start()
    print "p.pid:", p.pid
    print "p.name:", p.name
    print "p.is_alive:", p.is_alive()
```

结果

```
`p.pid: ``8736``p.name: Process``-1``p.is_alive: True``The time is Tue Apr ``21` `20:``55:``12` `2015``The time is Tue Apr ``21` `20:``55:``15` `2015``The time is Tue Apr ``21` `20:``55:``18` `2015``The time is Tue Apr ``21` `20:``55:``21` `2015``The time is Tue Apr ``21` `20:``55:``24` `2015`
```

 

**例1.2：创建函数并将其作为多个进程**

```
import multiprocessing
import time

def worker_1(interval):
    print "worker_1"
    time.sleep(interval)
    print "end worker_1"

def worker_2(interval):
    print "worker_2"
    time.sleep(interval)
    print "end worker_2"

def worker_3(interval):
    print "worker_3"
    time.sleep(interval)
    print "end worker_3"

if __name__ == "__main__":
　　p1 = Process(target=worker_1, args=(6,))
   p2 = Process(target=worker_2, args=(4,))
    p3 = Process(target=worker_3, args=(2,))
　　p1.start() p2.start() p3.start()
　　print("The number of CPU is:" + str(cpu_count()))
  　　　for p in active_children():
      　　　print("child p.name:=%s" % p.name + "\tp.id=%s" % str(p.pid))
    　　print(p1.pid)
    　　print("END-----")
```

**例1.3：将进程定义为类**

```
import multiprocessing
import time

class ClockProcess(multiprocessing.Process):
    def __init__(self, interval):
        multiprocessing.Process.__init__(self)
        self.interval = interval

    def run(self):
        n = 5
        while n > 0:
            print("the time is {0}".format(time.ctime()))
            time.sleep(self.interval)
            n -= 1

if __name__ == '__main__':
    p = ClockProcess(3)
    p.start()      
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

**注**：进程p调用start()时，自动调用run()

结果

```
`the time is Tue Apr ``21` `20:``31:``30` `2015``the time is Tue Apr ``21` `20:``31:``33` `2015``the time is Tue Apr ``21` `20:``31:``36` `2015``the time is Tue Apr ``21` `20:``31:``39` `2015``the time is Tue Apr ``21` `20:``31:``42` `2015`
```

 

**例1.4：daemon程序对比结果**

**#1.4-1** 不加daemon属性

```
import multiprocessing
import time

def worker(interval):
    print("work start:{0}".format(time.ctime()));
    time.sleep(interval)
    print("work end:{0}".format(time.ctime()));

if __name__ == "__main__":
    p = multiprocessing.Process(target = worker, args = (3,))
    p.start()
    print "end!"
```

结果

```
`end!``work start:Tue Apr ``21` `21:``29:``10` `2015``work end:Tue Apr ``21` `21:``29:``13` `2015`
```

**#1.4-2** 加上daemon属性

```
import multiprocessing
import time

def worker(interval):
    print("work start:{0}".format(time.ctime()));
    time.sleep(interval)
    print("work end:{0}".format(time.ctime()));

if __name__ == "__main__":
    p = multiprocessing.Process(target = worker, args = (3,))
    p.daemon = True
    p.start()
    print "end!"
```

结果

```
`end!`
```

**注**：因子进程设置了daemon属性，主进程结束，它们就随着结束了。

　　在多线程模型中，默认情况下（sub-Thread.daemon=False)主线程会等待子线程退出后再退出，而如果sub- Thread.setDaemon(True)时，主线程不会等待子线程，直接退出，而此时子线程会随着主线程的对出而退出，避免这种情况，主线程中需要 对子线程进行join，等待子线程执行完毕后再退出。对应的，在多进程模型中，Process类也有daemon属性，而它表示的含义与 Thread.daemon类似，当设置sub-Process.daemon=True时，主进程中需要对子进程进行等待，否则子进程会随着主进程的退 出而退出

**更详细：http://www.tuicool.com/articles/zii6bm**

**#1.4-3** 设置daemon执行完结束的方法

```
import multiprocessing
import time

def worker(interval):
    print("work start:{0}".format(time.ctime()));
    time.sleep(interval)
    print("work end:{0}".format(time.ctime()));

if __name__ == "__main__":
    p = multiprocessing.Process(target = worker, args = (3,))
    p.daemon = True
    p.start()
    p.join()
    print "end!"
```

结果

```
`work start:Tue Apr ``21` `22:``16:``32` `2015``work end:Tue Apr ``21` `22:``16:``35` `2015``end!`
```

### 2. Lock

当多个进程需要访问共享资源的时候，Lock可以用来避免访问的冲突。

```
import multiprocessing
import sys

def worker_with(lock, f):
    with lock:
        fs = open(f, 'a+')
        n = 10
        while n > 1:
            fs.write("Lockd acquired via with\n")
            n -= 1
        fs.close()
        
def worker_no_with(lock, f):
    lock.acquire()
    try:
        fs = open(f, 'a+')
        n = 10
        while n > 1:
            fs.write("Lock acquired directly\n")
            n -= 1
        fs.close()
    finally:
        lock.release()
    
if __name__ == "__main__":
    lock = multiprocessing.Lock()
    f = "file.txt"
    w = multiprocessing.Process(target = worker_with, args=(lock, f))
    nw = multiprocessing.Process(target = worker_no_with, args=(lock, f))
    w.start()
    nw.start()
    print "end"
```

结果（输出文件）

```
`Lockd acquired via with``Lockd acquired via with``Lockd acquired via with``Lockd acquired via with``Lockd acquired via with``Lockd acquired via with``Lockd acquired via with``Lockd acquired via with``Lockd acquired via with``Lock acquired directly``Lock acquired directly``Lock acquired directly``Lock acquired directly``Lock acquired directly``Lock acquired directly``Lock acquired directly``Lock acquired directly``Lock acquired directly`
```

### 3. Semaphore

Semaphore用来控制对共享资源的访问数量，例如池的最大连接数。

```
import multiprocessing
import time

def worker(s, i):
    s.acquire()
    print(multiprocessing.current_process().name + "acquire");
    time.sleep(i)
    print(multiprocessing.current_process().name + "release\n");
    s.release()

if __name__ == "__main__":
    s = multiprocessing.Semaphore(2)
    for i in range(5):
        p = multiprocessing.Process(target = worker, args=(s, i*2))
        p.start()
```

结果

```
`Process``-1``acquire``Process``-1``release` `Process``-2``acquire``Process``-3``acquire``Process``-2``release` `Process``-5``acquire``Process``-3``release` `Process``-4``acquire``Process``-5``release` `Process``-4``release`
```

例子2：

```
import multiprocessing
import time


def worker(s, ):
    s.acquire()
    print(multiprocessing.current_process().name + "acquire")
    time.sleep(1)
    # print(multiprocessing.current_process().name + "release\n")
    s.release()

if __name__ == "__main__":
    s = multiprocessing.Semaphore(2)
    for i in range(5):
        p = multiprocessing.Process(target = worker, args=(s, ))
        # time.sleep(0.01)
        p.start()
#####结果######
```

Process-4acquire
Process-3acquire


Process-1acquire
Process-2acquire

Process-5acquire



### 4. Event

Event用来实现进程间同步通信。

```
import multiprocessing
import time

def wait_for_event(e):
    print("wait_for_event: starting")
    e.wait()　#一直阻塞的去等待set值
    print('*****')
    print("wairt_for_event: e.is_set()->" + str(e.is_set()))

def wait_for_event_timeout(e, t):
    print("wait_for_event_timeout:starting")
    e.wait(2)  #等2s去取set值
    print('------')
    print("wait_for_event_timeout:e.is_set->" + str(e.is_set()))

if __name__ == "__main__":
    e = multiprocessing.Event()
    # e.set()
    w1 = multiprocessing.Process(name="block", target=wait_for_event, args=(e,))
    w2 = multiprocessing.Process(name="non-block", target=wait_for_event_timeout, args=(e, 2))
    w1.start()
    w2.start()
    time.sleep(10)
    e.set()        # 设置set的值
    print("main: event is set")
```

结果

### 5. Queue

Queue是多进程安全的队列，可以使用Queue实现多进程之间的数据传递。put方法用以插入数据到队列中，put方法还有两个可选参数：blocked和timeout。如果blocked为True（默认值），并且timeout为正值，该方法会阻塞timeout指定的时间，直到该队列有剩余的空间。如果超时，会抛出Queue.Full异常。如果blocked为False，但该Queue已满，会立即抛出Queue.Full异常。

get方法可以从队列读取并且删除一个元素。同样，get方法有两个可选参数：blocked和timeout。如果blocked为True（默认值），并且timeout为正值，那么在等待时间内没有取到任何元素，会抛出Queue.Empty异常。如果blocked为False，有两种情况存在，如果Queue有一个值可用，则立即返回该值，否则，如果队列为空，则立即抛出Queue.Empty异常。Queue的一段示例代码：

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
import multiprocessing

def writer_proc(q):      
    try:         
        q.put(1, block = False) 
    except:         
        pass   

def reader_proc(q):      
    try:         
        print q.get(block = False) 
    except:         
        pass

if __name__ == "__main__":
    q = multiprocessing.Queue()
    writer = multiprocessing.Process(target=writer_proc, args=(q,))  
    writer.start()   

    reader = multiprocessing.Process(target=reader_proc, args=(q,))  
    reader.start()  

    #reader.join()   这样会一直阻塞
    #writer.join()
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

结果

```
`1`
```

 

[回到顶部](http://www.cnblogs.com/kaituorensheng/p/4445418.html#_labelTop)

### **6. Pipe**

Pipe方法返回(conn1, conn2)代表一个管道的两个端。Pipe方法有duplex参数，如果duplex参数为True(默认值)，那么这个管道是全双工模式，也就是说conn1和conn2均可收发。duplex为False，conn1只负责接受消息，conn2只负责发送消息。

 

send和recv方法分别是发送和接受消息的方法。例如，在全双工模式下，可以调用conn1.send发送消息，conn1.recv接收消息。如果没有消息可接收，recv方法会一直阻塞。如果管道已经被关闭，那么recv方法会抛出EOFError。

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
import multiprocessing
import time

def proc1(pipe):
    # while True:
    for i in range(3):
        print("send: %s" %(i))
        pipe.send(i)
        time.sleep(1)


def proc2(pipe):
    while True:
        print ("proc2 rev:", pipe.recv())
        time.sleep(1)

def proc3(pipe):
    while True:
        print("PROC3 rev:", pipe.recv())
        time.sleep(1)

if __name__ == "__main__":
    pipe = multiprocessing.Pipe()
    p1 = multiprocessing.Process(target=proc1, args=(pipe[0],))
    p2 = multiprocessing.Process(target=proc2, args=(pipe[1],))
    #p3 = multiprocessing.Process(target=proc3, args=(pipe[1],))

    p1.start()
    p2.start()
    # p3.start()

    # p1.join()
    # p2.join()
    # p3.join()
#######结果########
```

send: 0
proc2 rev: 0
send: 1
proc2 rev: 1
send: 2
proc2 rev: 2

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

结果

![img](https://images0.cnblogs.com/blog2015/408927/201504/301445185683314.png)

 

[回到顶部](http://www.cnblogs.com/kaituorensheng/p/4445418.html#_labelTop)

### 7. Pool

在利用Python进行系统管理的时候，特别是同时操作多个文件目录，或者远程控制多台主机，并行操作可以节约大量的时间。当被操作对象数目不大时，可以直接利用multiprocessing中的Process动态成生多个进程，十几个还好，但如果是上百个，上千个目标，手动的去限制进程数量却又太过繁琐，此时可以发挥进程池的功效。
Pool可以提供指定数量的进程，供用户调用，当有新的请求提交到pool中时，如果池还没有满，那么就会创建一个新的进程用来执行该请求；但如果池中的进程数已经达到规定最大值，那么该请求就会等待，直到池中有进程结束，才会创建新的进程来它。

 例子：

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
import multiprocessing
import time


def func(msg, a):
    # if a == 1:
    #     time.sleep(8)
    #     print(1)
    print("msg:", msg)

    print("++++")
    time.sleep(3)
    # print("end")

if __name__ == "__main__":
    pool = multiprocessing.Pool(processes=3)
    for i in range(7):
        msg = "hello %d" % (i)
        a = i
        # 维持执行的进程总数为processes，当一个进程执行完毕后会添加新的进程进去
        pool.apply_async(func, (msg, a, ))
    pool.close()

    # 调用join之前，先调用close函数，否则会出错。执行完close后不会有新的进程加入到pool,join函数等待所有子进程结束
    pool.join()
    print("Sub-process(es) done.")
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

**例7.1：使用进程池（非阻塞）**

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
#coding: utf-8
import multiprocessing
import time

def func(msg):
    print "msg:", msg
    time.sleep(3)
    print "end"

if __name__ == "__main__":
    pool = multiprocessing.Pool(processes = 3)
    for i in xrange(4):
        msg = "hello %d" %(i)
        pool.apply_async(func, (msg, ))   #维持执行的进程总数为processes，当一个进程执行完毕后会添加新的进程进去

    print "Mark~ Mark~ Mark~~~~~~~~~~~~~~~~~~~~~~"
    pool.close()
    pool.join()   #调用join之前，先调用close函数，否则会出错。执行完close后不会有新的进程加入到pool,join函数等待所有子进程结束
    print "Sub-process(es) done."
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

一次执行结果

```
`mMsg: hark~ Mark~ Mark~~~~~~~~~~~~~~~~~~~~~~ello ``0` `msg: hello ``1``msg: hello ``2``end``msg: hello ``3``end``end``end``Sub-process(es) done.`
```

函数解释：

- apply_async(func[, args[, kwds[, callback]]]) 它是**非阻塞**，apply(func[, args[, kwds]])是**阻塞**的（理解区别，看例1例2结果区别）
- close()   关闭pool，使其不在接受新的任务。
- terminate()   结束工作进程，不在处理未完成的任务。
- join()   主进程阻塞，等待子进程的退出， join方法要在close或terminate之后使用。

执行说明：创建一个进程池pool，并设定进程的数量为3，xrange(4)会相继产生四个对象[0, 1, 2, 4]，四个对象被提交到pool中，因pool指定进程数为3，所以0、1、2会直接送到进程中执行，当其中一个执行完事后才空出一个进程处理对象3，所以会出现输出“msg: hello 3”出现在"end"后。因为为非阻塞，主函数会自己执行自个的，不搭理进程的执行，所以运行完for循环后直接输出“mMsg: hark~ Mark~ Mark~~~~~~~~~~~~~~~~~~~~~~”，主程序在pool.join（）处等待各个进程的结束。

 

**例7.2：使用进程池（阻塞）**

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
#coding: utf-8
import multiprocessing
import time

def func(msg):
    print "msg:", msg
    time.sleep(3)
    print "end"

if __name__ == "__main__":
    pool = multiprocessing.Pool(processes = 3)
    for i in xrange(4):
        msg = "hello %d" %(i)
        pool.apply(func, (msg, ))   #维持执行的进程总数为processes，当一个进程执行完毕后会添加新的进程进去

    print "Mark~ Mark~ Mark~~~~~~~~~~~~~~~~~~~~~~"
    pool.close()
    pool.join()   #调用join之前，先调用close函数，否则会出错。执行完close后不会有新的进程加入到pool,join函数等待所有子进程结束
    print "Sub-process(es) done."
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

一次执行的结果

```
`msg: hello ``0``end``msg: hello ``1``end``msg: hello ``2``end``msg: hello ``3``end``Mark~ Mark~ Mark~~~~~~~~~~~~~~~~~~~~~~``Sub-process(es) done.`
```

　　

**例7.3：使用进程池，并关注结果**

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
import multiprocessing
import time

def func(msg):
    print "msg:", msg
    time.sleep(3)
    print "end"
    return "done" + msg

if __name__ == "__main__":
    pool = multiprocessing.Pool(processes=4)
    result = []
    for i in xrange(3):
        msg = "hello %d" %(i)
        result.append(pool.apply_async(func, (msg, )))
    pool.close()
    pool.join()
    for res in result:
        print ":::", res.get()
    print "Sub-process(es) done."
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

一次执行结果

```
`msg: hello ``0``msg: hello ``1``msg: hello ``2``end``end``end``::: donehello ``0``::: donehello ``1``::: donehello ``2``Sub-process(es) done.`
```

 

**例7.4：使用多个进程池**

![img](https://images.cnblogs.com/OutliningIndicators/ContractedBlock.gif) View Code

 

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
#coding: utf-8
import multiprocessing
import os, time, random

def Lee():
    print "\nRun task Lee-%s" %(os.getpid()) #os.getpid()获取当前的进程的ID
    start = time.time()
    time.sleep(random.random() * 10) #random.random()随机生成0-1之间的小数
    end = time.time()
    print 'Task Lee, runs %0.2f seconds.' %(end - start)

def Marlon():
    print "\nRun task Marlon-%s" %(os.getpid())
    start = time.time()
    time.sleep(random.random() * 40)
    end=time.time()
    print 'Task Marlon runs %0.2f seconds.' %(end - start)

def Allen():
    print "\nRun task Allen-%s" %(os.getpid())
    start = time.time()
    time.sleep(random.random() * 30)
    end = time.time()
    print 'Task Allen runs %0.2f seconds.' %(end - start)

def Frank():
    print "\nRun task Frank-%s" %(os.getpid())
    start = time.time()
    time.sleep(random.random() * 20)
    end = time.time()
    print 'Task Frank runs %0.2f seconds.' %(end - start)
        
if __name__=='__main__':
    function_list=  [Lee, Marlon, Allen, Frank] 
    print "parent process %s" %(os.getpid())

    pool=multiprocessing.Pool(4)
    for func in function_list:
        pool.apply_async(func)     #Pool执行函数，apply执行函数,当有一个进程执行完毕后，会添加一个新的进程到pool中

    print 'Waiting for all subprocesses done...'
    pool.close()
    pool.join()    #调用join之前，一定要先调用close() 函数，否则会出错, close()执行后不会有新的进程加入到pool,join函数等待素有子进程结束
    print 'All subprocesses done.'
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

一次执行结果

```
`parent process ``7704` `Waiting for ``all` `subprocesses done...``Run task Lee``-6948` `Run task Marlon``-2896` `Run task Allen``-7304` `Run task Frank``-3052``Task Lee, runs ``1.59` `seconds.``Task Marlon runs ``8.48` `seconds.``Task Frank runs ``15.68` `seconds.``Task Allen runs ``18.08` `seconds.``All subprocesses done.`
```

#　　2、线程

　　线程，有时被称为轻量级进程(Lightweight Process，LWP），是程序执行流的最小单元。一个标准的线程由线程ID，当前指令[指针](http://baike.baidu.com/view/159417.htm)(PC），[寄存器](http://baike.baidu.com/view/6159.htm)集合和[堆栈](http://baike.baidu.com/view/93201.htm)组 成。另外，线程是进程中的一个实体，是被系统独立调度和分派的基本单位，线程自己不拥有系统资源，只拥有一点儿在运行中必不可少的资源，但它可与同属一个 进程的其它线程共享进程所拥有的全部资源。一个线程可以创建和撤消另一个线程，同一进程中的多个线程之间可以并发执行。由于线程之间的相互制约，致使线程 在运行中呈现出间断性。线程也有[就绪](http://baike.baidu.com/view/654230.htm)、[阻塞](http://baike.baidu.com/view/497285.htm)和[运行](http://baike.baidu.com/view/1026025.htm)三种基本状态。就绪状态是指线程具备运行的所有条件，逻辑上可以运行，在等待处理机；运行状态是指线程占有处理机正在运行；阻塞状态是指线程在等待一个事件（如某个信号量），逻辑上不可执行。每一个程序都至少有一个线程，若程序只有一个线程，那就是程序本身。

线程是程序中一个单一的顺序控制流程。进程内一个相对独立的、可调度的执行单元，是系统独立调度和分派CPU的基本单位指[运行](http://baike.baidu.com/view/1026025.htm)中的程序的调度单位。在单个程序中同时运行多个线程完成不同的工作，称为[多线程](http://baike.baidu.com/view/65706.htm)。

　　线程是程序中一个单一的顺序控制流程。进程内一个相对独立的、可调度的执行单元，是系统独立调度和分派CPU的基本单位指[运行](http://baike.baidu.com/view/1026025.htm)中的程序的调度单位。在单个程序中同时运行多个线程完成不同的工作，称为[多线程](http://baike.baidu.com/view/65706.htm)。



#3、协程

　　一个程序可以包含多个协程，可以对比与一个进程包含多个线程，因而下面我们来比较协程和线程。我们知道多个线程相对独立，有自己的上下文，切换受系统控制；而协程也相对独立，有自己的上下文，但是其切换由自己控制，由当前协程切换到其他协程由当前协程来控制。

　　http://www.zhihu.com/question/20511233

一、协程

　　1、又称微线程，纤程。英文名Coroutine.一句话说明什么是协程：协程是一种用户态的轻量级线程（相当于操作系统不知道它的存在，是用户控制的）。

　　2、协程拥有自己的寄存器上下文和栈(代码的必要的代码段和)。协程调度切换时，将寄存器上下文和栈保存到其他地方，在切回来的时候，恢复先前保存的寄存器上下文和栈，因此：协程能保留上一次调用时的状态(即所有局部状态的一个特定组合)，每次过程重入时，就相当于进入上一次调用的状态，换种说法：进入上一次离开时所处逻辑流的位置。

　　3、协程一定是在单线程中运行的。

二、协程的优点与缺点

　　优点：

　　1、无需线程上下文切换的开销。

　　2、无需原子操作（最小级别的操作）锁定及同步的开销。

　　3、方便切换控制流，简化编程模型。

　　4、高并发+高扩展性+低成本：一个CPU支持上万的协程都不是问题，所以很适合用于高并发处理。

　　缺点：

　　1、无法利用多核资源：协程的本质是个单线程，它不能同时将单个CPU的多个核用上，协程需要和进程配合才能运行在多CPU上，当然我们日常所编写的绝大部分应用都没有这个必要，除非是cpu密集型应用。

　　2、进行阻塞(Blocking)操作(如IO时)会阻塞掉整个程序。

三、使用yield实现协程操作例子

　　1、使用yield实现的一个最简单的协程的效果

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
 1 #!/usr/bin/python
 2 # -*- coding : utf-8 -*-
 3 # 作者： Presley
 4 # 时间： 2018-12-4
 5 # 邮箱：1209989516@qq.com
 6 # 这是我用来练习python 协程的测试脚本
 7 
 8 import time
 9 import queue
10 
11 def consumer(name):
12     print("starting eating baozi...")
13     while True:
14         new_baozi = yield
15         print("[%s] is eating baozi %s" %(name,new_baozi))
16 
17 def producer():
18     r = con.__next__()
19     r = con2.__next__()
20     n = 0
21     while n < 5:
22         n += 1
23         con.send(n)
24         con2.send(n)
25         print("\033[32;1m[producer]\033[0m is making")
26 
27 if __name__ == "__main__":
28     con = consumer("c1")
29     con2 = consumer("c2")
30 
31 
32     p = producer()
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

　　执行结果：

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
 1 C:\Users\wohaoshuai\AppData\Local\Programs\Python\Python36\python.exe E:/PythonLearn/day16/pro_consume.py
 2 starting eating baozi...
 3 starting eating baozi...
 4 [c1] is eating baozi 1
 5 [c2] is eating baozi 1
 6 [producer] is making
 7 [c1] is eating baozi 2
 8 [c2] is eating baozi 2
 9 [producer] is making
10 [c1] is eating baozi 3
11 [c2] is eating baozi 3
12 [producer] is making
13 [c1] is eating baozi 4
14 [c2] is eating baozi 4
15 [producer] is making
16 [c1] is eating baozi 5
17 [c2] is eating baozi 5
18 [producer] is making
19 
20 Process finished with exit code 0
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

 　2、greenlet

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
 1 #!/usr/bin/python
 2 # -*- coding : utf-8 -*-
 3 # 作者： Presley
 4 # 时间： 2018-12-4
 5 # 邮箱：1209989516@qq.com
 6 # 这是我用来练习python 协程的测试脚本
 7 
 8 from greenlet import greenlet
 9 
10 def test1():
11     print(12)
12     gr2.switch() 
13     print(34)
14     gr2.switch()
15 
16 def test2():
17     print(56)
18     gr1.switch()
19     print(78)
20 
21 gr1 = greenlet(test1)
22 gr2 = greenlet(test2)
23 gr1.switch()
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

执行结果：

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
1 C:\Users\wohaoshuai\AppData\Local\Programs\Python\Python36\python.exe E:/PythonLearn/day16/pro_consume.py
2 12
3 56
4 34
5 78
6 
7 Process finished with exit code 0
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

　　3、gevent

　　　　a、gevent是一个第三方库，可以轻松通过gevent实现并发同步或异步编程，在gevent中用到的主要模式是greenlet，它是以C扩展模块形式接入Python的轻量级协程。greenlet全部运行在主程序操作系统进程的内部，但它们被协作式地调度。

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
 1 #!/usr/bin/python
 2 # -*- coding : utf-8 -*-
 3 # 作者： Presley
 4 # 时间： 2018-12-1
 5 # 邮箱：1209989516@qq.com
 6 # 这是我用来练习python 协程的测试脚本
 7 
 8 import gevent
 9 
10 def foo():
11     print("Running in foo")
12     gevent.sleep(1)
13     print("Explicit context switch to foo again")
14 
15 def bar():
16     print("Explicit context to bar")
17     gevent.sleep(1)
18     print("Implicit context switch back to bar")
19 
20 def ex():
21     print("Explicit context to ex")
22     gevent.sleep(1)
23     print("Implicit context switch back to ex")
24 
25 gevent.joinall([
26     gevent.spawn(foo),  #类似产生一个协程的foo
27     gevent.spawn(bar),  #产生一个协程的bar
28     gevent.spawn(ex)
29 ])
30 
31 #代码的效果为：第一个协程切换到第二个，第二个切换到第三个，然后又遇到sleep(模拟io)又切换到下一个，然后实现并发的协程的效果
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

　　　　执行结果

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
1 C:\Users\wohaoshuai\AppData\Local\Programs\Python\Python36\python.exe E:/PythonLearn/day16/pro_consume.py
2 Running in foo
3 Explicit context to bar
4 Explicit context to ex
5 Explicit context switch to foo again
6 Implicit context switch back to bar
7 Implicit context switch back to ex
8 
9 Process finished with exit code 0
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

 　b、通过协程爬取网页实例

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
 1 #!/usr/bin/python
 2 # -*- coding : utf-8 -*-
 3 # 作者： Presley
 4 # 时间： 2018-12-5
 5 # 邮箱：1209989516@qq.com
 6 # 这是我用来练习python 协程的测试脚本
 7 
 8 from gevent import monkey;monkey.patch_all()
 9 import gevent
10 
11 from urllib.request import urlopen
12 
13 def f(url):
14     print("GET: %s"  %url)
15     resp = urlopen(url)
16     data = resp.read()
17     print("%d bytes received from %s." %(len(data),url))
18 
19 gevent.joinall([
20     gevent.spawn(f,"https://www.python.org/"),
21     gevent.spawn(f,"https://www.yahoo.com/"),
22     gevent.spawn(f,"https://github.com"),
23 ])
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

执行结果：

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
1 C:\Users\wohaoshuai\AppData\Local\Programs\Python\Python36\python.exe E:/PythonLearn/day16/pro_consume.py
2 GET: https://www.python.org/
3 GET: https://www.yahoo.com/
4 GET: https://github.com
5 80704 bytes received from https://github.com.
6 50008 bytes received from https://www.python.org/.
7 528149 bytes received from https://www.yahoo.com/.
8 
9 Process finished with exit code 0
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

　　c、通过gevent实现单线程下的多socket并发

　　　　server端

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
 1 #!/usr/bin/python
 2 # -*- coding : utf-8 -*-
 3 # 作者： Presley
 4 # 时间： 2018-12-5
 5 # 邮箱：1209989516@qq.com
 6 # 这是我用来练习python 协程的测试脚本
 7 
 8 
 9 import gevent
10 from gevent import socket,monkey
11 monkey.patch_all() #python中的一种黑魔法，只要写入一句话就自动的把python中的许多标准库变为非阻塞的模式
12 
13 def server(port):
14     s = socket.socket()
15     s.bind(("0.0.0.0",port))
16     s.listen(5000)
17     while True:
18         cli,addr = s.accept()
19         gevent.spawn(handle_request,cli) #执行handle_request函数，参数是cli,即客户端实例
20 def handle_request(s):
21     try:
22         while True:
23             data = s.recv(1024) #接收数据，这里设置成不阻塞
24             print("recv:",data)
25             s.send(data)
26             if not data:
27                 s.shutdown(socket.SHUT_RD) #如果接收为空值，结束
28     except Exception as ex:
29         print(ex)
30     finally:
31         s.close()
32 
33 if __name__ == "__main__":
34     server(8001)
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

　　　　client端

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
 1 #!/usr/bin/python
 2 # -*- coding : utf-8 -*-
 3 # 作者： Presley
 4 # 时间： 2018-12-5
 5 # 邮箱：1209989516@qq.com
 6 # 这是我用来练习python 协程的测试脚本
 7 
 8 import socket
 9 
10 HOST = "localhost"
11 PORT = 8001
12 s = socket.socket()
13 s.connect((HOST,PORT))
14 
15 while True:
16     msg = input(">>:")
17     if not msg:continue
18     msg = msg.encode("utf-8")
19     s.sendall(msg)
20     data = s.recv(1024)
21     print("Received",data.decode("utf-8"))
22 s.close()
```



#4、Daemon

　　Daemon()程序是一直运行的服务端[程序](http://baike.baidu.com/subview/17674/13521310.htm)，又称为[守护进程](http://baike.baidu.com/view/53123.htm)。通常在系统后台运行，没有控制终端，不与前台交互，Daemon程序一般作为[系统服务](http://baike.baidu.com/view/685551.htm)使 用。Daemon是长时间运行的进程，通常在系统启动后就运行，在系统关闭时才结束。一般说Daemon程序在后台运行，是因为它没有控制终端，无法和前 台的用户交互。Daemon程序一般都作为服务程序使用，等待客户端程序与它通信。我们也把运行的Daemon程序称作守护进程。

　　所谓守护 线程，是指在程序运行的时候在后台提供一种通用服务的线程，比如垃圾回收线程就是一个很称职的守护者，并且这种线程并不属于程序中不可或缺的部分。因此， 当所有的非守护线程结束时，程序也就终止了，同时会杀死进程中的所有守护线程。反过来说，只要任何非守护线程还在运行，程序就不会终止。

用户线程和守护线程两者几乎没有区别，唯一的不同之处就在于虚拟机的离开：如果用户线程已经全部退出运行了，只剩下守护线程存在了，虚拟机也就退出了。 因为没有了被守护者，守护线程也就没有工作可做了，也就没有继续运行程序的必要了。

#区别

多进程和多线程

进程是资源分配的最小单位，线程是CPU调度的最小单位。线程和进程的区别在于,子进程和父进程有不同的代码和数据空间,而多个线程则共享数据空 间,每个线程有自己的执行堆栈和程序计数器为其执行上下文.多线程主要是为了节约CPU时间,发挥利用,根据具体情况而定. 线程的运行中需要使用计算机的内存资源和CPU。

　　多进程： 进程是程序在计算机上的一次执行活动。当你运行一个程序，你就启动了一个进程。显然，程序是死的(静态的)，进程是活的(动态的)。进程可以分为系统进程 和用户进程。凡是用于完成操作系统的各种功能的进程就是系统进程，它们就是处于运行状态下的操作系统本身;所有由用户启动的进程都是用户进程。进程是操作 系统进行资源分配的单位。 进程又被细化为线程，也就是一个进程下有多个能独立运行的更小的单位。在同一个时间里，同一个计算机系统中如果允许两个或两个以上的进程处于运行状态，这 便是多任务。现代的操作系统几乎都是多任务操作系统，能够同时管理多个进程的运行。 多任务带来的好处是明显的，比如你可以边听mp3边上网，与此同时甚至可以将下载的文档打印出来，而这些任务之间丝毫不会相互干扰。那么这里就涉及到并行 的问题，俗话说，一心不能二用，这对计算机也一样，原则上一个CPU只能分配给一个进程，以便运行这个进程。我们通常使用的计算机中只有一个CPU，也就 是说只有一颗心，要让它一心多用，同时运行多个进程，就必须使用并发技术。实现并发技术相当复杂，最容易理解的是“时间片轮转进程调度算法”，它的思想简 单介绍如下：在操作系统的管理下，所有正在运行的进程轮流使用CPU，每个进程允许占用CPU的时间非常短(比如10毫秒)，这样用户根本感觉不出来 CPU是在轮流为多个进程服务，就好象所有的进程都在不间断地运行一样。但实际上在任何一个时间内有且仅有一个进程占有CPU。 如果一台计算机有多个CPU，情况就不同了，如果进程数小于CPU数，则不同的进程可以分配给不同的CPU来运行，这样，多个进程就是真正同时运行的，这 便是并行。但如果进程数大于CPU数，则仍然需要使用并发技术。 进行CPU分配是以线程为单位的，一个进程可能由多个线程组成，这时情况更加复杂，但简单地说，有如下关系：

　　总线程数<= CPU数量：并行运行

　　总线程数> CPU数量：并发运行

　　并行运行的效率显然高于并发运行，所以在多CPU的计算机中，多任务的效率比较高。但是，如果在多CPU计算机中只运行一个进程(线程)，就不 能发挥多CPU的优势。 这里涉及到多任务操作系统的问题，多任务操作系统(如Windows)的基本原理是:操作系统将CPU的时间片分配给多个线程,每个线程在操作系统指定的 时间片内完成(注意,这里的多个线程是分属于不同进程的).操作系统不断的从一个线程的执行切换到另一个线程的执行,如此往复,宏观上看来,就好像是多个 线程在一起执行.由于这多个线程分属于不同的进程,因此在我们看来,就好像是多个进程在同时执行,这样就实现了多任务

　　多线程：在计算机编程中，一个基本的概念就是同时对多个任务加以控制。许多程序设计问题都要求程序能够停下手头的工作，改为处理其他一些问题， 再返回主进程。可以通过多种途径达到这个目的。最开始的时候，那些掌握机器低级语言的程序员编写一些“中断服务例程”，主进程的暂停是通过硬件级的中断实 现的。尽管这是一种有用的方法，但编出的程序很难移植，由此造成了另一类的代价高昂问题。中断对那些实时性很强的任务来说是很有必要的。但对于其他许多问 题，只要求将问题划分进入独立运行的程序片断中，使整个程序能更迅速地响应用户的请求。

　　最开始，线程只是用于分配单个处理器的处理时间的一种工具。但假如操作系统本身支持多个处理器，那么每个线程都可分配给一个不同的处理器，真正 进入“并行运算”状态。从程序设计语言的角度看，多线程操作最有价值的特性之一就是程序员不必关心到底使用了多少个处理器。程序在逻辑意义上被分割为数个 线程;假如机器本身安装了多个处理器，那么程序会运行得更快，毋需作出任何特殊的调校。根据前面的论述，大家可能感觉线程处理非常简单。但必须注意一个问 题：共享资源!如果有多个线程同时运行，而且它们试图访问相同的资源，就会遇到一个问题。举个例子来说，两个线程不能将信息同时发送给一台打印机。为解决 这个问题，对那些可共享的资源来说(比如打印机)，它们在使用期间必须进入锁定状态。所以一个线程可将资源锁定，在完成了它的任务后，再解开(释放)这个 锁，使其他线程可以接着使用同样的资源。

　　多线程是为了同步完成多项任务，不是为了提高运行效率，而是为了提高资源使用效率来提高系统的效率。线程是在同一时间需要完成多项任务的时候实现的。

　　一个采用了多线程技术的应用程序可以更好地利用系统资源。其主要优势在于充分利用了CPU的空闲时间片，可以用尽可能少的时间来对用户的要求做 出响应，使得进程的整体运行效率得到较大提高，同时增强了应用程序的灵活性。更为重要的是，由于同一进程的所有线程是共享同一内存，所以不需要特殊的数据 传送机制，不需要建立共享存储区或共享文件，从而使得不同任务之间的协调操作与运行、数据的交互、资源的分配等问题更加易于解决。

进程间通信(IPC，Inter-Process Communication)，指至少两个进程或线程间传送数据或信号的一些技术或方法。进程是计算机系统分配资源的最小单位。每个进程都有自己的一部分 独立的系统资源，彼此是隔离的。为了能使不同的进程互相访问资源并进行协调工作，才有了进程间通信。这些进程可以运行在同一计算机上或网络连接的不同计算 机上。

　　进程间通信技术包括消息传递、同步、共享内存和远程过程调用。IPC是一种标准的Unix通信机制。

　　使用IPC 的理由：

　　信息共享

　　加速;

　　模块化;

　　方便; 以及

　　私有权分离.

　　主要的 IPC 方法

　　方法 提供方(操作系统或其他环境)

　　文件 多数操作系统

　　信号 多数操作系统

　　Socket 多数操作系统

　　消息队列(en:Message queue) 多数操作系统

　　管道(en:Pipe) 所有的 POSIX systems, Windows.

　　具名管道(en:Named Pipe) 所有的 POSIX 系统, Windows.

　　信号量(en:Semaphore) 所有的 POSIX 系统, Windows.

　　共享内存 所有的 POSIX 系统, Windows.

　　Message passing(en:Message passing) 用于 MPI规范，Java RMI, CORBA, MSMQ, MailSlot 以及其他.