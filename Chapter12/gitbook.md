# Gitbook

###是什么

GitBook 是一个基于 Node.js 的命令行工具，支持 Markdown 语法格式，可以输出 HTML、PDF、eBook 等格式的电子书。

GitBook 不是 Markdown 编辑工具，也不是 Git 版本管理工具，但 GitBook 又与 Markdown 和 Git 息息相关

GitBook：管理文档，预览、制作电子书；

同时通过 Git 管理书籍内容的变更，托管 GitHub，实现多人协作

目前使用的搭配是 `GitBook + Typora + Git`



###为什么

简单来说，GitBook + Markdown + Git 带来的好处有：

> 语法简单
>
> 兼容性强
>
> 导出方便
>
> 专注内容
>
> 团队协作

当然，GitBook 不是万能的，当我们需要复杂排版时，依然需要依托于 Word 等工具。但不用担心，因为我们可以把 Markdown 格式的文档导出为 Word 格式，再进一步加工。



###怎么办

怎么安装 —— 如何搭建 GitBook 环境？

1.Node.js：因为 GitBook 是基于装 Node.js， Node.js 都会默认安装 npm（node 包管理工具）

2.打开命令行，执行以下命令安装 GitBook：

npm install -g gitbook-cli

安装完之后，就会多了一个 gitbook 命令（如果没有，请确认上面的命令是否加了 -g）。

2.所以你还需要安装 Typora（一个很棒的支持 macOS、Windows、Linux 的 Markdown 编辑工具）和 Git 版本管理工具。

Typora 下载地址：https://typora.io/
Git 下载地址：https://git-scm.com/downloads

Typora 的安装很简单，难点在于需要翻墙才能下载（当然你也可以找我要）。Git 的安装也很简单，但要用好它需要不少时间，这里就不展开了（再讲下去怕你要跑啦~）。



###怎么使用

mkdir mybook &&  cd mybook

执行以下命令：

gitbook init

执行完后，你会看到多了两个文件 —— README.md 和 SUMMARY.md，它们的作用如下：

README.md —— 书籍的介绍写在这个文件里
SUMMARY.md —— 书籍的目录结构在这里配置

这时候，我们启动恭候多时的 Typora 来编辑这两个文件了：

编辑 SUMMARY.md 文件，内容修改为：

```
# 目录

* [前言](README.md)
* [第一章](Chapter1/README.md)
  * [第1节：衣](Chapter1/衣.md)
  * [第2节：食](Chapter1/食.md)
  * [第3节：住](Chapter1/住.md)
  * [第4节：行](Chapter1/行.md)
* [第二章](Chapter2/README.md)
* [第三章](Chapter3/README.md)
* [第四章](Chapter4/README.md)

```


然后我们回到命令行，在 mybook 文件夹中再次执行 gitbook init 命令。GitBook 会查找 SUMMARY.md 文件中描述的目录和文件，如果没有则会将其创建。

Typora 是所见即所得（实时渲染）的 Markdown 编辑器，这时候它是这样的：



###效果

接着我们执行 gitbook serve 来预览这本书籍，执行命令后会对 Markdown 格式的文档进行转换，默认转换为 html 格式，

最后提示 “Serving book on http://localhost:4000”。嗯，打开浏览器看一下吧：



###上线

当你写得差不多，你可以执行 gitbook build 命令构建书籍，默认将生成的静态网站输出到 _book 目录。实际上，这一步也包含在 gitbook serve 里面，因为它们是 HTML，所以 GitBook 通过 Node.js 给你提供服务了。

当然，build 命令可以指定路径：

gitbook build [书籍路径] [输出路径]

serve 命令也可以指定端口：

gitbook serve --port 2333

你还可以生成 PDF 格式的电子书：

gitbook pdf ./ ./mybook.pdf

生成 epub 格式的电子书：

gitbook epub ./ ./mybook.epub

生成 mobi 格式的电子书：

gitbook mobi ./ ./mybook.mobi

如果生成不了，你可能还需要安装一些工具，比如 ebook-convert。或者在 Typora 中安装 Pandoc 进行导出。

除此之外，别忘了还可以用 Git 做版本管理呀！在 mybook 目录下执行 git init 初始化仓库，执行 git remote add 添加远程仓库（你得先在远端建好）。接着就可以愉快地 commit，push，pull … 啦！

# Ubuntu下搭建gitbook环境

1.1 安装nodejs
参考文章：http://blog.csdn.net/zijie_xiao/article/details/51114917

1.2 安装gitbook
sudo npm install -g gitbook-cli
1
查看gitbook是否安装成功

gitbook -V

### 1.3 命令行gitbook 使用

在书目录下，初始化

```
gitbook init1
```

编译生成静态网页

```
gitbook build1
```

可通过静态网址访问

```
gitbook serve
```

ubuntu连不上外网，gitbook安装不成功

更改思路：

生成html，使用python构建网络服务