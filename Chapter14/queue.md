# 第4节：消息队列

# [Python消息队列（RabbitMQ）](https://www.cnblogs.com/dongxiaodong/p/10495941.html)

RabbitMQ 即一个消息队列，主要是用来实现应用程序的异步和解耦，同时也能起到消息缓冲，消息分发的作用。可维护多个队列，可实现消息的一对一和广播等方式发送

RabbitMQ是一个开源的AMQP实现，服务器端用Erlang语言编写，支持多种客户端，如：Python、Ruby、.NET、Java、JMS、C、PHP、ActionScript、XMPP、STOMP等，支持AJAX。用于在分布式系统中存储转发消息，在易用性、扩展性、高可用性等方面表现不俗。

## CentOs安装：

安装socat

```
yum -y install socat
```

安装erlang

```
wget http://www.rabbitmq.com/releases/erlang/erlang-19.0.4-1.el7.centos.x86_64.rpm
Rpm -ivh erlang-19.0.4-1.el7.centos.x86_64.rpm
```

安装rabbitmq

```
wget  http://www.rabbitmq.com/releases/rabbitmq-server/v3.6.10/rabbitmq-server-3.6.10-1.el7.noarch.rpm
rpm -ivh rabbitmq-server-3.6.10-1.el7.noarch.rpm
```

启动：

```
systemctl start rabbitmq-server
```

查看状态：

```
rabbitmqctl status
```

配置网页管理端：

```
mkdir /etc/rabbitmq
```

启用插件：

```
rabbitmq-plugins enable rabbitmq_management
```

配置开放端口：

```
firewall-cmd --zone=public --add-port=15672/tcp --permanent
firewall-cmd --zone=public --add-port=5672/tcp --permanent
```

重启防火墙：

```
systemctl restart firewalld.service
```

创建用户：

```
rabbitmqctl add_user ruroot rproot
```

修改角色为管理员：

```
rabbitmqctl set_user_tags ruroot administrator
```

设置权限：

```
rabbitmqctl set_permissions -p / ruroot2 ".*" ".*" ".*"
```

测试结果：

![img](https://img2018.cnblogs.com/blog/1485202/201903/1485202-20190308145316051-323962034.png)

命令行消息管理：

得到所有队列及存在的数据条数

```
rabbitmqctl list_queues
```

## Python简单操控

**安装**

```
pip3 install pika
```

**发送数据：**

如果生成多个的话，实现效果是轮询发送，一个一个循环发送数据，如同“皇帝轮流做…”

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
 1 import pika
 2 
 3 #建立连接
 4 userx=pika.PlainCredentials("ruroot2","rproot2")
 5 conn=pika.BlockingConnection(pika.ConnectionParameters("192.168.43.10",5672,'/',credentials=userx))
 6 
 7 #开辟管道
 8 channelx=conn.channel()
 9 
10 #声明队列，参数为队列名
11 channelx.queue_declare(queue="dongchannel11")
12 
13 #发送数据，发送一条，如果要发送多条则复制此段
14 channelx.basic_publish(exchange="",
15                        routing_key="dongchannel11",# 队列名
16                        body="dongxiaodongtodata3" # 发送的数据
17                        )
18 print("--------发送数据完成-----------")
19 
20 #关闭连接
21 conn.close()
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

**取出数据：**

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
 1 import pika
 2 
 3 #建立连接
 4 userx=pika.PlainCredentials("ruroot2","rproot2")
 5 conn=pika.BlockingConnection(pika.ConnectionParameters("192.168.43.10",5672,'/',credentials=userx))
 6 
 7 #开辟管道
 8 channelx=conn.channel()
 9 
10 #声明队列，参数为队列名
11 channelx.queue_declare(queue="dongchannel11")
12 
13 #消息处理函数，执行完成才说明接收完成，此时才可以接收下一条，串行
14 def dongcallbackfun(v1,v2,v3,bodyx):
15     print("得到的数据为:",bodyx)
16 
17 #接收准备
18 channelx.basic_consume(dongcallbackfun, #收到消息的回调函数
19                        queue="dongchannel11", #队列名
20                        no_ack=True #是否发送消息确认
21                        )
22 print("-------- 开始接收数据 -----------")
23 
24 #开始接收消息
25 channelx.start_consuming()
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

**发送端是否设置数据保存时间：**

默认服务器（rabbitmq-server）重启后消息队列和消息数据均会全部消失

消息队列的永久保存，开启后将仅仅实现服务器重启后消息队列依然在，但数据还是会丢失，如果要保存数据，请参考接下来

```
#声明队列，参数为队列名
#实现队列永久保存，durable=True
channelx.queue_declare(queue="dongch1",durable=True)
```

数据的永久保存（一直等待被取，即使服务器重启），将要永久保存的发送数据添加属性properties

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
#发送数据
channelx.basic_publish(exchange="",
                       routing_key="dongch1",# 队列名
                       body="dongxiaodongtodata333335", # 发送的数据
                       properties=pika.BasicProperties(
                           delivery_mode=2, #实现消息永久保存
                       )
                       )
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

**发送端实现能者多劳**

在发送端发送数据前，添加下面一句，此句添加一次即可，可以实现自动判断多接收端的处理速度，实现接收端处理快则多派发任务，处理慢则少派发任务

```
channelx.basic_qos(prefetch_count=1)
```

**接收端是否接收确认：**

接收端开启消息确认（值为False），接收端则会在接收回调函数结束时手动发送确认消息到数据发送者，如果接收端在回调函数处理未完成时就挂掉了，那么发送端将会立即把当前数据转交到下一个接收端进行数据处理

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
1 #消息处理函数，执行完成才说明接收完成，此时才可以接收下一条，串行
2 def dongcallbackfun(channlx,methodx,v3,bodyx):
3     print("得到的数据为:",bodyx)
4     channelx.basic_ack(delivery_tag=methodx.delivery_tag) #发送数据完成确认消息，手动确认
5 
6 #接收准备
7 channelx.basic_consume(dongcallbackfun, #收到消息的回调函数
8                        queue="dongchannel11", #队列名
9                        no_ack=False #是否在消息回调函数结束后发送确认信息到发消息者，true表示不发送
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

**非阻塞版数据接收：**

启用会立即返回结果，如果有数据则进入回调函数，无数据则进行下一条，可以配合while使用

```
conn.process_data_events() #使用连接对象进行数据接收判断
print("无数据")
```

## 实现消息的订阅和发布：

**发布：**

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
 1 import pika
 2 
 3 #建立连接
 4 userx=pika.PlainCredentials("ruroot2","rproot2")
 5 conn=pika.BlockingConnection(pika.ConnectionParameters("192.168.1.175",5672,'/',credentials=userx))
 6 
 7 #开辟管道
 8 channelx=conn.channel()
 9 
10 #声明发布和订阅通道,如果可以确认通道存在则可以去掉该句
11 channelx.exchange_declare(exchange="dongee",exchange_type="fanout")
12 
13 #发送数据
14 channelx.basic_publish(exchange="dongee",#确定发布主题为：dongee
15                        routing_key="",
16                        body="dongxiaodongeeedata11", # 发送的数据
17                        )
18 
19 print("--------发送数据完成-----------")
20 
21 #关闭连接
22 conn.close()
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

**订阅：**

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
 1 import pika
 2 #建立连接
 3 userx=pika.PlainCredentials("ruroot2","rproot2")
 4 conn=pika.BlockingConnection(pika.ConnectionParameters("192.168.1.175",5672,'/',credentials=userx))
 5 
 6 #开辟管道
 7 channelx=conn.channel()
 8 
 9 #声明发布和订阅通道,如果可以确认通道存在则可以去掉该句
10 channelx.exchange_declare(exchange="dongee",exchange_type="fanout")
11 
12 #声明队列，生成一个随机的且不存在的队列,该队列会在连接断开后自动销毁
13 resqueue=channelx.queue_declare(exclusive=True)
14 #得到随机生成的队列名
15 queuenamex=resqueue.method.queue
16 
17 #将队列和发布数据绑定，确定订阅主题为：dongee
18 channelx.queue_bind(exchange="dongee",queue=queuenamex)
19 
20 #消息处理函数，执行完成才说明接收完成，此时才可以接收下一条，串行
21 def dongcallbackfun(channlx,methodx,v3,bodyx):
22     print("得到的数据为:",bodyx)
23 
24 #接收准备
25 channelx.basic_consume(dongcallbackfun, #收到消息的回调函数
26                        queue=queuenamex, #队列名
27                        no_ack=True
28                        )
29 
30 print("-------- 开始接收数据 -----------")
31 
32 #开始接收消息
33 channelx.start_consuming()
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

## 通过管道实现进一步的消息订阅和发布：

发布:

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
 1 import pika
 2 
 3 #建立连接
 4 userx=pika.PlainCredentials("ruroot2","rproot2")
 5 conn=pika.BlockingConnection(pika.ConnectionParameters("192.168.1.175",5672,'/',credentials=userx))
 6 
 7 #开辟管道
 8 channelx=conn.channel()
 9 
10 #声明发布和订阅通道,如果可以确认通道存在则可以去掉该句
11 channelx.exchange_declare(exchange="dongee2",exchange_type="direct")
12 
13 #发送数据
14 channelx.basic_publish(exchange="dongee2",#确定发布主题为：dongee2
15                        routing_key="dongqu33", #确定发布的队列（发布的主题）：dongqu33
16                        body="dongxiaodong333", # 确定发送的数据
17                        )
18 
19 #发送数据
20 channelx.basic_publish(exchange="dongee2",#确定发布主题为：dongee2
21                        routing_key="dongqu22", #确定发布的队列（发布的主题）：dongqu22
22                        body="dongxiaodong222", # 确定发送的数据
23                        )
24 
25 print("--------发送数据完成-----------")
26 
27 #关闭连接
28 conn.close()
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

订阅：

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
 1 import pika
 2 #建立连接
 3 userx=pika.PlainCredentials("ruroot2","rproot2")
 4 conn=pika.BlockingConnection(pika.ConnectionParameters("192.168.1.175",5672,'/',credentials=userx))
 5 
 6 #开辟管道
 7 channelx=conn.channel()
 8 
 9 #声明发布和订阅通道,如果可以确认通道存在则可以去掉该句
10 channelx.exchange_declare(exchange="dongee2",exchange_type="direct")
11 
12 #声明队列，生成一个随机的且不存在的队列,该队列会在连接断开后自动销毁
13 resqueue=channelx.queue_declare(exclusive=True)
14 #得到随机生成的队列名
15 queuenamex=resqueue.method.queue
16 
17 #将队列和发布数据绑定，确定订阅主题为：dongqu11 和 dongqu22
18 channelx.queue_bind(exchange="dongee2",queue=queuenamex,routing_key="dongqu11")
19 channelx.queue_bind(exchange="dongee2",queue=queuenamex,routing_key="dongqu22")
20 
21 #消息处理函数，执行完成才说明接收完成，此时才可以接收下一条，串行
22 def dongcallbackfun(channlx,methodx,v3,bodyx):
23     print("队列名(订阅的主题名）为：%r  得到的数据为:%r  "%(methodx.routing_key,bodyx))
24 
25 #接收准备
26 channelx.basic_consume(dongcallbackfun, #收到消息的回调函数
27                        queue=queuenamex, #队列名
28                        no_ack=True
29                        )
30 
31 print("-------- 开始接收数据 -----------")
32 
33 #开始接收消息
34 channelx.start_consuming()
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)