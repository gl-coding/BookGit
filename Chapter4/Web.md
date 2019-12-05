# 第1节：网页前端

##less

LESS CSS使用方法 , CSS也能跟JS一样玩。

在使用CSS的时候，总会有这个想法：
这个属性值老是重复写好烦。
这个属性值我在前面那个CSS文件中写过，好想直接拿过来用。
CSS能不能像其他程序性语言一样用一个变量来代替需要重复利用的内容呢。
鉴于以上的想法并非我一人会想到，只要是写过前端代码的肯定都会思考过这个问题，无奈CSS基本可以说没有语法可依循，于是LESS框架应运而生。

什么是LESS
作为一门标记性语言，CSS 的语法相对简单，对使用者的要求较低，但同时也带来一些问题：CSS 需要书写大量看似没有逻辑的代码，不方便维护及扩展，不利于复用，尤其对于非前端开发工程师来讲，往往会因为缺少 CSS 编写经验而很难写出组织良好且易于维护的 CSS 代码，造成这些困难的很大原因源于 CSS 是一门非程序式语言，没有变量、函数、SCOPE（作用域）等概念
它在 CSS 的语法基础之上，引入了变量，Mixin（混入），运算以及函数等功能，大大简化了 CSS 的编写，并且降低了 CSS 的维护成本，就像它的名称所说的那样，LESS 可以让我们用更少的代码做更多的事情。

LESS的原理
本质上，LESS 包含一套自定义的语法及一个解析器，用户根据这些语法定义自己的样式规则，这些规则最终会通过解析器，编译生成对应的 CSS 文件。LESS 并没有裁剪 CSS 原有的特性，更不是用来取代 CSS 的，而是在现有 CSS 语法的基础上，为 CSS 加入程序式语言的特性。



安装

- node.js

- 命令行输入“npm install -g less"安装less；

  

直接引用LESS文件

如果想要直接在客户端使用 .less（LESS 源文件），只需要从 http://lesscss.org下载 less.js 文件，然后在需要引入 LESS 源文件的 HTML 中加入如下代码：

LESS 源文件的引入方式与标准 CSS 文件引入方式一样：

<link rel="stylesheet/less" type="text/css" href="index.less">

另外LESS是作用域的
简单的讲就是局部变量还是全局变量的概念，查找变量的顺序是先在局部定义中找，如果找不到，则查找上级定义，直至全局。

如：

 @width : 20px; 
 .index{ 
   @width : 30px; 
   .centerDiv{ 
       width : @width;// 此处应该取最近定义的变量 width 的值 30px 
              } 
 } 
 .leftDiv { 
     width : @width; // 此处应该取最上面定义的变量 width 的值 20px 
 }

最后，最后也是LESS最厉害的作用之一了，可以把LESS当成JS来玩。

@import "base-less.less";
@index-color: red;
.index-home {
    box-sizing: content-box;
    background-color: @index-color;
    color: @base-font-color;
    .marginTop(100px); 
}
.marginTop(@distance) {
    margin-top: @distance; 
}
