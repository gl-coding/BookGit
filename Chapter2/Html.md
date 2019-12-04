# 第3节：Html

HTML

HTML为超文本标记语言，超文本指的是超链接。

用记事本写的是纯文本，纯文本中只能保存文本内容，图片、音频、视频等无法保存。

基本格式：

``` html
<html> 
​      <head>
​            <title> 这是一个非常好的网页</title>
​      </head>
​      <body>
​            <!-- 这里是写注释的，不会再页面中显示，但是可以在源码中看见。
​            -->
​            <h1>这是我的第一个网页</h1>
​      </body>
</html>
```



网页的主体内容写在 之间；

表示根标签,一个页面只有一个，网页的所有内容都应该写在html根标签中。

该标签的内容，不会再网页中直接显示，用来帮助浏览器解析页面。

网页标题，它是网页中对于搜索来说最重要的内容，会影响到网页在搜索引擎中的排名。

&lt;!−−−这里写注释−−>&lt;!-- -这里写注释--&gt;<!−−−这里写注释−−>

执行后的效果：



属性

可以通过属性来设置标签，如果处理标签，如果处理标签，可以在开始标签中添加属性，属性需要写在开始标签中，实际上就是一个名值对。

设置颜色属性： 

<!--将“第二个”变为红色-->

<h1>这是我的<font color="red" size="7">第二个</font>网页</h1>
1

2

<font>标签：定文本的字体、字体尺寸、字体颜色。

color:颜色属性

size:字体大小属性，最大为7

font是表现属性，不赞成使用，因为表现用CSS设置更加好。

运行后效果：

 

HTML5声明：

 

<!doctype html>

1

为了兼容一些旧的页面，浏览器中设置了两种解析模式：

 

标准模式

怪异模式

如果不声明可能在怪异模式时出现异常。

元素

一个完整的标签就是元素。

进制

太简单，省略了，不记笔记。

 

乱码

乱码出现的原因：

计算机是一个非常笨的，只认识两个东西：0和1.在计算机中保存的任何内容，最终都需要转换为0和1来保存。在读取的时候，需要把二进制编码转换为正确的内容。

编码：依据一定的规则，将字符转换为二进制编码的过程。

解码：依据一定的规则，将二进制编码转为字符的过程。

字符集：编码和解码所采用的规则，被称为字符集。就相当于密码本。

常见的字符集：

 

ASCII

ISO-8859-1

GBK

GB2312：中文系统的默认编码

UTF-8：万国码，支持地球上所有的文字

ANSI：自动以系统的默认编码来保存文件

产生乱码的根本原因是编码和解码采用的字符集不同。

在中文系统的浏览器中，默认采用GB2312进行解码。

可用标签meta来设置网页的一些元数据，比如网页的字符集，关键字，简介。

当出现乱码时，可用meta来告诉浏览器，网页所采用的编码字符集，然后浏览器会采用相应的字符集来解码。

<meta charset="utf-8" />
1

这条标签告诉浏览器，我们采用utf-8来编码，然后浏览器会采用相应的字符集来解码，从而不出现乱码。

 

常用的标签

标题标签

一共有六级标题。对于搜索引擎来说，一级标题的重要性仅次于title，会影响页面在搜索引擎中的排名。

一般页面中标题标签只使用h1，h2，h3,以后的基本不用。

 

```
<! doctype html>
<html>
   <head>
                  <meta charset='utf-8'/>
​         <title>常用的标签</title>
   </head>
   <body>
​         <!--标题标签,一共有六级标题-->
​         <h1>一级标题</h1>
​         <h2>一级标题</h2>
​         <h3>一级标题</h3>
​         <h4>一级标题</h4>
​         <h5>一级标题</h5>
​         <h6>一级标题</h6>
   </body>
</html>
```

效果：

 

段落标签: <p> </p>

 

<p>我是一个p标签，我用来表示一个段落</p>
1

在HTML中，字符之间插入的空格再多，浏览器也会当成一个空格，换行也会当做一个空格。

换行标签：<br/>

如果要换行采用<br/>

上述两个标签的实例：

 

<! doctype html>

<html>

   <head>

                  <meta charset='utf-8'/>
​         <title>常用的标签</title>

   </head>

   <body>

​         <!--段落标签，段落标签用于表示内容中的一个自然段。-->

                  <p>我是一个p标签，我用来表示一个段落</p>
                  <p>我是一个p标签，我用来表示一个段落</p>
​         

​         <!--在HTML中，字符之间插入的空格再多，浏览器也会当成一个空格，

​         换行也会当做一个空格。-->

                  <p>

​            离离原上草，

​            一岁一枯荣，

​            野火烧不尽，

​            粒粒皆辛苦。

​         </p>

​         <!--若要换行，则采用br标签-->

                  <p>

​            离离原上草，<br/>

​            一岁一枯荣，<br/>

​            野火烧不尽，<br/>

​            粒粒皆辛苦。<br/>

​         </p>

   </body>

</html>

1

2

3

4

5

6

7

8

9

10

11

12

13

14

15

16

17

18

19

20

21

22

23

24

25

26

27

28

效果：

 

 

实体

在HTML中，一些如< >这种特殊字符是不能直接使用的，需要使用一些特殊的符号来表示这些字符，这些特殊符号被称为实体（转义字符串）

实体的语法：&实体名字;

<:&lt;

\>:&gt;

&nbsp;空格

&copy;:版权符号

 

图片标签

使用img标签来向网页引入一个外部图片，该标签是自结束标签，

属性：

src:设置一个外部图片的路径。

alt:可用来设置图片的描述，只有在图片不能显示的时候才会出现字样，搜索引擎可用通过该属性来识别不同的图片，如果不写该属性，则搜索引擎不会对该图片进行收录解锁。

width:设置图片宽度

height:设置图片高度

如果宽度和高度只是设置一个，另一个也会同时等比例调整大小，如果同时设置两个属性就按照我们的设置来，一般不建议设置这两个属性。

插入一幅图：

 

 [外链图片转存失败(img-mA7htndO-1562049705918)(https://mp.csdn.net/mdeditor/images/1.jpg)]

1

图片路径

src属性配置的是图片的路径，目前我们所要使用的路径全部都是相对路径。

相对路径：相对于当前html文件所在的目录的文件夹。

../:上一级目录

../../：上一级的上一级目录

./:当前html文件的下一级目录

 

图片格式

jpeg(jpg):支持的颜色比较多，图片可以压缩，但是不支持透明，一般用于保存照片等颜色丰富的图片。

gif：支持的颜色少，只是支持简单的透明，支持动态图。图片颜色单一，或者动态图时候可以使用。

png：支持的颜色多，并且支持复杂的透明，可以用来显示颜色复杂的透明图片。

图片的使用原则：效果不一致，使用效果好的，效果一致使用小的。

 

meta标签

使用meta标签还可以用来设置网页的关键字。

比如：

 

<meta name = "keyworde" content="HTML5,javascript,前端"/>
1

在该网页中，只要输入:前端，HTML5，javascript，前端，这时该网页被搜索到的概率很大。

meta还可以实现网页重定向。

 

<! doctype html>

<html>

  <head>

            <meta charset='utf-8'/>
​       <title></title>

            <meta name = "keyworde" content="HTML5,javascript,前端"/>
            <meta http-equiv="refresh" content="5;url=http://www.baidu.com"/>
  </head>

  <body>

​     <h1>5秒后跳转页面</h1>

  </body>

</html>

1

2

3

4

5

6

7

8

9

10

11

12

效果：5秒后会自动跳转到百度主页。

 

HTML的语法规范

HTML不区分大小写，但是我们一般使用小写。

注释不能嵌套。

HTML标签必须结构完整，要么成对出现，要么自结束标签。

HTML标签可以嵌套，但是不能交叉嵌套。

HTML标签中的属性必须有值，且值必须加引号。

内联框架

使用内联框架可以引入一个外部页面，使用iframe来创建一个内联框架，属性和图片类似。

属性：

src:指向一个外部页面的路径，可以使用相对路径。

在现实中不推荐使用内联框架，因为内联框架中的内容不会被搜索引擎所检索。

 

<! doctype html>

<html>

   <head>

                  <meta charset='utf-8'/>
​         <title></title>

   </head>

   <body>

              <iframe src = "dome2.html"></iframe>
   </body>

</html>

1

2

3

4

5

6

7

8

9

10

效果：

 

 

超链接

使用超链接可以让我们从一个页面跳转到另一个页面，使用a标签创建一个超链接。

属性：

href:指向链接跳转的目标地址，可以写一个相对路径，也可以写一个完整的地址。

 

<a href="http://www.baidu.com">我是一个超链接 </a>

1

a标签中的target属性可以用来指定打开链接的位置，它的可选值：

 

_self:表示在当前窗口中打开（默认值）

_blank:在一个新的窗口中打开链接

可以设置一个内联框架的name属性值，链接将会在指定的内联框架中打开。

center标签中的内容，会默认在页面中居中显示，可以将要居中的内容放在该标签中。

<! doctype html>

<html>

   <head>

                  <meta charset='utf-8'/>
​         <title></title>

   </head>

   <body>

            <a href="http://www.baidu.com"target = "_black">我是一个超链接 </a><br /><br /><br />

            <a href="dome2.html">我是一个超链接 </a>

​      <center>

​         这是我的个人博客

​      </center>

   </body>

</html>

1

2

3

4

5

6

7

8

9

10

11

12

13

14

效果：

 

 

兄弟元素选择器

后一个兄弟元素选择器

作用：可以选中一个元素后紧挨着的指定的兄弟元素

语法：前一个+后一个

例子：为span后的一个p元素设置一个背景颜色为黄色

 

<!DOCTYPE html>

<html>

   <head>

            <meta charset="utf-8">

​      <title>这是一个网页</title>

            <style type="text/css">

​         span+p{

​            background-color:red;

​         }

​      </style>

   </head>

   <body>

            <p>我是一个P标签</p>
            <p>我是一个P标签</p>
            <p>我是一个P标签</p>
            <p>我是一个P标签</p>
​      <span>我是一个span标签</span>

            <p>我是一个P标签</p>
            <p>我是一个P标签</p>
            <p>我是一个P标签</p>
   </body>

</html>

1

2

3

4

5

6

7

8

9

10

11

12

13

14

15

16

17

18

19

20

21

22

效果：

 

 

选中后边的所有兄弟元素

 

      <style type="text/css">

​         span~p{

​            background-color:red;

​         }

​      </style>

1

2

3

4

5

效果：

 

 

否定伪类

作用：可以从已经选中的元素中剔除出某些元素

语法：:not(选择器)

例子：为除了class值为hello的所有P元素设置一个背景颜色为红色。

 

<!DOCTYPE html>

<html>

   <head>

            <meta charset="utf-8">

​      <title>这是一个网页</title>

            <style type="text/css">

​         p:not(.hello){

​            background-color:red;

​         }

​      </style>

   </head>

   <body>

            <p>我是一个P标签</p>
            <p>我是一个P标签</p>
            <p>我是一个P标签</p>
            <p>我是一个P标签</p>
            <p class="hello">我是一个不同的P元素</p>
            <p>我是一个P标签</p>
            <p>我是一个P标签</p>
            <p>我是一个P标签</p>
   </body>

</html>

1

2

3

4

5

6

7

8

9

10

11

12

13

14

15

16

17

18

19

20

21

22

效果：

 

 

 

样式继承

像儿子可以继承父亲的遗产一样，在CSS中，祖先元素上的样式，也会被他的后代所继承。利用继承，可以将一些基本的样式设置给祖先元素，这样所有的后代元素将会自动继承这些样式。

但是并不是所有的样式都会被子元素继承，比如：背景相关的样式不会被继承。

例子：

 

<!DOCTYPE html>

<html>

   <head>

            <meta charset="utf-8">

​      <title>这是一个网页</title>

            <style type="text/css">

​         

​      </style>

   </head>

   <body>

            <p style="font-size:30px;">

​         我是p标签中的文字

​         <span>我是span</span>

​      </p>

​      <span>我是p标签外的span</span>

   </body>

</html>

1

2

3

4

5

6

7

8

9

10

11

12

13

14

15

16

17

效果：

 

子元素不会继承背景相关的样式。

例子：

 

<!DOCTYPE html>

<html>

   <head>

            <meta charset="utf-8">

​      <title>这是一个网页</title>

            <style type="text/css">

​         

​      </style>

   </head>

   <body>

            <div style="background-color:yellow">

                  <p style="font-size:30px;">

​            我是p标签中的文字

​            <span>我是span</span>

​         </p>

​      </div>

​      <span>我是p标签外的span</span>

   </body>

</html>

1

2

3

4

5

6

7

8

9

10

11

12

13

14

15

16

17

18

19

效果:

 

我们发现子元素背景颜色变黄了，但是这不是继承的，这是由于所有标签的背景颜色是透明的，这里div中的p中的内容的背景颜色是透明的，但是div中背景颜色设置为黄色，子元素背景颜色的黄色是div的背景颜色透过来了覆盖了原来的透明色，因此让人误认为是p继承了div的背景颜色。

 

选择器的优先级

使用不同的选择器，选中同一个元素时并且设置相同的样式时，这时样式之间产生了冲突。到底最终会采用哪个选择器定义的样式，由选择器的优先级确定，优先级高的有限显示。

 

优先级规则：

   内联样式，优先级：1000

   id选择器，优先级：100

   类和伪类，优先级：10

   元素选择器，优先级：1

   通配选择器`*`:优先级：0

   继承的样式，没有优先级。

1

2

3

4

5

6

7

<!DOCTYPE html>

<html>

   <head>

            <meta charset="utf-8">

​      <title>这是一个网页</title>

            <style type="text/css">

​         /* 类选择器 */

​         .p1{

​            background-color:yellow;

​         }

​         /* 元素选择器 */

​         p{

​            background-color:red;

​            font-size:50px;

​         }

​         /* id选择器 */

​         \#p2{

​            background-color:blue;

​         }

​         /* 通配选择器 */

​         *{

​            font-size:30px;

​         }

​         

​      </style>

   </head>

   <body>

            <p class="p1" id="p2">我是一个段落

​      <span>我是一个p标签</span>

​      </p>

   </body>

</html>

1

2

3

4

5

6

7

8

9

10

11

12

13

14

15

16

17

18

19

20

21

22

23

24

25

26

27

28

29

30

31

32

效果：

 

分析：span中的文字没有继承p标签总的文字大小，而是采用通配选择器的字体大小，这是因为继承没有优先级，由于上述设置背景颜色的选择器中id选择器的优先级最高，因此背景色为蓝色。

当选择器中包含多种选择器时，需要将多种选择器的优先级相加然后比较。但是注意，选择器优先级计算不会超过他的最大数量级。比如：我们有10个id选择器，最终的优先级不会是1000，而是999或者900。

例子：

 

<!DOCTYPE html>

<html>

   <head>

            <meta charset="utf-8">

​      <title>这是一个网页</title>

            <style type="text/css">

​      

​         \#p2{

​            background-color:blue;

​         }

​      

​         p#p2{

​            background-color:red;

​         }

​      </style>

   </head>

   <body>

            <p class="p1" id="p2" >我是一个段落

​      <span>我是一个p标签</span>

​      </p>

   </body>

</html>

1

2

3

4

5

6

7

8

9

10

11

12

13

14

15

16

17

18

19

20

21

22

效果：

 

由于p#p2的优先级为101，而#p2的优先级为100，因此显示红色背景。

如果选择器的优先级一样，谁在后面就用谁。

例子：

 

<!DOCTYPE html>

<html>

   <head>

            <meta charset="utf-8">

​      <title>这是一个网页</title>

            <style type="text/css">

​         .p1{

​            background-color:yellow;

​         }

​         .p3{

​            background-color:red;

​         }

​      

​      </style>

   </head>

   <body>

            <p class="p1 p3" id="p2" >我是一个段落

​      <span>我是一个p标签</span>

​      </p>

   </body>

</html>

1

2

3

4

5

6

7

8

9

10

11

12

13

14

15

16

17

18

19

20

21

效果：

 

并集选择器的优先级是单独计算。

 

div, p,  #p1, .hello

1

可以在样式的最后添加一个！important，则此时该样式会获得一个最高的优先级，甚至超过内联样式，但是开发中慎用。

例子：

 

<!DOCTYPE html>

<html>

   <head>

            <meta charset="utf-8">

​      <title>这是一个网页</title>

            <style type="text/css">

​         .p1{

​            background-color:yellow !important;

​         }

​         

​      

​      </style>

   </head>

   <body>

            <p class="p1" id="p2" style="background-color:blue;">我是一个段落

​      <span>我是一个p标签</span>

​      </p>

   </body>

</html>

1

2

3

4

5

6

7

8

9

10

11

12

13

14

15

16

17

18

19

效果：

 

分析：尽管我们采用了内联样式设置背景颜色为黄色，但是我们在类选择器中用了!important,因此该类选择器的优先级最高，故背景颜色为黄色。

 

伪类的顺序

:link 未访问的链接的颜色状态

:visited 访问过的链接的颜色状态

:hover 将鼠标移入链接时，链接的颜色状态

:active 激活链接时，链接的颜色状态

1

2

3

4

这几个的优先级是一样的，顺序按照上面的顺序写，这样才不会出错。记忆方法：LVhao（LV牌子的包包hao）

 

文本标签

em:语气上的强调，默认斜体显示

strong:强调内容，比em更加强烈，默认使用粗体显示。

i:标签中的内容会以斜体显示

b:标签中的内容会以加粗显示

H5规范中规定：对于不需要着重强调的内容而是单纯的加粗或者斜体，则用这两个标签。

small:标签中的内容会比他的父元素的文章的内容小一些。在h5中使用small标签来表示一些细则一类的内容。

big:标签中的内容比父元素的文字大，没有语义。

cite:网页中所有加有书名号的内容都可以使用cite标签，表示参考的内容。

q:表示短的引用（行内引用）

引用后的效果：

 

blockquote:表示一个长引用(块级引用)

sup:设置一个上标

sub:设置一个下标

例子：

 

<!DOCTYPE html>

<html>

   <head>

            <meta charset="utf-8">

​      <title>这是一个网页</title>

            <style type="text/css">

​         

​      

​      </style>

   </head>

   <body>

            <p>

​         明朝<sup><a href="#">[1]</a></sup>

​      </p>

​      

   </body>

</html>

1

2

3

4

5

6

7

8

9

10

11

12

13

14

15

16

17

效果：

 

del：标签中的内容会有一个横线删除

例子：

 

<!DOCTYPE html>

<html>

   <head>

            <meta charset="utf-8">

​      <title>这是一个网页</title>

            <style type="text/css">

​         

​      

​      </style>

   </head>

   <body>

            <p>

​         <del>1000</del>

​      </p>

            <p>9.98</p>
   </body>

</html>

1

2

3

4

5

6

7

8

9

10

11

12

13

14

15

16

17

效果：

 

ins:表示一个插入的内容，会添加下划线。

pre:是一个预格式标签，会将其中的格式保存，不会忽略多个空格。

code:专门用于表示代码

 

无序列表和有序列表

列表就相当于去超市购物时的那个购物清单，在HTML中也可以创建列表，在网页中一共有三中列表。

 

无序列表

有序列表

定义列表

1.无序列表

使用ul标签来创建一个无序列表

使用li在ul中创建一个一个的列表项，一个li就是一个列表项。

<body>

​      <ul>

​         <li>西门大官人</li>

​         <li>荣大官人</li>

​         <li>许大官人</li>

​         <li>柴大官人</li>

​      </ul>

   </body>

1

2

3

4

5

6

7

8

效果;

 

去掉项目符号：

 

<style type="text/css">

​         /* 去掉项目符号 */

​         ul{list-style:none;}

​      </style>

1

2

3

4

效果：

 

ul和li都是块元素。

2.有序列表

有序列表和无序列表类似，只不过它使用ol来代替ul。

 

type属性，可以指定序号的类型

   可选值：

​        1.默认值，使用阿拉伯数字

​        2.a/A 采用小写或者大写字母作为序号

​        3.i/I采用小写或者大写罗马数字作为序号

1

2

3

4

5

例子：

 

<!DOCTYPE html>

<html>

   <head>

            <meta charset="utf-8">

​      <title>这是一个网页</title>

            <style type="text/css">

​         

​      </style>

   </head>

   <body>

​      <ol>

​         <li>西门大官人</li>

​         <li>荣大官人</li>

​         <li>许大官人</li>

​         <li>柴大官人</li>

​      </ol>

​      <ol type="A">

​         <li>西门大官人</li>

​         <li>荣大官人</li>

​         <li>许大官人</li>

​         <li>柴大官人</li>

​      </ol>

​      <ol type="i">

​         <li>西门大官人</li>

​         <li>荣大官人</li>

​         <li>许大官人</li>

​         <li>柴大官人</li>

​      </ol>

   </body>

</html>

 

1

2

3

4

5

6

7

8

9

10

11

12

13

14

15

16

17

18

19

20

21

22

23

24

25

26

27

28

29

30

31

效果：

 

列表之间可以互相嵌套，可以在无序列表中放入有序等等。

例子：

 

<!DOCTYPE html>

<html>

   <head>

            <meta charset="utf-8">

​      <title>这是一个网页</title>

            <style type="text/css">

​         

​      </style>

   </head>

   <body>

            <p>菜谱</p>
​      <ul>

​         <li>鱼香肉丝</li>

​         <ol>

​            <li>鱼</li>

​            <li>香</li>

​            <li>肉丝</li>

​         </ol>

​         <li>宫保鸡丁</li>

​         <ul>

​            <li>宫保</li>

​            <li>鸡丁</li>

​         </ul>

​         <li>青椒肉丝</li>

​      </ul>

​      

   </body>

</html>

1

2

3

4

5

6

7

8

9

10

11

12

13

14

15

16

17

18

19

20

21

22

23

24

25

26

27

28

效果：

 

3.定义列表

用来对一些词汇或者内容进行定义。

比如：

 

胡萝卜：一种蔬菜

1

使用dl来创建一个定义列表。

 

dl中有两个子标签

   dt:被定义的内容

   dd:对被定义内容做描述

1

2

3

<!DOCTYPE html>

<html>

   <head>

            <meta charset="utf-8">

​      <title>这是一个网页</title>

            <style type="text/css">

​         

​      </style>

   </head>

   <body>

​      <dl>

​         <dt>武松</dt>

​         <dd>打虎英雄，战斗力 99</dd>

​         

​         <dt>武大</dt>

​         <dd>著名餐饮企业家，战斗力0</dd>

​      </dl>

   </body>

</html>

1

2

3

4

5

6

7

8

9

10

11

12

13

14

15

16

17

18

19

效果：

 

同意dl和ul和ol之间都可以互相嵌套。

 

长度单位

像素：px,像素是在网页中使用的最多的单位，一个像素相当于我们屏幕中的一个小点，我们的屏幕实际上就是由这些像素点构成的。但是这些像素点是不能直接看见的，不同的显示器一个像素的大小也不同，显示效果越好越清晰，像素越小，反之越大。

百分比：%，也可以将单位设置一个百分比的形式，这样浏览器将会根据其父元素的样式来计算该值，使用百分比的好处是，当父元素的属性值发生变化的时候，子元素也会按照比例发生改变。在我们创建一个自适应的页面时，经常使用百分比作为单位。

例子：

 

<!DOCTYPE html>

<html>

   <head>

            <meta charset="utf-8">

​      <title>这是一个网页</title>

            <style type="text/css">

​         /* 像素 */

​         .box{

​            width:200px;

​            height:200px;

​            background-color:red;

​         }

​         /* 百分比 */

​         .box1{

​            width:50%;

​            height:50%;

​            background-color:yellow;

​         }

​      </style>

   </head>

   <body>

            <div class="box">

                  <div class="box1"></div>
​      </div>

   </body>

</html>

1

2

3

4

5

6

7

8

9

10

11

12

13

14

15

16

17

18

19

20

21

22

23

24

25

26

效果：

 

当父元素红色正方变大，子元素也会变大。

em和百分比类似，它是相对于当前元素的字体大小来计算的。

 

1em = 1 font-size

1

使用em时，当字体大小发生改变时，em也会随之改变，当设置字体相关的样式时，经常会使用em。

例子：

 

<!DOCTYPE html>

<html>

   <head>

            <meta charset="utf-8">

​      <title>这是一个网页</title>

            <style type="text/css">

​         /* 像素 */

​         .box{

​            width:200px;

​            height:200px;

​            background-color:red;

​         }

​         /* 百分比 */

​         .box1{

​            font-size:100px;

​            width:0.5em;

​            height:50%;

​            background-color:yellow;

​         }

​      </style>

   </head>

   <body>

            <div class="box">

                  <div class="box1"></div>
​      </div>

   </body>

</html>

1

2

3

4

5

6

7

8

9

10

11

12

13

14

15

16

17

18

19

20

21

22

23

24

25

26

27

效果：

 

 

RGB值

颜色单位；在CSS中可以直接使用颜色的单词来表示不同的颜色。也可以使用RGB值来表示颜色。

所谓的RGB值指的是通过Red Green Blue三元色，通过这三种颜色的不同浓度来表示不同的颜色。

例子：

 

rgb(红色浓度，绿色的浓度，蓝色的浓度)

   -颜色的浓度需要一个0-255之间的值，255表示最大，0表示最小。

   -浓度也可以采用一个百分数来设置，需要一个0%-100%之间的数字，使用百分数最终也会转换为0-255之间的数。0%表示0；100%表示255.

1

2

3

十六进制RGB值表示颜色

也可以使用十六进制的RGB值来表示颜色，原理和上边RGB原理一样，只不过使用十六进制数来代替，使用三组两位的十六进制数组来表示一个颜色。

语法：#红色绿色蓝色

00：表示没有，相当于rgb中的0；ff表示最大，相当于rgb中的255.

两位两位重复的颜色可以简写，比如：

\#ff0000可以写成#f00

 

字体样式

浏览器中一般默认的文字大小为16px。font-size设置的不是文字本身的大小，每个页面中，每个文字都是处在一个看不见的框中，我们设置的font-size实际上设置的是格的高度，并不是字体大小，一般情况下文字比这个格小一些，也会比格大，根据字体的不同，显示效果也不同。

当采用某种字体时，如果浏览器支持则使用该字体，如果字体不支持，则使用默认字体。可以同时指定多个字体，这时浏览器会优先使用前边的字体，如果前边没有在尝试下一个。

例子：

 

<!DOCTYPE html>

<html>

   <head>

            <meta charset="utf-8">

​      <title>这是一个网页</title>

            <style type="text/css">

​         .p1{

​            color:red;

​            font-size:20px;

​            font-family:华文彩云,arial,微软雅黑;

​         }

​      

​      </style>

   </head>

   <body>

            <p class="p1">我是一个p标签，ABCDefg</p>
   </body>

</html>

1

2

3

4

5

6

7

8

9

10

11

12

13

14

15

16

17

18

效果：

 

 

字体分类

在网页中将字体分成5大类：

 

一般会将字体的大分类指定为font-family中的最后一个字体，防止前面的字体无法在浏览器中实现。

例子：

 

<!DOCTYPE html>

<html>

   <head>

            <meta charset="utf-8">

​      <title>这是一个网页</title>

            <style type="text/css">

​         .p1{

​            color:red;

​            font-size:20px;

​            font-family:华文彩云,arial,微软雅黑;

​         }

​      

​      </style>

   </head>

   <body>

            <p style="font-size:50px;font-family:serif;">衬线字体ABCDefg</p>
            <p style="font-size:50px;font-family:sans-serif;">非衬线字体ABCDefg</p>
            <p style="font-size:50px;font-family:monospace;">等宽字体ABCDefg</p>
            <p style="font-size:50px;font-family:cursive;">草书字体ABCDefg</p>
            <p style="font-size:50px;font-family:fantasy;">虚幻字体ABCDefg</p>
   </body>

</html>

1

2

3

4

5

6

7

8

9

10

11

12

13

14

15

16

17

18

19

20

21

22

效果：

 

 

文本样式二

font-style可以用来设置文字的斜体。

 

可选值：

​      normal,默认值，文字正常显示。

​      italic 文字会以斜体表示。

​      oblique 文字会以倾斜的效果显示。

1

2

3

4

大部分浏览器都不会对倾斜和斜体做区分，也就是说我们设置italic和oblique它们的效果往往是一样的。一般我们只会使用italic。

 

<style type="text/css">

​         .p1{

​            color:red;

​            font-size:30px;

​            font-family:微软雅黑;

​            font-style:italic;

​         }

​      </style>

1

2

3

4

5

6

7

8

font-weight可以用来设置文本的加粗效果；

 

可选值：

normal 文字正常显示

bold 文字加粗显示

1

2

3

该样式也可以指定100-900之间的9个值，但是由于用户的计算机往往没有这么多级别的字体，所以达到我们想要的效果也就是200，有可能比200粗，但是也有可能是一样的。

 

<style type="text/css">

​         .p1{

​            font-weight:600;

​         }

​      </style>

1

2

3

4

5

font-variant可以用来设置小型大写字母。

 

可选值：

   normal,默认值，文字正常显示

   small-caps 文字以小型大写字母显示

1

2

3

小型大写字母：将所有的字母都以大写形式显示，但是小写字母的大写要比大写字母的大小小一些。

例子：

 

<!DOCTYPE html>

<html>

   <head>

            <meta charset="utf-8">

​      <title>这是一个网页</title>

            <style type="text/css">

​         .p1{

​            font-weight:600;

​            font-variant:small-caps;

​         }

​         

​      </style>

   </head>

   <body>

            <p class="p1">我是一段文字ABCabc</p>
   </body>

</html>

1

2

3

4

5

6

7

8

9

10

11

12

13

14

15

16

17

效果：

 

分析：小写字母变成大写的，但是比原本大写的要小一些。

在css中还为我们提供了一个样式叫font，使用该样式可以同时设置字体相关的所有样式。

可以将字体的格式的值统一写在font格式中，不同的值之间使用空格隔开，使用font设置字体样式时，文字的大小和字体必须写，而且字体放在最后，文字的大小放在倒数第二。

 

.P3{

​            font:italic small-caps bold 60px "微软雅黑";

​         }

1

2

3

行高

在css中并没有为我们提供一个直接设置行间距的方式，我们只能通过设置行高来间接的设置行间距，行高越大行间距越大，使用line-height来设置行高。行高类似于单线本，单线本是一行一行，线与线之间的距离就行高，网页中的文字实际上也是写在一个看不见的线中的，而文字会默认在行高中垂直居中显示。

 

行间距=行高-字体大小

1

通过设置line-height可以间接的设置行高，

 

可以接受的值：

​      1.直接接收一个大小

​      2.可以指定一个百分数，则会相对于字体去计算行高

​      3.可以直接传一个数值，则行高会设置字体大小相应的倍数。

1

2

3

4

设置代码：

 

<style type="text/css">

​         .p1{

​            font-size:30px;

​            line-height:40px;

​            /* 百分数 */

​            line-height:200%;

​            /* 倍数 */

​            line-height:2;

​         }

​      </style>

1

2

3

4

5

6

7

8

9

10

对于当行文本来说，可以将行高设置为和父元素的高度一致，这样可以是单行文本在父元素中垂直居中。

例子:

 

<!DOCTYPE html>

<html>

   <head>

            <meta charset="utf-8">

​      <title>这是一个网页</title>

            <style type="text/css">

​         .box{

​            width:200px;

​            height:200px;

​            background-color:#bfa;

​            

​            line-height:200px;

​         }

​      </style>

   </head>

   <body>

            <div class="box"><a href="#">我是一个链接</a></div>
   </body>

</html>

1

2

3

4

5

6

7

8

9

10

11

12

13

14

15

16

17

18

19

效果：

 

在font中也可以指定行高，在字体后可以添加/行高来指定行高，该值是可选的，如果不指定则会使用默认值。

例子：

 

<!DOCTYPE html>

<html>

   <head>

            <meta charset="utf-8">

​      <title>这是一个网页</title>

            <style type="text/css">

​         .p1{

​            font:30px/80px 华文彩云;

​         }

​      </style>

   </head>

   <body>

            <p class="p1">旗下拥有：专业的中文IT技术社区： CSDN.NET；移动端开发者专属APP： CSDN APP、CSDN学院APP；新媒体矩阵微信公众号：CSDN资讯、程序人生、GitChat、CSDN学院、AI科技大本营、区块链大本营、CSDN云计算、GitChat精品课、人工智能头条、CSDN企业招聘；IT技术培训学习平台： CSDN学院；技术知识移动社区： GitChat；人工智能新社区： TinyMind；权威IT技术内容平台：《程序员》+ GitChat；IT人力资源服务：科锐福克斯；IT技术管理者平台：CTO俱乐部。</p>
   </body>

</html>

1

2

3

4

5

6

7

8

9

10

11

12

13

14

15

效果：

 

如果按照下面的写法，则行高设置失败，这是因为我们设置的行高被font中的默认行高覆盖。

 

<style type="text/css">

​         .p1{

​            line-height:60px;

​            font:30px/80px 华文彩云;

​         }

​      </style>

1

2

3

4

5

6

文本样式

text-transform可以用来设置文本的大小写

 

可选值：

​      none 默认值，该怎么显示就怎么显示，不做任何设置

​      capitalize 单词的首字母变成大写,通过空格来识别单词

​      uppercase 所有字母都变成大写

​      lowercase 所有的字母都变成小写

1

2

3

4

5

例子：

 

<!DOCTYPE html>

<html>

   <head>

            <meta charset="utf-8">

​      <title>这是一个网页</title>

            <style type="text/css">

​         .p1{

​            text-transform:uppercase;

​         }

​      </style>

   </head>

   <body>

            <p class="p1">We Are </p>
   </body>

</html>

1

2

3

4

5

6

7

8

9

10

11

12

13

14

15

效果：

 

text-decoration可以用来设置文本的修饰

 

可选值：

​         none：默认值，不添加任何修饰，正常显示

​         underline 为文本添加下划线

​         overline 添加上划线

​         line-through 添加删除线

1

2

3

4

5

超链接会默认添加下划线，也就是超链接的text-decoration的默认值是underline，如果需要去除超链接的下划线则需要将样式设置为none.

letter-spacing可以指定字符间距。

word-spacing可以指定单词与单词间的间距，实际上就是设置词与词之间的大小。

text-align:用于设置文本的对齐关系。

 

   可选值

​            left 默认值：靠左对齐

​            right 文本右对齐

​            center 文本居中对齐

​            justify 两端对齐，通过调整文本之间的空格大小， 来达到一个两端对齐的效果。

1

2

3

4

5

text-indent:用来设置首行缩进，当给它指定一个正值时，会自动想右侧缩进指定的像素，如果指定负值，则会向左侧移动指定的像素。通过用这种方式可以将一些不想显示的文字隐藏起来。一般使用em作为单位。

 

盒子模型的简介

非常重要，这是最重要的CSS知识点。

CSS处理网页时，它认为每个元素都包含在一个不可见的盒子里。

为什么要想象成盒子？因为如果把所有的元素都想象成盒子，那么我们对网页的布局就相当于是摆放盒子。我们只需要将相应的盒子摆放到网页中相应的位置即可完成网页的布局。

 

上图是盒子模型，中间的框是内容区。

内容区的设置：

使用width来设置盒子内容区的宽度，使用功能height来设置盒子内容区的高度，width和height只是设置盒子内容区的大小，而不是盒子的整个大小，盒子可见框的大小由内容区，内边距和边框共同决定。

边框的设置：

要为一个元素设置边框必须指定三个样式，缺一不可。

border-width:边框的宽度

border-color:边框的颜色

border-style:边框的样式

 

<!DOCTYPE html>

<html>

   <head>

            <meta charset="utf-8">

​      <title>这是一个网页</title>

            <style type="text/css">

​         .box1{

​            /* 

​             使用width来设置盒子内容区的宽度

​             使用功能height来设置盒子内容区的高度

​             width和height只是设置盒子内容区的大小，而不是

​             盒子的整个大小，盒子可见框的大小由内容区，内边距和边框

​             共同决定。

​             */

​            width:100px;

​            height:100px;

​            background-color:yellowgreen;

​            /* 为元素设置边框

​             要为一个元素设置边框必须指定三个样式

​               border-width:边框的宽度

​               border-color:边框的颜色

​               border-style:边框的样式

​             */

​            border-width:20px;

​            border-color:red;

​            border-style:solid;

​         }

​      

​      </style>

   </head>

   <body>

            <div class="box1"></div>
   </body>

</html>

1

2

3

4

5

6

7

8

9

10

11

12

13

14

15

16

17

18

19

20

21

22

23

24

25

26

27

28

29

30

31

32

33

34

效果：

 

 

分析：此时盒子的内容区大小不变，仍然是100px*100px，盒子的边框为红色的，整个盒子变大。

如果border-width指定了四个值，则四个值分别设置了上右下左(顺时针)。如果指定了三个值，则这三个值分别设置给上、左右、下。如果设置了两个值则分别设置给上下、左右。如果设置一个值，则四个边都是这个值，比如上面的例子。

设置四个值的例子：

 

<!DOCTYPE html>

<html>

   <head>

            <meta charset="utf-8">

​      <title>这是一个网页</title>

            <style type="text/css">

​         .box1{

​         

​            width:100px;

​            height:100px;

​            background-color:yellowgreen;

​         

​            border-width:10px 20px 30px 40px;

​            border-color:red;

​            border-style:solid;

​         }

​      

​      </style>

   </head>

   <body>

            <div class="box1"></div>
   </body>

</html>

1

2

3

4

5

6

7

8

9

10

11

12

13

14

15

16

17

18

19

20

21

22

23

效果：

 

除了border-width，css中还提供了四个border-xxx-eidthxxx的值可能是：top，right,bottom,left，专门设置指定边的宽度。

注：设置边框的三个样式都具有与border-width一样的规则。

大部分的浏览器中，边框的宽度和颜色都有默认值，而边框的样式的饿默认值都是none。

同时设置三个样式：

 

border

​      -边框的简写样式，通过它可以同时设置四个边框的样式，宽度，颜色，而且没有任何顺序要求。

​      border一指定就是同时指定四个边不能分别指定。

​      border-top,border-right,border-bottom,border-left,border能设置一条边。

1

2

3

4

例子：设置除了右边的其他三条边框。

 

<!DOCTYPE html>

<html>

   <head>

            <meta charset="utf-8">

​      <title>这是一个网页</title>

            <style type="text/css">

​         .box1{

​         

​            width:200px;

​            height:200px;

​            background-color:yellowgreen;

​         

​            border:solid 10px red;

​            border-right:none;

​         }

​      

​      </style>

   </head>

   <body>

            <div class="box1"></div>
   </body>

</html>

1

2

3

4

5

6

7

8

9

10

11

12

13

14

15

16

17

18

19

20

21

22

效果：

 

 

内边距

设置内边距：

内边距(padding)，指定盒子内容区与盒子之间的距离，一共有四个方向的内边距，可以通过四个属性设置：

 

 padding-top

 padding-bottom

 padding-right

 padding-left

1

2

3

4

内边距会影响可见框的大小，元素的背景会延伸到内边距。

例子：设置上边距盒子变大。

 

<!DOCTYPE html>

<html>

   <head>

            <meta charset="utf-8">

​      <title>这是一个网页</title>

            <style type="text/css">

​         .box1{

​         

​            width:200px;

​            height:200px;

​            background-color:green;

​         

​            /* 设置边框 */

​            border:10px red solid;

​            /* 

​             */

​            padding-top:100px;

​            }

​            .box2{

​               width:200px;

​               height:200px;

​               background-color:yellow;

​            }

​      </style>

   </head>

   <body>

            <div class="box1">

                  <div class="box2"></div>
​      </div>

   </body>

</html>

1

2

3

4

5

6

7

8

9

10

11

12

13

14

15

16

17

18

19

20

21

22

23

24

25

26

27

28

29

30

31

效果：

 

 

分析：绿色的是内边距，黄色的是内容区。

盒子的大小由内容区、内边距、边框共同决定。

 

使用padding可以同时设置四个边框的样式，规则和border-width一致。

 

外边距

外边距指的是当前盒子与其他盒子之间的距离，他不会影响可见框的大小，而是会影响到盒子的位置，盒子的四个方向的外边框：

 

margin-top

margin-right

margin-bottom

margin-left

1

2

3

4

由于页面中的元素都是靠左和靠上摆放，所以注意：当我们上和左边距时，会导致盒子自身的位置发生改变，而如果是设置右和下外边距会改变其他盒子的位置。

例子：

 

<!DOCTYPE html>

<html>

   <head>

            <meta charset="utf-8">

​      <title>这是一个网页</title>

            <style type="text/css">

​         .box1{

​         

​            width:200px;

​            height:200px;

​            background-color:green;

​         

​            /* 设置边框 */

​            border:10px red solid;

​            margin-top:100px;

​            margin-left:100px;

​            margin-bottom:100px;

​            }

​         .box2{

​         

​            width:200px;

​            height:200px;

​            background-color:yellow;

​            }

​      </style>

   </head>

   <body>

            <div class="box1">      </div>
            <div class="box2"></div>


   </body>

</html>

1

2

3

4

5

6

7

8

9

10

11

12

13

14

15

16

17

18

19

20

21

22

23

24

25

26

27

28

29

30

31

32

效果：

 

外边距也可以指定为一个负值，如果外边距设置的是负值，则元素往反方向移动。

margin还可以设置为auto，auto一般只设置给水平方向的margin。如果只指定左外边距或者右外边距的margin为auto，则会将外边距设置为最大值。垂直方向外边距如果设置为auto，则外边距默认值为0.

如果将margin-left和margin-right同时设置为auto，则会将两则的外边距设置为相同的值，既可以使得元素自动在父元素中水平居中。

外边距同样可以使用简写属性margin，同时设置四个外边距，规则和padding

一行。

 

垂直外边距的重叠

在网页中垂直方向的相邻外边距会发生外边距的重叠，所谓的外边距重叠指兄弟元素之间的相邻外边距会取最大值而不是取和。

例子：

 

<!DOCTYPE html>

<html>

   <head>

            <meta charset="utf-8">

​      <title>这是一个网页</title>

            <style type="text/css">

​         .box1{

​         

​            width:200px;

​            height:200px;

​            background-color:green;

​            margin-bottom: 100px;

 

​            }

​            

​         .box2{

​         

​            width:200px;

​            height:200px;

​            background-color:yellow;

​            margin-top: 200px;

​            }

​      </style>

   </head>

   <body>

            <div class="box1">      </div>
            <div class="box2"></div>


   </body>

</html>

1

2

3

4

5

6

7

8

9

10

11

12

13

14

15

16

17

18

19

20

21

22

23

24

25

26

27

28

29

30

效果

 

空白处是200而不是300px。

发生外边距重叠需要两个因素：两个盒子相邻且是在垂直方向上发生。

如果父子元素的垂直外边距相邻了，则子元素的外边距会设置给父元素。

例子：

 

<!DOCTYPE html>

<html>

   <head>

            <meta charset="utf-8">

​      <title>这是一个网页</title>

            <style type="text/css">

​         .box3{

​               width:200px;

​               height:200px;

​               background-color:red;

​            }

​         .box4{

​               width:100px;

​               height:100px;

​               background-color:yellowgreen;

​            }

​      </style>

   </head>

   <body>

            <div class="box3">

                  <div class="box4"></div>
​      </div>

   </body>

</html>

 

效果：

 

 

浏览器默认样式

浏览器为在页面中没有样式时，也可以让页面有一个比较好的显示效果，所以为很多元素都设置了一些默认的margin和padding，它的这些默认样式，正常情况下我们是不需要使用的，所以我们往往在编写样式之前需要将浏览器中默认的样式统统去掉。

采用下面的代码可去除浏览器默认样式：

 

   *{

​               matgin:0;

​               padding:0;

​            }

1

2

3

4

内联元素不能设置width和height。设置水平内边距，内联元素可以设置水平方向的内边距。内联元素可以设置边框，但是垂直的边框不会影响到页面布局。

内联元素支持水平方向的外边距。水平方向的外边距不会重叠。而是求和。内联元素不支持垂直外边距。

 

display和visibility

将一个内联元素变成块元素，通过display样式可以修改元素的类型。

 

可选值：

​      inlien:可以将一个元素作为内联元素显示

​      block:可以将一个元素设置为块元素显示

​      inline-block:将一个元素转换为行内块元素显示

​            -可以使得一个元素既有行内元素特点又有块元素特点，既可以设置宽高，又不会独占一行。

​      none表示不显示元素，并且元素不会在页面中继续占有位置。

1

2

3

4

5

6

例子：

 

<!DOCTYPE html>

<html>

   <head>

            <meta charset="utf-8">

​      <title>这是一个网页</title>

            <style type="text/css">

​         a{

​            background-color:green;

​            display:inline-block; 

​            width:200px;

​            height:200px;

​         }

​      

​      </style>

   </head>

   <body>

            <a href="#">我是一个大大的超链接</a>

​      <span>哈哈</span>

   </body>

</html>

1

2

3

4

5

6

7

8

9

10

11

12

13

14

15

16

17

18

19

20

效果：

 

visibility

 

可以用来设置元素的隐藏和显示的状态

hidden 元素隐藏不显示，使用该元素隐藏的元素虽然不会在页面中显示，但是位置依然保存。

1

2

例子：

 

<!DOCTYPE html>

<html>

   <head>

            <meta charset="utf-8">

​      <title>这是一个网页</title>

            <style type="text/css">

​      

​         .box{

​            width:100px;

​            height:100px;

​            background-color:red;

​            visibility: hidden;

​            

​         }

​      

​      </style>

   </head>

   <body>

            <div class="box"></div>
            <p>哈哈</p>
   </body>

</html>

1

2

3

4

5

6

7

8

9

10

11

12

13

14

15

16

17

18

19

20

21

22

效果：

 

 

overflow

子元素是默认存在于父元素的内容区中，理论上讲子元素的最大可以等于父元素内容区大小，如果子元素的大小超过了父元素的内容区，则超过的大小在父元素以外的位置显示，超出父元素的内容，我们称为溢出的内容。

父元素默认将溢出内容，在父元素外边显示。

例子：

 

<!DOCTYPE html>

<html>

   <head>

            <meta charset="utf-8">

​      <title>这是一个网页</title>

            <style type="text/css">

​      

​         .box1{

​            width:200px;

​            height:200px;

​            background-color:red;  

​         }

​         .box2{

​            width:100px;

​            height:500px;

​            background-color:yellow;   

​         }

​      

​      </style>

   </head>

   <body>

            <div class="box1">

                  <div class="box2"></div>
​      </div>

​      

   </body>

</html>

效果：

 

通过overflow可以设置父元素如何处理溢出内容。

 

可选值：

   visible,默认值，不会对溢出的内容做任何改变。

   hidden,溢出的内容会被修剪，不会显示。

   scroll，会为父元素添加滚动条，通过拖动滚动条查看。该属性无论内容是否溢出都会添加水平和垂直方向的滚动条。

   auto，会根据需求自动添加滚动条，需要水平就添加水平，需要垂直就添加垂直。

 

文档流

文档流处在网页的最底层，它表示的是一个页面中的位置，我们所创建的元素都默认处在文档流中。

元素在文档流中的特点

 

块元素

   1.块元素在文档流中会独占一行，块元素会自上向下排列。

   2.块元素在文档流中默认宽度是父元素的100%。

   3.块元素在文档流中高度默认被内容区撑开。

1

2

3

4

例子：

 

<!DOCTYPE html>

<html>

   <head>

            <meta charset="utf-8">

​      <title>这是一个网页</title>

            <style type="text/css">

​      

​      

   

​      </style>

   </head>

   <body>

            <div style="width:100px;height:100px;background-color:yellow;"></div>
            <div style="width:100px;height:100px;background-color:red;"></div>
   </body>

</html>

效果：

 

 

内联元素

   1.内联元素在文档流中只占自身的大小，会默认从左向右排列。如果一行中不足以容纳所有的内联元素，则自动换到下一行，继续自左向右排列。

   2.在文档流中，内联元素的宽度和高度默认都被内容撑开。

例子:

 

<!DOCTYPE html>

<html>

   <head>

            <meta charset="utf-8">

​      <title>这是一个网页</title>

            <style type="text/css">

​      

​      

   

​      </style>

   </head>

   <body>

​      <span style = "background-color:yellowgreen;">我是一个span</span>

​      <span style = "background-color:yellowgreen;">我是一个span</span>

​      <span style = "background-color:yellowgreen;">我是一个span</span>

​      <span style = "background-color:yellowgreen;">我是一个span</span>

​      <span style = "background-color:yellowgreen;">我是一个span</span>

​      

   </body>

</html>

1

2

3

4

5

6

7

8

9

10

11

12

13

14

15

16

17

18

19

20

结果：

 

 

浮动

在文档流中，块元素默认是垂直排列。

如果希望块元素在页面中水平排列，可以使得块元素脱离文档流。

使用float来使元素浮动，从而脱离文档流。

 

可选值

   none，默认值，元素默认在文档流中排列

   left，元素会立即脱离文档流，向页面的左侧浮动

   right，元素会立即脱离文档流，向页面的右侧浮动

1

2

3

4

当为一个元素设置浮动以后（float属性是一个非none的值），元素会立即脱离文档流，元素脱离文档流以后会向上移动。

元素浮动以后，会尽量向页面的左上或右上漂浮，直到遇到父元素的边框或者其他浮动元素。

例子：

 

<!DOCTYPE html>

<html>

   <head>

            <meta charset="utf-8">

​      <title>这是一个网页</title>

            <style type="text/css">

​         .box1{

​            width:200px;

​            height:200px;

​            background-color:red;

​            float:left;

​            

​         }

​         .box2{

​            width:200px;

​            height:200px;

​            background-color:yellow;

​            float:left;

​         }

​         .box3{

​            width:200px;

​            height:200px;

​            background-color:blue;

​            float:left;

​         }

   

​      </style>

   </head>

   <body>

            <div class="box1"></div>
            <div class="box2"></div>
            <div class="box3"></div>
   </body>

</html>

 

效果：

 

如果浮动元素上边是一个没有浮动的块元素，则浮动元素不会超过块元素。浮动的元素不会超过他上边的兄弟元素，最多一边对齐。

浮动的元素不会盖住文字，文字会自动环绕在浮动元素的周围，可以通过设置浮动文字环绕图片的效果。

例子：

 

<!DOCTYPE html>

<html>

   <head>

            <meta charset="utf-8">

​      <title>这是一个网页</title>

            <style type="text/css">

​         .box1{

​            width:200px;

​            height:200px;

​            background-color:red;

​            float:left;

​            

​         }

​         .p1{

​            

​            background-color:yellow;

​         }

​         *{

​            margin:0;

​            padding:0;

​         }

   

​      </style>

   </head>

   <body>

            <div class="box1"></div>
            <p class="p1">哔哩哔哩（bilibili）现为国内领先的年轻人文化社区，该网站于2009年6月26日创建，被粉丝们亲切的称为“B站”。

B站的特色是悬浮于视频上方的实时评论功能，爱好者称其为“弹幕”，这种独特的视频体验让基于互联网的弹幕能够超越时空限制，构建出一种奇妙的共时性的关系，形成一种虚拟的部落式观影氛围，让B站成为极具互动分享和二次创造的文化社区。B站目前也是众多网络热门词汇的发源地之一。</p>

   </body>

</html>

 

效果：

 

在文档流中，子元素的宽度默认占父元素全部。

当元素设置浮动以后，会完全脱离文档流。块元素脱离文档流以后，高度和宽度都被内容撑开。

内联元素脱离文档流以后会变成块元素，一旦脱离文档流都是块元素。

 

简单布局

完成下图的网页布局：

 

实现代码：

 

<!DOCTYPE html>

<html>

   <head>

            <meta charset="utf-8">

​      <title>这是一个网页</title>

            <style type="text/css">

​         *{

​            margin:0;

​            padding:0;

​         }

​         .header{

​            width:1000px;

​            height:150px;

​            background-color:yellowgreen;

​         

​            /* 居中 */

​            margin:0 auto;

​         }

​         .content{

​         

​            width:1000px;

​            height:400px;

​            background-color:orange;

​            /* 居中 */

​            margin:10px auto;

​         }

​         .left{

​            width:200px;

​            height:100%;

​            background-color:skyblue;

​            float:left;

​         }

​         .center{

​            width:580px;

​            height:100%;

​            background-color:yellow;

​            float:left;

​            margin:0 10px;

​         }

​         .right{

​            width:200px;

​            height:100%;

​            background-color:pink;

​            float:left;

​         }

​         .footer{

​         

​            width:1000px;

​            height:150px;

​            background-color:red;

​            margin:0 auto;

​         }

​         

​      

   

​      </style>

   </head>

   <body>

​      <!-- 头部div -->

            <div class="header"></div>
​      <!-- 主题内容div -->

            <div class="content">

                  <div class="left"></div>
                  <div class="center"></div>
                  <div class="right"></div>
​      </div>

​      <!-- 底部信息div -->

            <div class="footer"></div>
   </body>

</html>

1

2

3

4

5

效果：

 

 

高度塌陷

在文档流中，父元素的高度默认是被子元素撑开的，也就是子元素多高，父元素就多高。

例子：

 

<!DOCTYPE html>

<html>

   <head>

            <meta charset="utf-8">

​      <title>这是一个网页</title>

            <style type="text/css">

​         .box1{

​            border: 10px red solid;

​         }

​         .box2{

​            width:100px;

​            height:100px;

​            background-color:blue;

​         }

​         

​      

   

​      </style>

   </head>

   <body>

            <div class="box1">

                  <div class="box2"></div>
​      </div>

   </body>

</html>

结果：

 

在上面的基础上，为子元素设置浮动以后，子元素会完全脱离文档流，此时将会导致子元素无法撑起父元素的高度，导致父元素的高度塌陷。

在上面的例子中加入浮动：