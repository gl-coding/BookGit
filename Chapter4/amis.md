# 第1节：可配置前端Amis

##Amis

一种页面渲染器，可以直接基于特定格式的JSON配置将页面渲染出来，结合业务方API可快速完成各类管理页面的开发。 

目前用于百度内部AMIS平台，已有100+部门接入使用，创建1.2w +页面，欢迎大家使用和提建议。

通过amis搭建自己的后台系统，可以参考这：https://github.com/fex-team/amis-admin

AMIS是做啥的

完全基于 JSON 的 mis 工具,，不需要前端就可以自己搭建信息管理系统，比如监控啊管理啊之类的，这是能让前端失业的一个框架。

这个截图所有的元素, 都由json控制, 不需要任何前端代码，十足的后端福利。

大概看下基本用法中的例子：

 

为了简化前端开发，amis Renderer 能够直接用配置就能将页面渲染出来。

 

先来看个简单的例子。

{

"$schema": "https://houtai.baidu.com/v2/schemas/page.json#",

"type": "page",

"title": "这是标题部分",

"subTitle": "这是子标题",

"remark": "这是小提示信息",

"aside": "这是侧边栏部分",

"body": "这是内容区",

"toolbar": "这是工具栏部分"

}

 

PS: 可以通过编辑器实时修改预览

 

从上面的内容可以看出，一个简单页面框架已经基本出来了，这是 amis 渲染器配置的入口。从 page 渲染器开始出发，通过在容器中放置不同的渲染器来配置不同性质的页面。

 

简单说明以上配置信息。

 

$schema 这个字段可以忽略，他是指定当前 JSON 配置是符合指定路径 https://houtai.baidu.com/v2/schemas/page.json 的 JSON SCHEMA 文件描述的。PS: 编辑器就是靠这个描述文件提示的，可以 hover 到字段上看效果。

 

type 指定渲染器类型，这里指定的类型为 page。更多渲染器类型可以去这里面查看。

 

title 从 title 开始就是对应的渲染模型上的属性了。这里用来指定标题内容。

 

subTitle 副标题.

 

remark 标题上面的提示信息

 

aside 边栏区域内容

 

body 内容区域的内容

 

toolbar 工具栏部分的内容

 

这里有三个配置都是容器类型的。aside、body 和 toolbar。

 

 

 

什么是容器类型？

 

 

 

容器类型表示，他能够把其他渲染类型放进来。以上的例子为了简单，直接放了个字符串。

 

 

 

字符串类型内部是把他当成了 tpl 渲染器来处理，在这里也可以通过对象的形式指定，如以下的例子的 body 区域是完全等价的。

 

{

"$schema": "https://houtai.baidu.com/v2/schemas/page.json",

"type": "page",

"body": {

"type": "tpl",

"tpl": "这是内容区"

}

}

 

容器内可以直接放一个渲染器，也可以放多个，用数组包起来即可如：

 

{

"$schema": "https://houtai.baidu.com/v2/schemas/page.json",

"type": "page",

"body": [

{

"type": "tpl",

"tpl": "<p>段落1</p>"

},

 

{

"type": "tpl",

"tpl": "<p>段落2</p>"

},

 

"<p>段落3</p>"

]

}

 

再来看一个表单页面的列子

 

{

"$schema": "https://houtai.baidu.com/v2/schemas/page.json#",

"type": "page",

"body": {

"api": "/api/mock2/form/saveForm",

"type": "form",

"title": "联系我们",

"controls": [

{

"type": "text",

"label": "姓名",

"name": "name"

},

 

{

"type": "email",

"label": "邮箱",

"name": "email",

"required": true

},

 

{

"type": "textarea",

"label": "内容",

"name": "content",

"required": true

}

],

"actions": [

{

"label": "发送",

"type": "submit",

"primary": true

}

]

}

} 

这个例子就是在 body 容器内，放置一个 form 类型的渲染器，它就成了一个简单的表单提交页面了，controls 中可以决定放哪些表单项目，actions 中可以放置操作按钮。

 
