# 第2节 Bs4

# 3.2 Bs4

##### 是什麽？

###### BeautifulSoup，就是一个第三方的库，使用之前需要安装

·  pip install bs4

·  pip进行安装，默认是从国外安装，所以需要将pip源设置为国内源，国内有豆瓣源、阿里源、网易源等等xxx

### 配置永久国内源：

- **1.windows****配置方式：**

（1）打开文件资源管理器
 --------在地址栏中输入 %appdata%
 （2）手动创建一个文件夹叫做 pip
 （3）在pip的文件夹里面新建一个文件 pip.ini
 （4）文件中写如下内容

```
[global]
index-url = http://pypi.douban.com/simple
[install]
trusted-host=pypi.douban.com
```

- **linux****配置方式：**

（1）cd ~
 （2）mkdir .pip
 （3）vi ~/.pip/pip.conf
 （4）编辑内容和windows的内容一模一样

#### 安装

pip install bs4
 pip install lxml

###### bs4是什麽？

- 它的作用是能够快速方便简单的提取网页中指定的内容，给我一个网页字符串，然后使用它的接口将网页字符串生成一个对象，然后通过这个对象的方法来提取数据

###### lxml是什麽？

- lxml是一个解析器，也是下面的xpath要用到的库，bs4将网页字符串生成对象的时候需要用到解析器，就用lxml，或者使用官方自带的解析器 html.parser

### bs4语法学习

- 通过本地文件进行学习，通过网络进行写代码
       （1）根据标签名进行获取节点
       只能找到第一个符合要求的节点
       （2）获取文本内容和属性
- 属性

soup.a.attrs 返回一字典，里面是所有属性和值
 soup.a['href'] 获取href属性

- 文本

**soup.a.string**
 **soup.a.text**
 **soup.a.get_text()**
 【注】当标签里面还有标签的时候，string获取的为None，其他两个获取纯文本内容

#### （3）find方法

**soup.find('a')**
 **soup.find('a', class_='xxx')**
 **soup.find('a', title='xxx')**
 **soup.find('a', id='xxx')**
 **soup.find('a', id=re.compile(r'xxx'))**
 【注】find只能找到符合要求的第一个标签，他返回的是一个对象

#### （4）find_all

返回一个列表，列表里面是所有的符合要求的对象
 **soup.find_all('a')**
 **soup.find_all('a', class_='wang')**
 **soup.find_all('a', id=re.compile(r'xxx'))**
 **soup.find_all('a', limit=2)** 提取出前两个符合要求的a

#### （5）select

选择，选择器 css中

常用的选择器
 标签选择器、id选择器、类选择器
 层级选择器**
 div h1 a 后面的是前面的子节点即可
 div > h1 > a 后面的必须是前面的直接子节点
 属性选择器
 input[name='hehe']
 select('选择器的')
 【注】返回的是一个列表，列表里面都是对象
 【注】find find_all select不仅适用于soup对象，还适用于其他的子对象，如果调用子对象的select方法，那么就是从这个子对象里面去找符合这个选择器的标签

```
from bs4 import BeautifulSoup
 
# 生成soup对象
soup = BeautifulSoup(open('soup.html', encoding='utf8'), 'lxml')
print(type(soup))
 
print(soup.a.attrs)
print(soup.a.attrs['href'])
print(soup.a['href'])
 
print(soup.a.string)
print(soup.a.text)
print(soup.a.get_text())
 
print(soup.div.string)
print(soup.div.text)
print(soup.div.get_text())
 
ret = soup.find('a')
ret = soup.find('a', title='清明')
ret = soup.find('a', class_='dumu')
print(ret)
 
import re
ret = soup.find('a', id='xiaoge')
ret = soup.find('a', id=re.compile(r'^x'))
print(ret.string)
 
ret = soup.find_all('a')
print(ret[1].string)
 
ret = soup.find_all('a', class_='wang')
print(ret)
 
ret = soup.find_all('a', id=re.compile(r'^x'))
print(ret)
 
ret = soup.select('a')
ret = soup.select('#muxiong')
print(ret[0]['title'])
 
ret = soup.select('.wang')
print(ret)
 
ret = soup.select('div > a')
print(ret)
 
ret = soup.select('a[title=东坡肉]')
 
print(ret)
 
odiv = soup.select('.tang')[0]
 
ret = odiv.select('a')
 
print(ret)
```

 

 

# 3.3 实战

3.3.1

 

3.3.2