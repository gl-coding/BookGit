# 第3节：组件前端Vue

#vue全家桶

vue2 + vuex + vue-router + webpack + ES6/7 + fetch + sass + flex + svg

##Vue.js 浅谈单页应用和多页应用

## 多页面

1. **多页面应用：每次页面跳转，后台都会返回一个新的HTML文档，就是多页面应用。**
2. 在以往传统开发的应用（网站）大多都是多页面应用，路由由后端来写。

> ![mpa](https://image-static.segmentfault.com/134/071/1340714692-5c871f636e043_articlex)

> 页面跳转=》返回HTML，优点：首屏时间快，SEO效果好，缺点是页面切换慢。

- 首屏时间快？访问页面，服务器只需要返回一个HTML文件，这个过程就经历了一个HTTP请求，请求响应回来，页面就能被展示出来。
- SEO（搜索引擎排名）效果好？搜索引擎能识别HTML的内容，根据内容进行排名。
- 页面切换慢：每一次切换页面都需要发起一个HTTP请求，假设网络较慢就会出现卡顿情况。

## 单页面

1. **单页应用：用vue写的项目是单页应用，刷新页面会请求一个HTML文件，切换页面的时候，并不会发起新的请求一个HTML文件，只是页面内容发生了变化**
2. vue.js原理：JS感知URL变化，当URL发生变化后，使用JS动态把当前的页面内容清除掉，再把下一个页面的内容挂载到页面上。此时的路由就不是后端来做了，而是前端来做，判断页面到底显示哪一个组件，再把以前的组件清除掉使用新的组件。就不会每一次跳转都请求HTML文件。

> ![spa](https://image-static.segmentfault.com/426/425/4264253619-5c87227d1743f_articlex)

> 页面跳转 =》 JS渲染，优点页面切换快，缺点首屏时间稍慢，SEO差

- 首屏时间慢？请求HTML还有JS的请求。（在此我想问：HTML里面不也有JS请求嘛？这一点是在看知乎上某个大神说的，没明白，但我觉得HTML里的JS大多是操作DOM的，因此跟HTML文件可以理解成一个请求。而vue.js则是负责整个应用的逻辑的，所以又得另算一个逻辑请求时延。）

- 页面切换快？页面跳转不需要去做HTML文件的请求，节约HTTP请求发送的时延。

- SEO差？搜索引擎只认识HTML内容不认识JS内容。单页应用的渲染都是靠JavaScript渲染出来的。搜索引擎不好识别排名。

  

### 有上面这么多的问题，为什么当下的前端开发中还要使用VUE开发单页应用？

- **vue中还有服务器端渲染的解决方案，完美解决上述问题。**

总结如下：

  单页面应用指一个系统只加载一次资源，然后下面的操作交互、数据交互是通过router、ajax来进       行，页面并没有刷新；
<1>在vue搭建的环境里面怎么有没有公用的css和js?如果有是怎么引用的？

      有公用的css和js，有两种引用的方法：（要深刻理解单页面应用程序哦，单页面就是引入后在哪里都能使用）
    
      1.全局公共引用样式和js文件


​       

   2.组件的引入 

  单页面的应用优点：

  1.分离前后端关注点，前端负责界面显示，后端负责数据存储和计算。不会把前后端的逻辑混杂在一起；

  2.减轻服务器压力，服务器只用出数据就可以；

  3.同一套后端程序代码，不用修改就可以用于Web界面、手机、平板等多种客户端；

  4.用户体验好、快，内容的改变不需要重新加载整个页面，web应用更具响应性和更令人着迷；

  5.SPA和RESTful架构一起使用，后端不再负责模板渲染、输出页面工作，web前端和各种移动终端地位对等，后端API通用化；

  

单页面的应用缺点：

1.初次加载耗时相对增多；
2.导航不可用，如果一定要导航需要自行实现前进、后退，需要程序来实现管理；
3.使用脚本修改页面，这个脚本我们都知道，他的兼容性是个大问题；

4. 不利于SEO问题，现在可以通过Prerender等技术解决一部分；

##webpack

本质上，*webpack* 是一个现代 JavaScript 应用程序的*静态模块打包器(module bundler)*。当 webpack 处理应用程序时，它会递归地构建一个*依赖关系图(dependency graph)*，其中包含应用程序需要的每个模块，然后将所有这些模块打包成一个或多个 *bundle*。

# 从零搭建vue+webpack项目安装

## 一 安装node

  vue项目搭建依赖node的npm包管理器，所以我们先得安装node，此处就不详细讲解其安装过程。

## 二 安装vue-cli

```
npm install -g vue-cli
```

安装成功后可以输入vue查看相关命令的使用，输入vue list可以查看vue可以用的模板:

![img](https://images2018.cnblogs.com/blog/825265/201804/825265-20180411153056486-511980029.png)

我们这里选择webpack模板：

```
vue init webpack projectName
```

输入上述命令，设置根据提示设置你的项目即可，如果不设置，一路回车就可以，以下是我的配置：

![img](https://images2018.cnblogs.com/blog/825265/201804/825265-20180411154858388-144229889.png)

以上，项目初始化完成，最后：

![img](https://images2018.cnblogs.com/blog/825265/201804/825265-20180411154947582-374044704.png)

可以看到，vue非常贴心的告诉你to get started,运行cd vue-test和npm run dev:

![img](https://images2018.cnblogs.com/blog/825265/201804/825265-20180411155556521-1451668436.png)

浏览器输入http://localhost:8080看见一下页面则大功告成啦：

![img](https://images2018.cnblogs.com/blog/825265/201804/825265-20180411155738703-1611661565.png)

回到项目路径下：

![img](https://images2018.cnblogs.com/blog/825265/201804/825265-20180411155833665-1228304494.png)

可以看见刚刚我们那一堆命令已经自动为我们生成一堆项目文件啦

项目目录讲解

![img](https://images2018.cnblogs.com/blog/825265/201804/825265-20180411160107401-789032956.png)

通过上一节，我们得到以上的项目目录：

build及config：webpack配置相关

node_modules:通过npm install安装的依赖代码库

src：项目源码

static：存放静态资源

----.gitkeep：意思是就算这是个空文件，仍旧可以提交到代码版本库（因为一般如果为空文件夹，git会忽略这个文件夹）中。

.babelrc：babel相关配置（因为我们的代码大多都是ES6，而大多浏览器是不支持ES6的，所以我们需要babel帮我们转换成ES5语法）

.editorconfig：编辑器的配置，可以在这里修改编码、缩进等

.eslintignore：设置忽略语法检查的目录文件

.eslintrc.js：eslint的配置文件

.gitignore：git忽略里面设定的这些文件的提交

index.html：入口html文件

package.json：项目的配置文件，用于描述一个项目，包括我们init时的设置、开发环境、生成环境的依赖插件及版本等。

package-lock.json：普通package.json文件“^2.0”这样写的，意味着版本可以大于等于2.0，如此就会出现各种错误。



##vuex

![img](https://ss2.baidu.com/6ONYsjip0QIZ8tyhnq/it/u=3746507390,1548579672&fm=173&app=49&f=JPEG?w=500&h=200&s=4DB1AC50E4A059010AD00F57020050F6)

如果你之前使用过vue.js，你一定知道在vue中各个组件之间传值的痛苦，在vue中我们可以使用vuex来保存我们需要管理的状态值，值一旦被修改，所有引用该值的地方就会自动更新，那么接下来我们就来学习一下vuex是如何修改状态值的：

我们新建一个vue项目（这里由于我们是讲解vuex，所以对于vue项目的创建我们不会讲解太详细）；在命令行输入 vue init webpack web（使用webpack创建一个项目名为web的项目）；

项目创建后，然后安装vuex，使用命令：npm install vuex --save（安装vuex保存到本地），安装成功后你会看到这个界面：

![img](https://ss0.baidu.com/6ONWsjip0QIZ8tyhnq/it/u=2734701558,2124673427&fm=173&app=49&f=JPEG?w=640&h=99)

然后我们执行npm run dev 启动项目，在浏览器输入："localhost:8080"；正常的话然后我们会看到项目的启动页，

![img](https://ss1.baidu.com/6ONXsjip0QIZ8tyhnq/it/u=2716087147,1198573266&fm=173&app=49&f=JPEG?w=640&h=520&s=4D803C72235A65CC587C41DD0000C0F2)

看到这个界面说明项目启动成功，然后我们在项目的src目录下新建一个目录store，在该目录下新建一个index.js文件，我们用来创建vuex实例，然后在该文件中引入vue和vuex，创建Vuex.Store实例保存到变量store中，最后使用export default导出store：

![img](https://ss2.baidu.com/6ONYsjip0QIZ8tyhnq/it/u=1859579942,68850159&fm=173&app=49&f=JPEG?w=640&h=349&s=E5DA2776311364651E7190CA0000C030)

然后我们在main.js文件中引入该文件，在文件里面添加 import store from ‘./store’;，再在vue实例全局引入store对象；

![img](https://ss1.baidu.com/6ONXsjip0QIZ8tyhnq/it/u=1691605006,1489505414&fm=173&app=49&f=JPEG?w=640&h=319&s=E75AA376139B64694861D9DF00008030)

然后我们就可以开始编写我们的vuex业务代码了，那么，我们的数据如何保存？

**State：**

vuex中的数据源，我们需要保存的数据就保存在这里，可以在页面通过 this.$store.state来获取我们定义的数据；

![img](https://ss1.baidu.com/6ONXsjip0QIZ8tyhnq/it/u=1400205445,3782005504&fm=173&app=49&f=JPEG?w=534&h=378&s=E77AA376194B404D485598DA00008032)

![img](https://ss2.baidu.com/6ONYsjip0QIZ8tyhnq/it/u=2372334884,2398783945&fm=173&app=49&f=JPEG?w=640&h=323&s=E55A23760B1B68431C79D0DE0000D031)

这时候我们页面上就得到了这个count值1：

![img](https://ss0.baidu.com/6ONWsjip0QIZ8tyhnq/it/u=2038357071,3728881452&fm=173&app=49&f=JPEG?w=370&h=459&s=4D803C72E3F073847D7F914D020090E2)

**Getters：**

Getter相当于vue中的computed计算属性，getter 的返回值会根据它的依赖被缓存起来，且只有当它的依赖值发生了改变才会被重新计算，这里我们可以通过定义vuex的Getter来获取，Getters 可以用于监听、state中的值的变化，返回计算后的结果，这里我们修改Hello World.vue文件如下：

![img](https://ss0.baidu.com/6ONWsjip0QIZ8tyhnq/it/u=1124938485,2036207992&fm=173&app=49&f=JPEG?w=640&h=233&s=E75AA3761BEA59200C5D20DB0000C032)

再修改index.js文件如下，其中getters中的getStateCount方法接收一个参数state，这个参数就是我们用来保存数据的那个对象；

![img](https://ss0.baidu.com/6ONWsjip0QIZ8tyhnq/it/u=1921550637,1430178875&fm=173&app=49&f=JPEG?w=640&h=271&s=E75A237687BA6429087C44CC00009032)

然后我们在页面显示：

![img](https://ss0.baidu.com/6ONWsjip0QIZ8tyhnq/it/u=3757051071,719618635&fm=173&app=49&f=JPEG?w=640&h=500&s=4DA03C726B5A76CC5E7D415D000050E2)

**Mutations：**

数据我们在页面是获取到了，但是如果我们需要修改count值怎么办？如果需要修改store中的值唯一的方法就是提交mutation来修改，我们现在Hello World.vue文件中添加两个按钮，一个加1，一个减1；这里我们点击按钮调用addFun（执行加的方法）和reductionFun（执行减法的方法），然后在里面直接提交mutations中的方法修改值：

![img](https://ss1.baidu.com/6ONXsjip0QIZ8tyhnq/it/u=2228905111,904599018&fm=173&app=49&f=JPEG?w=640&h=448&s=EF7AA356091E444D546D20DB00009031)

修改index.js文件，添加mutations，在mutations中定义两个函数，用来对count加1和减1，这里定义的两个方法就是上面commit提交的两个方法如下：

![img](https://ss0.baidu.com/6ONWsjip0QIZ8tyhnq/it/u=2913736281,4062485011&fm=173&app=49&f=JPEG?w=625&h=610&s=E77AA776090F654F48F501DA0000C032)

页面上点击+、- 按钮操作数据：

点击 “+”按钮

![img](https://ss1.baidu.com/6ONXsjip0QIZ8tyhnq/it/u=2553142864,605934454&fm=173&app=49&f=JPEG?w=625&h=586&s=4DA03C726B5E56CC5E5D914D000050E2)

执行成功，我们再连续点击三次减 “-” 按钮

![img](https://ss2.baidu.com/6ONYsjip0QIZ8tyhnq/it/u=3177576797,4127004431&fm=173&app=49&f=JPEG?w=640&h=597&s=4DA03C726B5A57CC0E54B14D0000E0E1)

ok！完美。

**Actions：**

我们看到，当点击三次后值从2变成了-1；页面上的值是改变了；我们达到了修改store中状态值的目的，但是，官方并不介意我们这样直接去修改store里面的值，而是让我们去提交一个actions，在actions中提交mutation再去修改状态值，接下来我们修改index.js文件，先定义actions提交mutation的函数：

![img](https://ss2.baidu.com/6ONYsjip0QIZ8tyhnq/it/u=445995293,2183698068&fm=173&app=49&f=JPEG?w=640&h=471&s=E75AA376031A446D04C521DA0000C032)

然后我们去修改Hello World.vue文件：

![img](https://ss2.baidu.com/6ONYsjip0QIZ8tyhnq/it/u=1625150480,2688445974&fm=173&app=49&f=JPEG?w=640&h=523&s=EFFAA356190F454D087D21DA0000C032)

这里我们把commit提交mutations修改为使用dispatch来提交actions；我们点击页面，效果是一样的。

![img](https://ss1.baidu.com/6ONXsjip0QIZ8tyhnq/it/u=524200192,111152114&fm=173&app=49&f=JPEG?w=640&h=614&s=CDA03C726B5A77CC5C7D415D0000C0F2)

![img](https://ss1.baidu.com/6ONXsjip0QIZ8tyhnq/it/u=3140260030,100455928&fm=173&app=49&f=JPEG?w=599&h=552&s=CDA03C726B5A66CC5E7D415D0200C0E2)

好了，我们这里已经实现了一个基本的vuex修改状态值的完整流程，如果我们需要指定加减的数值，那么我们直接传入dispatch中的第二个参数，然后在actions中的对应函数中接受参数在传递给mutations中的函数进行计算：

![img](https://ss2.baidu.com/6ONYsjip0QIZ8tyhnq/it/u=1750476689,3680419388&fm=173&app=49&f=JPEG?w=640&h=422&s=E7FAA7761B1A444D485D20D000005032)

![img](https://ss0.baidu.com/6ONWsjip0QIZ8tyhnq/it/u=1511832012,2160221297&fm=173&app=49&f=JPEG?w=640&h=270&s=E77AA376175A586100DCD5DA0000C030)

![img](https://ss0.baidu.com/6ONWsjip0QIZ8tyhnq/it/u=2367974535,3004418768&fm=173&app=49&f=JPEG?w=640&h=509&s=4DA03C726B5256CC0E55B14D0000A0E1)

这个时候我们再去点击“ - ”按钮就会发现不再是减1了，而是减去10了。

**mapState、mapGetters、mapActions**

如果我们不喜欢这种在页面上使用“this.$stroe.state.count”和“this.$store.dispatch('funName')”这种很长的写法，那么我们可以使用mapState、mapGetters、mapActions就不会这么麻烦了；

我们修改Hello World.vue文件如下：

![img](https://ss0.baidu.com/6ONWsjip0QIZ8tyhnq/it/u=3828043860,1588050571&fm=173&app=49&f=JPEG?w=640&h=628&s=EFFAA356490F454D5AEDA9DA02008030)

此时我们在页面使用count1调用：

![img](https://ss0.baidu.com/6ONWsjip0QIZ8tyhnq/it/u=2040125526,720641027&fm=173&app=49&f=JPEG?w=640&h=495&s=59863D723342554D547CD1CD000070B2)

正常显示，效果是一样的，我们就可以不再使用很长的写法来调用了。

# [less快速学习](https://www.cnblogs.com/fatty-yu/p/8758871.html)

写在前面：大概写这么个意思哈，注释样式什么的大家忽略掉哈哈哈

## **1 变量**

```
eg:
@test_width:300px
.box{
widht:@test_width;
htight:@test_width;
}
```

## 2 混合

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
.border{
border:1px solid pink;
}
.box{
widht:@test_width;
htight:@test_width;
.border;
}
//混合--带参数
 
.border2（@border_width）{
border:@border_width solid pink;
}
 
.test_border2{
.border2(30px);
}
 
// 混合--带默认值
.border3（@border_width：30px）{
border:@border_width solid pink;
}
 
.test_border3{
.border2();//border:30px solid pink;
}
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

## 3 匹配模式

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
//以三角形为例
.trianglt(top,@w:5px,@c:#ccc){
border-width:@w;
border-color:transparent transparent @w transparent;
border-style: dashed dashed solid dashed ;
}
.trianglt(right,@w:5px,@c:#ccc){
border-width:@w;
border-color:transparent transparent transparent @w;
border-style: dashed dashed dashed solid ;
}
 
//公共的，每个调用的就算传参不同，也会带
.trangle(@_,@w:5px,@c:#ccc){
width:0;
height:0;
overflow:hidden;
}
//调用
.sanjiao{
.trangle(top,100px);
}
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

## 4 运算

```
@test_01:300px;
.box_02{
width:(@test_01-20)*5;//这个20可带可不带单位，两者只要有一个有单位即可
}
```

## 5 嵌套

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
<ul>
<li><a></a><span></span></li>
</ul>
.list{
width:20px;
height:20px;
li{
float:left; //相当于 .list li
a{
color:#000;// .list li a
}
}
a{
color:#000;//.list a可写在li里，但是为了避免多层嵌套
&:hover{
color:red;//a:hover,&表示上一层选择器
}
}
}
@arguments
 
.border_arg(@w:30px,@c:red,@xx:solid){
border:@arguments;//border:@w @c @xx;
}
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

## 6 避免编译（忽略不编译）

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
.test{
width:~'calc(300px-30px)' //width:calc(300px-30px )
}
 
 
important
 
.test_important{
.test()!important;//width:30px!important;里面的每一个都会带上important
}
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

