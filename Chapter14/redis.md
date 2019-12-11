# 第3节：存储基础之Redis



- - Redis最基础入门教程
    - [简介](https://www.cnblogs.com/xiaohuiduan/p/11394505.html#e7ae80e4bb8b_2)
- Redis 简介
  - [Redis 优势](https://www.cnblogs.com/xiaohuiduan/p/11394505.html#redis20e4bc98e58abf_4)
  - Redis与其他key-value存储有什么不同？
    - [字符串（Strings）](https://www.cnblogs.com/xiaohuiduan/p/11394505.html#e5ad97e7aca6e4b8b2efbc88stringsefbc89_6)
    - [哈希（Hash）](https://www.cnblogs.com/xiaohuiduan/p/11394505.html#e59388e5b88cefbc88hashefbc89_7)
    - [列表（List）](https://www.cnblogs.com/xiaohuiduan/p/11394505.html#e58897e8a1a8efbc88listefbc89_8)
    - [集合（Sets）](https://www.cnblogs.com/xiaohuiduan/p/11394505.html#e99b86e59088efbc88setsefbc89_9)
    - [有序集合（sorted sets）](https://www.cnblogs.com/xiaohuiduan/p/11394505.html#e69c89e5ba8fe99b86e59088efbc88sorted20setsefbc89_10)
    - [发布消息/订阅频道](https://www.cnblogs.com/xiaohuiduan/p/11394505.html#e58f91e5b883e6b688e681afe8aea2e99885e9a291e98193_11)
    - [结语](https://www.cnblogs.com/xiaohuiduan/p/11394505.html#e7bb93e8afad_12)

 

## Redis最基础入门教程

还记得第一次面试*来也*的时候，面试官问我，“会MongoDB吗？”，“不会”；“知道redis吗？”，“知道，但是没用过”，“emm……”

 

![img](https://img2018.cnblogs.com/blog/1439869/201908/1439869-20190822151856232-557640789.jpg)

 

### 简介

在面对高并发的数据读取的时候，当连表查询的需求不是那么的强烈，此时，非关系型数据库得到了高速的发展。其中，非关系型数据库中的键值数据库中的redis便是我们今天需要讲的内容。其中redis为了保证效率，会将数据保存在内存中（当然redis会周期性的把更新的数据写入磁盘或者把修改操作写入追加的记录文件）。

Redis亦被称为数据机构服务器，因为它的值（Value）可以是字符串（String），哈希（Hash），列表（List），集合（Sets）和有序集合（sorted sets）。

Redis 在线测试：http://try.redis.io/

下面是一段来自于[菜鸟教程](https://www.runoob.com/redis/redis-intro.html)的介绍

> # Redis 简介
>
> Redis 是完全开源免费的，遵守BSD协议，是一个高性能的key-value数据库。
>
> Redis 与其他 key - value 缓存产品有以下三个特点：
>
> - Redis支持数据的持久化，可以将内存中的数据保存在磁盘中，重启的时候可以再次加载进行使用。
> - Redis不仅仅支持简单的key-value类型的数据，同时还提供list，set，zset，hash等数据结构的存储。
> - Redis支持数据的备份，即master-slave模式的数据备份。
>
> 
>
> ## Redis 优势
>
> - 性能极高 – Redis能读的速度是110000次/s,写的速度是81000次/s 。
> - 丰富的数据类型 – Redis支持二进制案例的 Strings, Lists, Hashes, Sets 及 Ordered Sets 数据类型操作。
> - 原子 – Redis的所有操作都是原子性的，意思就是要么成功执行要么失败完全不执行。单个操作是原子性的。多个操作也支持事务，即原子性，通过MULTI和EXEC指令包起来。
> - 丰富的特性 – Redis还支持 publish/subscribe, 通知, key 过期等等特性。
>
> 
>
> ## Redis与其他key-value存储有什么不同？
>
> - Redis有着更为复杂的数据结构并且提供对他们的原子性操作，这是一个不同于其他数据库的进化路径。Redis的数据类型都是基于基本数据结构的同时对程序员透明，无需进行额外的抽象。
> - Redis运行在内存中但是可以持久化到磁盘，所以在对不同数据集进行高速读写时需要权衡内存，因为数据量不能大于硬件内存。在内存数据库方面的另一个优点是，相比在磁盘上相同的复杂的数据结构，在内存中操作起来非常简单，这样Redis可以做很多内部复杂性很强的事情。同时，在磁盘格式方面他们是紧凑的以追加的方式产生的，因为他们并不需要进行随机访问。

redis怎么安装，我就不做介绍了，因为不同的系统安装方式不一样。如果不想安装话可以使用在线的redis环境。不过还是推荐一下，因为接下来会使用python去实现一些操作。其中redis数据库的可视化可以使用**redis-desktop-manager**。命令行操作使用**redis-cli**。

接下来我将通过不同的数据结构来介绍redis的操作。

### 字符串（Strings）

字符串（Strings）是Redis的基本数据结构之一，由key和value组成。我们可以这样类比成编程语言的变量：keya代表变量名，value代表变量值。

**查看所有的key的命令**

```bash
keys *
```

 

![img](https://img2018.cnblogs.com/blog/1439869/201908/1439869-20190822151902224-158187429.png)

 

**创建字符串**

```bash
set key value
```

 

![img](https://img2018.cnblogs.com/blog/1439869/201908/1439869-20190822151907417-2003359313.png)

 

如果value中有空格，则需要使用**""**将value包起来。如：

```bash
set x "xxx xxx xxx"
```

**读取字符串**

```bash
get key
```

 

![img](https://img2018.cnblogs.com/blog/1439869/201908/1439869-20190822151912742-1908770428.png)

 

如果获取一个不存在的key，则会返回**nil**。

**修改key里面的值**

1. 进行修改

   下面这个命令key存在则修改，不存在则创建

```bash
set key 新的值
```

 如果我们不希望set的命令覆盖旧值怎么办？在使用"NX"参数即可。这样，当key存在时，使用`set key value NX`并不能覆盖原来的值。

```bash
set key value NX
```

1. 进行增添

   如果我们想在value的末尾加上一些字符串，使用append命令。（当key不存在的时候，则会创建key）当然，如果如果值有空格的话，和set的处理方法一样。

   ```bash
   append key value
   ```

2. 数字进行修改

   注意下面的命令只针对于value为数字的情况，否则就会报错。

   ```bash
   # 让key里面的数字加1
   incr key
   # 减1
   decr key
   # 加n
   incrby key n
   # 减n
   decrby key n
   ```

**删除**

如果key存在则放回1，否则返回0

```bash
del key
```

**代码实现**

下面是使用python对以上的所有命令进行实现（任何编程语言都差不多）

```python
import redis
client = redis.Redis()
# 获得所有的key
keys = client.keys()
# 创建字符串
client.set("thisKey","thatValue")
# 获得value
value = client.get("thisKey")
# 不覆盖修改
client.set("thisKey","way",nx=True)
# 增添
client.append("thisKey","newMSg")
# 对数字就行修改
client.set("num",1)
client.incr("num")
client.incrby("num",10)
client.decr("num")
client.decrby("num",4)
# 进行删除操作
client.delete("thisKey")
```

### 哈希（Hash）

在前面我们介绍了字符串类型的Redis储存方案，这个时候我们可以想一想如果我需要储存10w个人的分数，右需要储存10w个人的密码（假如这样做），那么我们需要多少多少个key？20w个key！！那么我们的key又该怎样分配呢（注意：key不能重复）？我们是不是得这样：*用户名_score*,*用户名_pwd*，在用户名后面加上不同的类型来代表不同的数据。那么在redis如何解决这些问题呢？使用**哈希表**！！关于哈希表的数据结构我们可以看看[这篇](https://www.cnblogs.com/xiaohuiduan/p/11263054.html#e695a3e58897e8a1a8_13)

Redis hash 是一个string类型的field和value的映射表（*key任然为key*），hash特别适合用于存储对象，每个 hash 可以存储 232 - 1 键值对（43多亿）。使用Hash表不仅能够减少Redis中key的个数，还能优化存储空间，占用的内存要比字符串小很多。

下面是redis的存储示意图：

 

![img](https://img2018.cnblogs.com/blog/1439869/201908/1439869-20190822151918078-128193825.png)

 

**添加数据：**

一次添加一个键值对数据：

> hset key field value

一次添加多个键值对数据：

> hmset key field1 value1 [field2 value2 ]

当然如果我们不想对已经存在的field进行修改

> hsetnx key field value

**获得数据：**

获得一个字段的值：

> hget key field

获得多个字段的值：

> hmget key field1 [field2]

获得所有的字段名和值

> hgetall key

当然我们也可以分别获得所有的field获得value

> hvals key

> hkeys key

**判断是否存在某字段**

> HEXISTS key field

如果字段存在则返回1，如果不存在则返回0

**获得哈希表中字段的数量**

> hlen key

接下来我就不再使用python实现这些东西了，会更多的来介绍各种结构的特点。如果想了解更多的指令可以看[菜鸟教程](https://www.runoob.com/redis/redis-tutorial.html)

### 列表（List）

列表是一种很神奇的结构，可以把列表成一根水管，数据从可以从一边进，然后从另外一边出来（当然，那一边即可以进又可以出，只不过顺序不同而已）。那么这种结构有什么用处呢？我们可以以发消息为例。发消息我们需要保证消息到达的顺序，那么我们是不是就可以使用列表了呢？例如：发送消息从左边进，接受消息从右边得到。下面介绍几个简单的指令：

**插入数据**

l代表left（左），r代表right(右)

> 从左边插入数据
>
> lpush key value
>
> 从右边插入数据
>
> rpush key value

**获得列表的长度**

注意下面的第一个**l**并不是代表left，而是代表list

> llen key

**查看数据**

> lrang key 开始索引 结束索引

索引从最左边开始编号，意思就是最后一个lpush的数据的索引是0（将列表想成一个小水管就行）。如果开始索引和结束索引一样，就返回索引位置的值。那么如果从右边开始呢？使用“负索引”即可。其中**-1**代表最右边的数据。-2代表最右边的第二个数据。

**弹出数据**

> 弹出最左边的数据
>
> lpop key
>
> 弹出最右边的数据
>
> rpop key

弹出数据和查看数据的差别在于，弹出数据的同时也会将数据进行删除。

### 集合（Sets）

这个集合和数学中的集合有着差不多的概念。怎么说呢？在redis的集合中，数据是**无序的**，**不能重复**。

**添加数据：**

s代表集合（set）

> sadd key value1 value2 value3……

**获得集合中元素的数量**

如果不存在这个集合则返回0

> scard key

**从集合中获取数据**

> spop key count

前面我们说道，集合是无序的，所以spop的获取也是无序的。（获得数据后会将数据删除）count代表获取几条数据。

这个是获得集合的所有数据（并不会删除数据）。不过这个命令在生产环境中最好不要使用，因为数据量大的话你的服务器可能就炸了。

> SMEMBERS key

**判断数据是否存在**

> sismember key value

存在返回1，否则返回0

**删除数据**

> srem key value1 value2……

**下面便是数学上面的知识了**

> 取交集
>
> sinter key1 key2……
>
> 取并集
>
> sunion key1 key2……
>
> 取差集
>
> sdiff key1 key2……

### 有序集合（sorted sets）

有序集合，顾名思义就是集合里面的数据是有序的。那么它有什么含义呢？我们想象一下，在一个高并发的场景中，数据是一直更新的，如果我们将数据存到数据库中，如果需要实时获取排名的话，那么肯定会对数据的性能造成很大的影响。毕竟数据量越大，排序时间也就越缓慢。和集合不同的是，有序集合的元素会关联一个double类型的分数，其中元素不能重复，但是分数可以重复。

**添加数据**

> zadd key score1 member1 [score2 member2]

前面说过，score必须为double类型，所以如果输入非double则会报错。

**修改数据**

修改数据可以使用zadd进行修改数据的分数，同时可以添加NX参数

> zadd key NX sorce member

还可以使用zincrby对数据对数据的分数进行加减操作

> ZINCRBY key 改变量 member

其中改变量既可以为正数也可以为负数。如果member不存在则会创建，member的分数和改变量一致。

**获取数据**

基于评分范围内的排序

1. 从小到大排序

> zrangebyscore 有序集合名 评分下限 评分上限 [withsores limit 切片开始位置 结果数量]

1. 从大到小排序

> zrevrangebyscore 有序集合名 评分下限 评分上限 [withsores limit 切片开始位置 结果数量]

其中使用括号括起来的代表可以省略，如果withsores省略代表只返回值，不返回评分。省略“limit 切片开始位置 结果数量”代表不对结果进行切片。

基于位置的排序

1. 从小到大排序

   位置是从零开始的

   > zrange 有序集合名 开始位置（含） 结束位置 （含）[withsores]

2. 从大到小排序

   > zrevrange 有序集合名 开始位置（含） 结束位置 （含）[withsores]

**获得排名**

> zrank 有序集合名 值

> zrevrank 有序集合名 值

zrank 和 zrevrank的区别在于，zrank排名是从0开始的，评分越小则排名越靠近0，评分最小的值排名为0。而zrevrank则是评分越大则越靠近0。相同点在于如果值不存在则返回None。

**获得一个值的评分**

> zscore 有序集合名 值

如果一个值不存在则返回None。

**查看某个评分范围内的值有多少**

> zcount 有序集合名 评分下限 评分上限

### 发布消息/订阅频道

我们来说一个场景，还是以前面的发消息场景为例，如果服务端的消息在进行更新，那么我们如何更新客户端的信息呢？按照前面的方法，我们只有使用轮询查询的方式，按照一定的时间（比如说1s）检查redis，看消息是否发生改变，如果消息发生了改变，则客户端进行更新，那么接下来就会有以下的问题：

1. 不停地检查redis，耗费系统资源
2. 使用轮询查询，消息会有延时
3. 即使1s（轮询的时间）中发送了5条消息，那么客户端只会发生一次改变。

这个时候我们就是可以使用redis的“发布/订阅”模式实现消息通信。

- 发布：消息的发布者
- 订阅：消息的接受者，可以为1个也可以为多个

**发布消息**

> publish 频道名 信息

**订阅频道**

> subscribe 频道名1 频道名2……

其中会返回3条消息：第一条是信息的类型，第二条是频道名，第三条是被发布的内容。其中需要注意，只能接受目前的消息，新加入的订阅是没办法接受到以前的订阅的。

### 结语

以上便是redis的一个很简单的入门教程。只介绍了redis的简单使用和一些基本操作，至于redis命令中更复杂的指令，百度或者google就行了。对于redis，我觉得我们（作为一个学生）应该关注的是redis为什么能够如此优秀？里面用了什么数据结构，以及如何能够将redis应用到高并发的场景中，怎么实现多服务器数据的保存以及备份问题。