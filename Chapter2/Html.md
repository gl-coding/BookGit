# 第3节：Html



HTML为超文本标记语言，超文本指的是超链接。

用记事本写的是纯文本，纯文本中只能保存文本内容，图片、音频、视频等无法保存。

基本格式：

``` html
<html> 
      <head>
            <title> 这是一个非常好的网页</title>
      </head>
      <body>
            <!-- 这里是写注释的，不会再页面中显示，但是可以在源码中看见。
            -->
            <h1>这是我的第一个网页</h1>
      </body>
</html>
```

## HTML 实例

```html
<!DOCTYPE html> 
<html>
  <head> <meta charset="utf-8"> 
    <title>菜鸟教程(runoob.com)</title> 
  </head> 
  <body> 
    <h1>我的第一个标题</h1> 
    <p>我的第一个段落。</p> 
  </body> 
</html>
```

## 实例解析

```
<!DOCTYPE html> 声明为 HTML5 文档
<html> 元素是 HTML 页面的根元素
<head> 元素包含了文档的元（meta）数据，如 <meta charset="utf-8"> 定义网页编码格式为 utf-8。
<title> 元素描述了文档的标题
<body> 元素包含了可见的页面内容
<h1> 元素定义一个大标题
<p> 元素定义一个段落
```

**注：**在浏览器的页面上使用键盘上的 F12 按键开启调试模式，就可以看到组成标签。

------

## 什么是HTML?

HTML 是用来描述网页的一种语言。

- HTML 指的是超文本标记语言: **H**yper**T**ext **M**arkup **L**anguage
- HTML 不是一种编程语言，而是一种**标记**语言
- 标记语言是一套**标记标签** (markup tag)
- HTML 使用标记标签来**描述**网页
- HTML 文档包含了HTML **标签**及**文本**内容
- HTML文档也叫做 **web 页面**

------

## HTML 标签

HTML 标记标签通常被称为 HTML 标签 (HTML tag)。

- HTML 标签是由*尖括号*包围的关键词，比如 <html>
- HTML 标签通常是*成对出现*的，比如 <b> 和 </b>
- 标签对中的第一个标签是*开始标签*，第二个标签是*结束标签*
- 开始和结束标签也被称为*开放标签*和*闭合标签*

<标签>内容</标签>

------

## HTML 元素

"HTML 标签" 和 "HTML 元素" 通常都是描述同样的意思.

但是严格来讲, 一个 HTML 元素包含了开始标签与结束标签，如下实例:

HTML 元素:

<p>这是一个段落。</p>
<p>这是一个段落。</p>
------

## Web 浏览器

Web浏览器（如谷歌浏览器，Internet Explorer，Firefox，Safari）是用于读取HTML文件，并将其作为网页显示。

浏览器并不是直接显示的HTML标签，但可以使用标签来决定如何展现HTML页面的内容给用户：

![img](https://www.runoob.com/wp-content/uploads/2013/06/html-first.png)

------

## HTML 网页结构

![image-20191205163534410](/Users/guolei08/Library/Application Support/typora-user-images/image-20191205163534410.png)

只有 <body> 区域 (白色部分) 才会在浏览器中显示。

------

## HTML版本

从初期的网络诞生后，已经出现了许多HTML版本:

| 版本      | 发布时间 |
| :-------- | :------- |
| HTML      | 1991     |
| HTML+     | 1993     |
| HTML 2.0  | 1995     |
| HTML 3.2  | 1997     |
| HTML 4.01 | 1999     |
| XHTML 1.0 | 2000     |
| HTML5     | 2012     |
| XHTML5    | 2013     |



------

## <!DOCTYPE> 声明

<!DOCTYPE>声明有助于浏览器中正确显示网页。

网络上有很多不同的文件，如果能够正确声明HTML的版本，浏览器就能正确显示网页内容。

doctype 声明是不区分大小写的，以下方式均可：

<!DOCTYPE html>

<!DOCTYPE HTML>

<!doctype html>

<!Doctype Html>
------

## 通用声明

### HTML5

```
<!DOCTYPE html>
```

### HTML 4.01

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN"
"http://www.w3.org/TR/html4/loose.dtd">

### XHTML 1.0

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">

查看完整网页声明类型 [DOCTYPE 参考手册](https://www.runoob.com/tags/tag-doctype.html)。

------

## 中文编码

目前在大部分浏览器中，直接输出中文会出现中文乱码的情况，这时候我们就需要在头部将字符声明为 UTF-8 或 GBK。

## HTML 实例

```html
<!DOCTYPE html> <html> <head> <meta charset="UTF-8"> <title>页面标题</title> </head> <body>  <h1>我的第一个标题</h1>  <p>我的第一个段落。</p>  </body> </html>
```

## 基本结构

HTML的文件后缀名为`.html`，下面是一个HTML文档的基本结构。

```
<!DOCTYPE html> <!-- 用于声明、告诉浏览器当前是一个 HTML 文档 -->

<html lang="zh-cn"> <!-- HTML 文档开始 | lang="zh-cn" 中文声明 -->

<head> </head> <!-- 头部区域 -->

<body> </body> <!-- 主体区域 -->

</html> <!-- HTML 文档结束 -->
```

------

## 头部区域

HTML的头部区域 `head` 用于定义一些网页的初始化工作，例如网页的标题、文档的编码、载入JavaScript、CSS文件等...



```
<head>

 <meta charset="utf-8"> <!-- 文档编码 -->

 <meta name="description" content="简明教程是一个有趣的知识库 :) "> <!-- 网页描述 -->

 <title>简明教程</title> <!-- 网页标题 -->

</head>
```

其中`title`标签定义的网页标题显示在浏览器顶部窗口的标签栏，而` meta ~ description `定义的网页描述是不可见的，它用于告诉搜索引擎的`爬虫机器人`，当前页面主要的内容，适当的时候搜索引擎会给你相关词汇的搜索排名，类似的标签还有`meta ~ keyword`、`meta ~ author`。

------

## 主体区域

HTML的主体区域 `body` 是浏览器的视窗区域，在这个区域写入的任何内容，都会在浏览器中显示。

```
<body>

 <p>当前是一个内容段落 ～</p>

</body>
```

------

## 标签形式

每个以`<>`符号组成的元素成为一个HTML标签，其中由分为 `单标签` 和 `双标签`。

```
<!-- 双标签 -->

<html> <!-- <> 标签开始 -->

 <head></head> <body></body>  ... <!-- 双标签内部可以包含下级标签 -->

</html> <!-- </> 标签结束 -->

<!-- 单标签 -->

<hr /> <!-- 自闭合 -->
```

------

## 标签属性

标签的形式除了有单双之外，还包括了属性，通常是作为标签功能的补充。

```
<html lang="zh-cn"> <!-- lang="" 就是标签的属性 | 而 zh-cn 称为属性值 -->

<!-- 一个标签可以包含多属性 -->

<a href="https://www.jmjc.tech" style="color: red;">简明教程</a>
```

------

## 严格类型

HTML并不是严格类型的语言，拥有一定的容错机制，当我们把标签写错的时候，浏览器并不会直接报错不显示了，而是根据自己的理解去解析错误的内容。

```
<hr /> <!-- 单标签的自闭合写成 <hr> 也能完成正确显示 -->

<p </p> <!-- 忘记写了一个 > 号 可能也会解析正确，也可能段落的内容被错位显示 -->
```

------

## 代码注释

HTML用于注释标签是 ``

```
<!-- 这是一段注释内容 -->
```

## 文本标签

常见的一些文本标签。

```
<p>一群大雁往南飞 ～ </p> <!-- 段落标签 -->

<span>无功能</span> <!-- 无功能，针对 CSS 设计的，用于载入 style="" 属性 -->

<br> <!-- 换行标签 -->

<strong>加粗</strong>

<em>斜体</em>

<del>删除</del>

<hr> <!-- 水平线 -->
显示效果
```

一群大雁往南飞 ～

无功能**加粗***斜体*~~删除~~

------

## 标题组

用于文档标题相关的定义从 `h1 ~ h6`，主要是字体大小和粗细的变化。

```
<h1>标题</h1>
<h2>标题</h2>
<h3>标题</h3>
<h4>标题</h4>
<h5>标题</h5>
<h6>标题</h6>
显示效果
```

# 标题

## 标题

### 标题

#### 标题

##### 标题

###### 标题

------

## 语义化

`标签语义化`是HTML5标准中的一个新特性，可以理解为标签名称的含义，就是标签的功能。在旧版本HTML4.0中，针对字体的加粗使用的是``标签，而到了HTML5使用的是``标签，因为 “strong” 这个单词的含义就有 “加粗” 的意思，但由于 HTML5 对 HTML4 的兼容，在浏览器的眼里``、`` 是相等的。除了 b、strong 之外，还有很多标签仅仅是语义化的效果，但是功能效果和 `span`、`div` 是完全一致的，所有为了方便，可以记住这几个主流的标签，通常也能完成大部分相同的工作。

## 布局

HTML中有一些标签类似于一个`盒子`，这些标签元素也被称为 “容器” 或者 “区块” 。一个个盒子的作用是对不同的元素进行分组，从而构成了整个页面的布局。

```
<body> <!-- body 其实也是一个大箱子 -->

 <header>头部</header> 

 <nav>导航</nav>
 
 <aside>侧边栏</aside>

 <section>主题</section> 

 <footer>尾部</footer>

</body>
```

需要注意，网页样式的布局要使用`CSS`定义，`HTML`的工作只是对功能空间的规划。

上面列举布局标签功能等同于HTML4.0的`div`标签， 只是HTML5标准的新特性 - [语义化效果](https://www.jmjc.tech/less/3)。

## 列表

```
无序列表
<ul>
 <li>苹果</li>
 <li>草莓</li>
 <li>葡萄</li>
 <li>西瓜</li>
</ul>
显示效果
```

- 苹果
- 草莓
- 葡萄
- 西瓜

------

```
有序列表
<ol>
 <li>one</li>
 <li>two</li>
 <li>three</li>
 <li>four</li>
</ol>
显示效果
```

1. one
2. two
3. three
4. four

## 组合

```
文本组合
<dl>
 <dt>标题</dt>
 <dd>内容 ~</dd>
 <dd>内容 N</dd>
</dl>
显示效果
```

- 标题

  内容 ~

  内容 N

------

```
图文组合
<figure>
 <img src="/public/home/img/flower.png">
 <figcaption>花</figcaption>
</figure>

```

显示效果

![img](https://www.jmjc.tech/public/home/img/flower.png)

## 表格

表格的基本结构。

```
<table border="1"> <!-- border="1" 显示边框  -->

 <!-- 下面是一个 “三行两列” 的表格 -->
 <!-- tr 行 | th 标题列 | td 普通列 -->

 <tr><th>性别</th><th>年龄</th></tr>
 <tr><td>男</td><td>21</td></tr>
 <tr><td>女</td><td>35</td></tr>

</table>
显示效果
```

| 性别 | 年龄 |
| :--- | :--- |
| 男   | 21   |
| 女   | 35   |

------

## colspan

```
行合并
<tr>
 <th colspan="2">数字</th> <!-- colspan="2" 2行合并 -->
</tr> 
<tr>
 <td>233</td> <td>666</td>
</tr>
显示效果
```

| 数字 |      |
| :--- | ---- |
| 233  | 666  |

------

## rowspan

```
列合并
<tr>
 <td rowspan ="2">数字</td> <td>233</td> <!-- rowspan="2" 2列合并-->
</tr> 
<tr>
 <td>666</td>
</tr>
效果
```

| 数字 | 233  |
| ---- | ---- |
| 666  |      |

## 链接

链接是资源之间的跳转，资源的类型可以是网页、图片、视频等任何能在浏览器中显示的元素。

```
<!-- href="资源路径" -->
<!-- target=_blank 新增窗口的方式打开资源 -->

<a href="https://www.jmjc.tech" target=_blank>简明教程</a> 
点击
☞ 简明教程
```

------

## 路径

路径也称为地址，又分为 `相对路径` 和 `绝对路径`，我们可以把计算机的文件系统看出是一棵树。

![img](https://www.jmjc.tech/public/home/img/path.png)

我们所在的位置是`index.html`，跟`img`同级，所有可以直接访问。相对路径就是相对当前文件的位置查找对应资源。

```
<a href="img/1.jpg">链接到图片</a>
```

在相对路径中 `./` 表示当前目录，`../` 表示上级目录，上例中使用 img/1.jpg = ./img/1jpg。

------

```
绝对路径
```

不管我们的文件在哪个位置，直接从根目录访问。

```
<a href="c:/desktop/html/img/1.jpg">链接到图片</a>
```

这样，即使我们的`index.html`文件跑到了`users`目录下，还是能够成功加载图片。

## 图片

```
加载图片
<!-- <img src="图片路径" width="宽度" height="高度" /> | 默认显示原图大小 -->

<img src="/public/home/img/fly.jpg" />
效果
```

![img](https://www.jmjc.tech/public/home/img/fly.jpg)

## ismap

捕获用户点击图片的坐标位置。

```
<a href="/less/6">
 <img src="/public/home/img/flower.png" ismap /> 
</a>
```

尝试点击图片，观察当前的URL的后缀，会增加类似`?26,48`的参数，这就是你所点击的图片坐标。

[![img](https://www.jmjc.tech/public/home/img/flower.png)](https://www.jmjc.tech/less/6)

## map

图片坐标映射。

```
<!-- 通过 usemap 关联映射区域 -->
<img src="/public/home/img/flower.png" usemap="#flower" />

<!-- 映射区域 -->
<map name="flower" />

 <!-- area 映射单元，可以定义多个 -->
 <!-- coords 映射坐标 -->
 <!-- href 映射资源 -->

 <area shape="rect" coords="35,35,60,60" href="/public/home/img/fly.jpg" target="_blank">

</map>
```

点击小花中心的黄色区域，会映射到 `fly.jpg` 这张图片。

![img](https://www.jmjc.tech/public/home/img/flower.png)

## 表单

表单是一种常见的前后端数据交互方式，下面是表单的基本结构和一些表单控件。

```
<!-- form 表单主体 | method 表单的 HTTP 请求方法 GET/POST | action 接收请求路径  -->

<form method="post" action="index.php" > 

 <!-- 表单控件 -->

 <input type="text" /> <!-- 文本框 -->

 <input type="password" /> <!-- 密码框 -->

 <input type="hidden" /> <!-- 隐藏框 -->

 <input type="number" /> <!-- 数字框 -->

 <input type="date" /> <!-- 日期控件 -->

 <!-- 多选框 | 相同 name 为一组 -->
 牛奶 <input type="checkbox" name="food" />  面包<input type="checkbox" name="food" />  

 <!-- 单选框 | 相同 name 为一组 -->
 男 <input type="radio" name="sex" />  女 <input type="radio" name="sex" />  

 <!-- 多行文本框 | cols 宽 rows 高 -->
 <textarea rows="2" cols="20"></textarea>

 <!-- 选择框 -->
 <select name="num">
  <option>one</option>
  <option>two</option>
  <option>three</option>
 </select>

 <!-- 上传文件 | accept 文件类型限制 -->
 <input type="file" accept="image/gif, image/jpeg, image/png" >

 <!-- 范围控件 | min max 范围值 -->
 <input type="range" min="1" max="100" />

 <!-- 颜色控件 -->
 <input type="color" />

 <!-- 表单提交 -->
 <input type="submit" value="提交" />

 <!-- 表单重置 -->
 <input type="reset" value="重置" />

 <!-- 普通按钮 -->
 <button type="button">按钮</button>

</form>
```

------

## 控件展示

```
文本框
```



------

```
密码框
```



------

```
隐藏框
```

------

```
数字框
```



------

```
日期
```



------

```
多选框
```

面包 

 牛奶 



------

```
单选框
```

男 

 女 



------

```
多行文本框
```



------

```
选择框
```



------

```
上传文件
```

------

```
范围
```

------

```
颜色
```



------

```
提交
```



------

```
重置
```



------

```
按钮
```

按钮

## 控件属性

```
name
<!-- name 属性是一个表示，后台通过这个表示获取对应的表单数据 -->

<input type="text" name="user" />
```

------

```
value
<!-- value 是控件的值 -->

<input type="text" name="user" value="Ada" />
```

------

```
placeholder
<!-- placeholder 提示 -->

<input type="text" placeholder="请输入用户名" />
```

------

```
datalist > list
<!-- datalist > list 下拉提示框 -->

<input type="text" name="someone" list="zhou">
<datalist id="zhou">
 <option value="周杰伦">周杰伦</option>
 <option value="周大福">周大福</option>
 <option value="周武王">周武王</option>
</datalist>
```

------

```
maxlength
<!-- maxlength 长度限制 -->

<input type="text" maxlength="12" />
```

------

```
size
<!-- size 控件尺寸 -->

<input type="text" size="30" />
```

------

```
required
<!-- required 必选 -->

<input type="text" required />
```

------

```
readonly
<!-- readonly 只读 -->

<input type="text" readonly />
```

------

```
disabled
<!-- disabled 禁用 -->

<input type="text" disabled />
```

------

```
pattern
<!-- pattern 正则校验 -->

<input type="text" pattern="[0-7]{3}" />
```

## progress

进度条也是`HTML5标准`的一个新特性，需要注意但凡是HTML5标准的即说明不支持IE9以下的浏览器。

```
<!-- value 当前量 max 总量 -->

<progress value="30" max="100"></progress>
显示效果
```



## meter

比上面`progress`定制性更强的进度条。

```
<!-- 根据 min low high max 4个刻度等级衡量 value 的值，optimum 用于标示每个等级相对应的显示颜色 -->

<meter value="100" min="0" low="100" high="200" max="300" optimum="200"></meter>
显示效果
```

# HTML5 多媒体

## 音频

HTML4.0 载入多媒体文件，需要是借助 Flash 实现，一般使用 `embed` 或者 `object` 元素，HTML5 新标准原生支持了音频和视频，增加了两个元素 `audio & video`。

```
<!-- controls 显示控件，默认是背景音乐 -->
<!-- autoplay 自动播放 -->
<!-- loop 循环播放 -->
<!-- preload 预加载 -->

<audio src="音频文件" controls="controls" loop="loop" preload autoplay></audio>
```

------

## 视频

视频的载入方式于音频类似。

```
<!-- poster 预览图 -->
<!-- width/height 宽高 -->
<!-- loop 循环播放 -->
<!-- autoplay 自动播放 -->
<!-- controls 显示控件 -->
<!-- preload 预加载 -->
<!-- muted 静音 -->

<video src="视频文件" poster="图片地址" controls="controls" width="600" height="600" loop="loop" autoplay preload muted></video>

<!-- 以上的很多参数是可选的，根据需要随意配搭 -->
```