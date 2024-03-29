# Socket编程

TCP的优点： 可靠，稳定 TCP的可靠体现在TCP在传递数据之前，会有三次握手来建立连接，而且在数据传递时，有确认、窗口、重传、拥塞控制机制，在数据传完后，还会断开连接用来节约系统资源。 TCP的缺点： 慢，效率低，占用系统资源高，易被攻击 TCP在传递数据之前，要先建连接，这会消耗时间，而且在数据传递时，确认机制、重传机制、拥塞控制机制等都会消耗大量的时间，而且要在每台设备上维护所有的传输连接，事实上，每个连接都会占用系统的CPU、内存等硬件资源。 而且，因为TCP有确认机制、三次握手机制，这些也导致TCP容易被人利用，实现DOS、DDOS、CC等攻击。

UDP的优点： 快，比TCP稍安全 UDP没有TCP的握手、确认、窗口、重传、拥塞控制等机制，UDP是一个无状态的传输协议，所以它在传递数据时非常快。没有TCP的这些机制，UDP较TCP被攻击者利用的漏洞就要少一些。但UDP也是无法避免攻击的，比如：UDP Flood攻击…… UDP的缺点： 不可靠，不稳定 因为UDP没有TCP那些可靠的机制，在数据传递时，如果网络质量不好，就会很容易丢包。 基于上面的优缺点，那么： 什么时候应该使用TCP： 当对网络通讯质量有要求的时候，比如：整个数据要准确无误的传递给对方，这往往用于一些要求可靠的应用，比如HTTP、HTTPS、FTP等传输文件的协议，POP、SMTP等邮件传输的协议。 在日常生活中，常见使用TCP协议的应用如下： 浏览器，用的HTTP FlashFXP，用的FTP Outlook，用的POP、SMTP Putty，用的Telnet、SSH QQ文件传输 ………… 什么时候应该使用UDP： 当对网络通讯质量要求不高的时候，要求网络通讯速度能尽量的快，这时就可以使用UDP。 比如，日常生活中，常见使用UDP协议的应用如下： QQ语音 QQ视频 TFTP ……

有些应用场景对可靠性要求不高会用到UPD，比如长视频，要求速率

**小结TCP与UDP的区别：**

1.基于连接与无连接；
2.对系统资源的要求（TCP较多，UDP少）；
3.UDP程序结构较简单；
4.流模式与数据报模式 ；

5.TCP保证数据正确性，UDP可能丢包，TCP保证数据顺序，UDP不保证。

 

```
tcp协议和udp协议的差别 
           TCP           UDP 
是否连接     面向连接     面向非连接 
传输可靠性   可靠        不可靠 
应用场合    少量数据    传输大量数据 

速度       慢         快

```

TCP与UDP区别总结：

1、TCP面向连接（如打电话要先拨号建立连接）;UDP是无连接的，即发送数据之前不需要建立连接

```
2、TCP提供可靠的服务。也就是说，通过TCP连接传送的数据，无差错，不丢失，不重复，且按序到达;UDP尽最大努力交付，即不保证可靠交付

3、TCP面向字节流，实际上是TCP把数据看成一连串无结构的字节流;UDP是面向报文的

UDP没有拥塞控制，因此网络出现拥塞不会使源主机的发送速率降低（对实时应用很有用，如IP电话，实时视频会议等）

4、每一条TCP连接只能是点到点的;UDP支持一对一，一对多，多对一和多对多的交互通信

5、TCP首部开销20字节;UDP的首部开销小，只有8个字节
```

6、TCP的逻辑通信信道是全双工的可靠信道，UDP则是不可靠信道

 

#  

TCP UDP
TCP与UDP基本区别
 1.基于连接与无连接
 2.TCP要求系统资源较多，UDP较少； 
 3.UDP程序结构较简单 
 4.流模式（TCP）与数据报模式(UDP); 
 5.TCP保证数据正确性，UDP可能丢包 
 6.TCP保证数据顺序，UDP不保证 
　　
UDP应用场景：
 1.面向数据报方式
 2.网络数据大多为短消息 
 3.拥有大量Client
 4.对数据安全性无特殊要求
 5.网络负担非常重，但对响应速度要求高
 
具体编程时的区别
  1.socket()的参数不同 
　　 2.UDP Server不需要调用listen和accept 
　　 3.UDP收发数据用sendto/recvfrom函数 
　　 4.TCP：地址信息在connect/accept时确定 
　　 5.UDP：在sendto/recvfrom函数中每次均 需指定地址信息 
　　 6.UDP：shutdown函数无效
 
编程区别
  通常我们在说到网络编程时默认是指TCP编程，即用前面提到的socket函数创建一个socket用于TCP通讯，函数参数我们通常填为SOCK_STREAM。即socket(PF_INET, SOCK_STREAM, 0)，这表示建立一个socket用于流式网络通讯。 
　  SOCK_STREAM这种的特点是面向连接的，即每次收发数据之前必须通过connect建立连接，也是双向的，即任何一方都可以收发数据，协议本身提供了一些保障机制保证它是可靠的、有序的，即每个包按照发送的顺序到达接收方。 

　　而SOCK_DGRAM这种是User Datagram Protocol协议的网络通讯，它是无连接的，不可靠的，因为通讯双方发送数据后不知道对方是否已经收到数据，是否正常收到数据。任何一方建立一个socket以后就可以用sendto发送数据，也可以用recvfrom接收数据。根本不关心对方是否存在，是否发送了数据。它的特点是通讯速度比较快。大家都知道TCP是要经过三次握手的，而UDP没有。 

基于上述不同，UDP和TCP编程步骤也有些不同，如下：

TCP: 
TCP编程的服务器端一般步骤是： 
　　1、创建一个socket，用函数socket()； 
　　2、设置socket属性，用函数setsockopt(); * 可选 
　　3、绑定IP地址、端口等信息到socket上，用函数bind(); 
　　4、开启监听，用函数listen()； 
　　5、接收客户端上来的连接，用函数accept()； 
　　6、收发数据，用函数send()和recv()，或者read()和write(); 
　　7、关闭网络连接； 
　　8、关闭监听； 

TCP编程的客户端一般步骤是： 
　　1、创建一个socket，用函数socket()； 
　　2、设置socket属性，用函数setsockopt();* 可选 
　　3、绑定IP地址、端口等信息到socket上，用函数bind();* 可选 
　　4、设置要连接的对方的IP地址和端口等属性； 
　　5、连接服务器，用函数connect()； 
　　6、收发数据，用函数send()和recv()，或者read()和write(); 
　　7、关闭网络连接；

UDP:
与之对应的UDP编程步骤要简单许多，分别如下： 
　　UDP编程的服务器端一般步骤是： 
　　1、创建一个socket，用函数socket()； 
　　2、设置socket属性，用函数setsockopt();* 可选 
　　3、绑定IP地址、端口等信息到socket上，用函数bind(); 
　　4、循环接收数据，用函数recvfrom(); 
　　5、关闭网络连接； 

UDP编程的客户端一般步骤是： 
　　1、创建一个socket，用函数socket()； 
　　2、设置socket属性，用函数setsockopt();* 可选 
　　3、绑定IP地址、端口等信息到socket上，用函数bind();* 可选 
　　4、设置对方的IP地址和端口等属性; 
　　5、发送数据，用函数sendto(); 
　　6、关闭网络连接；

TCP和UDP是OSI模型中的运输层中的协议。TCP提供可靠的通信传输，而UDP则常被用于让广播和细节控制交给应用的通信传输。

UDP补充：
  UDP不提供复杂的控制机制，利用IP提供面向无连接的通信服务。并且它是将应用程序发来的数据在收到的那一刻，立刻按照原样发送到网络上的一种机制。即使是出现网络拥堵的情况下，UDP也无法进行流量控制等避免网络拥塞的行为。此外，传输途中如果出现了丢包，UDO也不负责重发。甚至当出现包的到达顺序乱掉时也没有纠正的功能。如果需要这些细节控制，那么不得不交给由采用UDO的应用程序去处理。换句话说，UDP将部分控制转移到应用程序去处理，自己却只提供作为传输层协议的最基本功能。UDP有点类似于用户说什么听什么的机制，但是需要用户充分考虑好上层协议类型并制作相应的应用程序。

TCP补充：
 TCP充分实现了数据传输时各种控制功能，可以进行丢包的重发控制，还可以对次序乱掉的分包进行顺序控制。而这些在UDP中都没有。此外，TCP作为一种面向有连接的协议，只有在确认通信对端存在时才会发送数据，从而可以控制通信流量的浪费。TCP通过检验和、序列号、确认应答、重发控制、连接管理以及窗口控制等机制实现可靠性传输。

TCP与UDP区别总结：
1、TCP面向连接（如打电话要先拨号建立连接）;UDP是无连接的，即发送数据之前不需要建立连接
2、TCP提供可靠的服务。也就是说，通过TCP连接传送的数据，无差错，不丢失，不重复，且按序到达;UDP尽最大努力交付，即不保  证可靠交付
3、TCP面向字节流，实际上是TCP把数据看成一连串无结构的字节流;UDP是面向报文的
 UDP没有拥塞控制，因此网络出现拥塞不会使源主机的发送速率降低（对实时应用很有用，如IP电话，实时视频会议等）
4、每一条TCP连接只能是点到点的;UDP支持一对一，一对多，多对一和多对多的交互通信
5、TCP首部开销20字节;UDP的首部开销小，只有8个字节
6、TCP的逻辑通信信道是全双工的可靠信道，UDP则是不可靠信道



## Tcp

### 服务端

我们使用 socket 模块的 **socket** 函数来创建一个 socket 对象。socket 对象可以通过调用其他函数来设置一个 socket 服务。

现在我们可以通过调用 **bind(hostname, port)** 函数来指定服务的 *port(**端口**)*。

接着，我们调用 socket 对象的 *accept* 方法。该方法等待客户端的连接，并返回 *connection* 对象，表示已连接到客户端。

完整代码如下：

```python
#!/usr/bin/python # -*- coding: UTF-8 -*- # 文件名：server.py

 import socket # 导入 socket 模块 

s = socket.socket() # 创建 socket 对象 

host = socket.gethostname() # 获取本地主机名 

port = 12345 # 设置端口 

s.bind((host, port)) # 绑定端口 

s.listen(5) # 等待客户端连接 

while True: 

c,addr = s.accept() # 建立客户端连接 

print '连接地址：', addr c.send('欢迎访问菜鸟教程！') 

c.close() # 关闭连接
```



### 客户端

接下来我们写一个简单的客户端实例连接到以上创建的服务。端口号为 12345。

**socket.connect(hosname, port )** 方法打开一个 TCP 连接到主机为 *hostname* 端口为 *port* 的服务商。连接后我们就可以从服务端获取数据，记住，操作完成后需要关闭连接。

完整代码如下：

## 实例

```python
#!/usr/bin/python # -*- coding: UTF-8 -*- # 文件名：client.py

import socket # 导入 socket 模块 

s = socket.socket() # 创建 socket 对象 

host = socket.gethostname() # 获取本地主机名 

port = 12345 # 设置端口号 

s.connect((host, port)) 

print s.recv(1024) 

s.close()
```

现在我们打开两个终端，第一个终端执行 server.py 文件：

```
$ python server.py
```

第二个终端执行 client.py 文件：

```
$ python client.py 
欢迎访问菜鸟教程！
```

这时我们再打开第一个终端，就会看到有以下信息输出：

```
连接地址： ('192.168.0.118', 62461)
```

 

##UDP

udp的特点是不需要建立连接

一个作为客户端，一个作为服务端、客户端client.py，服务端server.py

客户端client.py

```python
import socket

#创建socket对象
#SOCK_DGRAM  udp模式
s=socket.socket(socket.AF_INET,socket.SOCK_DGRAM)

#发送数据 字节
s.sendto("你好".encode(),("169.254.184.146",8000))
```


服务端server.py

```python
import socket

s=socket.socket(socket.AF_INET,socket.SOCK_DGRAM)  #创建socket对象、SOCK_DGRAM udp模式
s.bind(("169.254.184.146",8000))  #绑定服务器的ip和端口
data=s.recv(1024)                 #一次接收1024字节
print(data.decode())              #decode()解码收到的字节
```


注意：先运行文件二在运行文件一
