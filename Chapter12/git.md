# Git

1,Git是什么?

  (1),Git是目前世界上最先进的分布式版本控制系统。

   (2),Git 与svn 的区别

​     Git是分布式版本控制系统,那么它就没有中央服务器的,每个人的电脑就是一个完整的版本库,这样工作就不需要联网,因为版本是在自己的电脑上面.既然每个人都有一个完整的版本库,那多个人如何协作的呢?比如自己在电脑上面修改了A文件,其他人也在电脑上面修改了A文件,这时，你们两之间只需把各自的修改推送给对方，就可以互相看到对方的修改了.

​    svn是集中式版本控制系统,版本库是集中放在中央服务器的,而干活的时候,用的都是自己的电脑,所以首先要从中央服务器哪里得到最新的版本，然后干活，干完后，需要把自己做完的活推送到中央服务器。集中式版本控制系统是必须联网才能工作，如果在局域网还可以，带宽够大，速度够快，如果在互联网下，如果网速慢的话，就蛋疼了。

2,，下载的git

 https://git-scm.com/

![img](https://img-blog.csdn.net/20180814230333292?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0NyYXp5X0N3/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

 

3,安装:

![img](https://img-blog.csdn.net/20180814231326119?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0NyYXp5X0N3/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

next--> 配置

![img](https://img-blog.csdn.net/20180814231354376?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0NyYXp5X0N3/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

**Additional icons** 附加图标    这里我打 --√

**On the Desktop** 在桌面上  这里我打 --√

**Windows Explorer integration** Windows资源管理器集成**鼠标右键**菜单

 **Git Bash Here**    这里我打 --√

 **Git GUI Here**     这里我打 --√

**Git LFS (Large File Support)**  大文件支持 

**Associate .git\* configuration files with the default text editor**: 将 .git 配置文件与默认文本编辑器相关联 ---  这里我打 --√

**Associate .sh files to be run with Bash** :将.sh文件关联到Bash运行 -----  这里我打 --√

 **Use a TrueType font in all console windows**  : 在所有控制台窗口中使用TrueType字体 

**Check daily for Git for Windows updates**  : 每天检查Git是否有Windows更新 

**选择Git使用的默认编辑器**

![img](https://img-blog.csdn.net/20180814232731485?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0NyYXp5X0N3/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

**配置PATH环境**

![img](https://img-blog.csdn.net/20180814232858561?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0NyYXp5X0N3/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

**Use Git from Git Bash only**

*This is the safest choice as your PATH will not be modified at all.You will only be able to use the Git command line tools form Git Bash.*

***这是最安全的选择，因为您的PATH根本不会被修改。您只能使用 Git Bash 的 Git 命令行工具。\***

 

**Use Git from the Windows Command Prompt**

*This option is considered safe as it only adds some minimal Git wrappers to your PATH to avoid cluttering your environment with optional Unix tools . You will be able to use Git from both Git Bash and the Windows Command Prompt.*

***这个选项被认为是安全的，因为它只向PATH添加一些最小的 Git包，以避免使用可选的Unix工具混淆环境。 您将能够从 Git Bash 和 Windows 命令提示符中使用 Git。\***

 

**Use Git and optional Unix tools from the Windows Command Prompt**

从Windows命令提示符使用Git和可选的Unix工具

*Both Git and the optional Unix tools will be added to you PATH*

***Git和可选的Unix工具都将添加到您计算机的 PATH 中\***

*Warning:This will override Windows tools like "find and sort".Only use this option if you understand the implications.*

***警告：这将覆盖Windows工具，如 “ find 和 sort ”。只有在了解其含义后才使用此选项。\***

 

**选择HTTPS传输后端**

![img](https://img-blog.csdn.net/20180814232909629?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0NyYXp5X0N3/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

**Use the OpenSSL library**

使用 OpenSSL 库

*Server certificates will be validated using the ca-bundle.crt file.*

***服务器证书将使用ca-bundle.crt文件进行验证。\***

 

**Use the native Windows Secure Channel library**

使用本地 Windows 安全通道库

*Server certificates will be validated using Windows Certificate Stores.This option also allows you to use your company's internal Root CA certificates distributed e.g. via Active Directory Domain Services.*

***服务器证书将使用Windows证书存储验证。此选项还允许您使用公司的内部根CA证书，例如， 通过Active Directory Domain Services 。\***

### 

**配置行结束转换**

![img](https://img-blog.csdn.net/20180814233308436?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0NyYXp5X0N3/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

**Checkout Windows-style,commit Unix-style line endings**

*Git will convert LF to CRLF when checking out text files.When committing text files,CRLF will be converted to LF .For cross-pltform projects,this is the recommended setting on Windows ("core.autocrlf" is set to "true")*

***在检出文本文件时，Git会将LF转换为CRLF。当提交文本文件时，CRLF将转换为LF。 对于跨平台项目，这是Windows上推荐的设置（“core.autocrlf”设置为“true”）\***

 

**Checkout as-is , commit Unix-style line endings**

*Git will not perform any conversion when checking out text files. When committing text files, CRLF will be converted to LF. For cross-platform projects,this is the recommended setting on Unix ("core.autocrlf" is set to "input")*

***在检出文本文件时，Git不会执行任何转换。 提交文本文件时，CRLF将转换为LF。 对于跨平台项目，这是Unix上的推荐设置 （“core.autocrlf”设置为“input”）\***

 

**Checkout as-is,commit as-is**

*Git will not perform any conversions when checking out or committing text files.Choosing this option is not recommended for cross-platform projects ("core.autocrlf"is set to "false")*

***在检出或提交文本文件时，Git不会执行任何转换。对于跨平台项目，不推荐使用此选项（“core.autocrlf”设置为“false”）\***

 

**配置终端模拟器以与 Git Bash 一起使用**

![img](https://img-blog.csdn.net/20180814233349269?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0NyYXp5X0N3/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

**Use MinTTY (the default terminal of MSYS2)**

*Git Bash will use MinTTY as terminal emulator,which sports a resizable window,non-rectangular selections and a Unicode font. Windows console programs (such as interactive Python) must be launched via 'winpty' to work in MinTTY.*

***Git Bash将使用MinTTY作为终端模拟器，该模拟器具有可调整大小的窗口，非矩形选区和Unicode字体。 Windows控制台程序（如交互式Python）必须通过'winpty'启动才能在MinTTY中运行。\***

 

**Use Windows' default console window**

*Git will use the default console window of Windows ("cmd.exe"),which works well with Win32 console programs such as interactive Python or node.js , but has a very limited default scroll-back,needs to be configured to use aUnicode font in order to display non-ASCII characters correctly,and prior to Windows 10 its windows was not freely resizable and it only allowed rectangular text selections.*

***Git将使用Windows的默认控制台窗口（“cmd.exe”），该窗口可以与Win32控制台程序（如交互式Python或node.js）一起使用，但默认的回滚非常有限，需要配置为使用unicode 字体以正确显示非ASCII字符，并且在Windows 10之前，其窗口不能自由调整大小，并且只允许矩形文本选择。\***

 

**配置额外的选项**

![img](https://img-blog.csdn.net/20180814233436904?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0NyYXp5X0N3/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

**Enable file system caching**

启用文件系统缓存

*File system data will be read in bulk and cached in memory for certain operations ("core.fscache" is set to "true"). This provides a significant performance boost.*

***文件系统数据将被批量读取并缓存在内存中用于某些操作（“core.fscache”设置为“true”）。 这提供了显着的性能提升。\***

 

**Enable Git Credential Manager**

启用Git凭证管理器

*The Git Credential Manager for Windows provides secure Git credential storage for Windows,most notably multi-factor authentication support for Visual Studio Team Services and GitHub. (requires .NET framework v4.5.1 or or later).*

***Windows的Git凭证管理器为Windows提供安全的Git凭证存储，最显着的是对Visual Studio Team Services和GitHub的多因素身份验证支持。 （需要.NET Framework v4.5.1或更高版本）。\***

 

**Enable symbolic links**

启用符号链接

*Enable symbolic links (requires the SeCreateSymbolicLink permission).Please note that existing repositories are unaffected by this setting.*

***启用符号链接（需要SeCreateSymbolicLink权限）。请注意，现有存储库不受此设置的影响。\***

###  

### Installing

### ![img](https://img-blog.csdn.net/20180506000504906)

### Completing the Git Setup Wizard

![img](https://img-blog.csdn.net/20180506000519185)

 

from : https://blog.csdn.net/crazy_cw/article/details/81629946



**1 Git简介**

Git是目前世界上最先进的分布式版本控制系统（没有之一）。

**2 \**Windows上安装Git\****

1. 在网上下载国内镜像Git的安装程序
2. 安装完成后，在开始菜单里找到“Git”->“Git Bash”，蹦出一个类似命令行窗口的东西，就说明Git安装成功！
3. 安装完成后，还需要最后一步设置，在命令行输入：（注：git config命令的--global参数，用了这个参数，表示你这台机器上所有的Git仓库都会使用这个配置）

- $ git config --global user.name "Your Name"
- $ git config --global user.email "email@example.com"

**3 \**创建版本库\****

1、选择一个合适的地方，创建一个空目录：

- $ mkdir app//创建一个叫app的文件夹
- $ cd app //切换到app目录下
- $ pwd //查看当前目![img](https://images2018.cnblogs.com/blog/825265/201804/825265-20180409112205309-1972875823.png)![img](e:/%E6%9C%89%E9%81%93%E4%BA%91%E7%AC%94%E8%AE%B0/geminiyu233@163.com/72a467bc38e74b9a8d10be684cb4f87d/clipboard.png)

2 、通过git init命令把这个目录变成Git可以管理的仓库（如果已有文件，则忽略第一步）：

![img](https://images2018.cnblogs.com/blog/825265/201804/825265-20180409112236397-1359760653.png)

![img](e:/%E6%9C%89%E9%81%93%E4%BA%91%E7%AC%94%E8%AE%B0/geminiyu233@163.com/0841b30761344127aa2a4878fd492710/clipboard.png)

瞬间Git就把仓库建好了，而且告诉你是一个空的仓库（empty Git repository）

- 目录下多了一个.git的目录，这个目录是Git来跟踪管理版本库的，没事千万不要手动修改这个目录里面的文件，不然改乱了，就把Git仓库给破坏了。
- 如果你没有看到.git目录，那是因为这个目录默认是隐藏的，用ls -ah命令就可以看见。

3、现在我们编写一个readme.txt文件放在app目录下，内容如下：

1111

然后：

1. 用命令git add告诉Git，把文件添加到仓库：

$ git **add readme.txt**

执行上面的命令，没有任何显示，这就对了，Unix的哲学是“没有消息就是好消息”，说明添加成功。

1. 用命令git commit告诉Git，把文件提交到仓库：

$ git **commit -m "wrote a readme file"**

**![img](https://images2018.cnblogs.com/blog/825265/201804/825265-20180409112307555-1033723156.png)**

![img](e:/%E6%9C%89%E9%81%93%E4%BA%91%E7%AC%94%E8%AE%B0/geminiyu233@163.com/00471fd5f3c3476b93d6aca46f14339b/clipboard.png)

解释一下git commit命令，-m后面输入的是本次提交的说明.

为什么Git添加文件需要add，commit一共两步呢？因为commit可以一次提交很多文件，所以你可以多次add不同的文件，比如：

- $ git add file1.txt
-  $ git add file2.txt file3.txt
-  $ git commit -m "add 3 files."

4、成功地添加并提交了一个readme.txt文件，现在，是时候继续工作了，我们继续修改readme.txt文件，改成如下内容：

11111

22222

现在，运行git status命令看看结果：

![img](https://images2018.cnblogs.com/blog/825265/201804/825265-20180409112326567-76827164.png)

![img](e:/%E6%9C%89%E9%81%93%E4%BA%91%E7%AC%94%E8%AE%B0/geminiyu233@163.com/7affde1a88e5425e8158027d10deb9a7/clipboard.png)

git status命令可以让我们时刻掌握仓库当前的状态，上面的命令告诉我们，readme.txt被修改过了，但还没有准备提交的修改。

5、虽然Git告诉我们readme.txt被修改了，但如果能看看具体修改了什么内容，自然是很好的。比如你休假两周从国外回来，第一天上班时，已经记不清上次怎么修改的readme.txt，所以，需要用git diff这个命令看看：

![img](https://images2018.cnblogs.com/blog/825265/201804/825265-20180409112349156-545456955.png)

![img](e:/%E6%9C%89%E9%81%93%E4%BA%91%E7%AC%94%E8%AE%B0/geminiyu233@163.com/668e602e28c44b7691bdb1c0b1371b7c/clipboard.png)

知道了对readme.txt作了什么修改后，再把它提交到仓库就放心多了，提交修改和提交新文件是一样的两步，第一步是git add，在执行第二步git commit之前，我们再运行git status看看当前仓库的状态：

![img](https://images2018.cnblogs.com/blog/825265/201804/825265-20180409112403981-808491313.png)

![img](e:/%E6%9C%89%E9%81%93%E4%BA%91%E7%AC%94%E8%AE%B0/geminiyu233@163.com/9d7b057cdac84926b855ce936ffc4206/clipboard.png)

git status告诉我们，将要被提交的修改包括readme.txt，下一步，就可以放心地提交了。

提交后，我们再用git status命令看看仓库的当前状态：

![img](https://images2018.cnblogs.com/blog/825265/201804/825265-20180409112444363-276788068.png)

![img](e:/%E6%9C%89%E9%81%93%E4%BA%91%E7%AC%94%E8%AE%B0/geminiyu233@163.com/79683b32bdc34a81a0cb3483cff111ad/clipboard.png)

Git告诉我们当前没有需要提交的修改，而且，工作目录是干净（working directory clean）的。

**4 \**版本回退\****

**4.1 \**git log\****

“保存一个快照”，这个快照在Git中被称为commit。一旦你把文件改乱了，或者误删了文件，还可以从最近的一个commit恢复，然后继续工作.

实际工作中，版本控制系统用git log命令可以告诉我们历史记录：

![img](https://images2018.cnblogs.com/blog/825265/201804/825265-20180409112525610-556779825.png)

![img](e:/%E6%9C%89%E9%81%93%E4%BA%91%E7%AC%94%E8%AE%B0/geminiyu233@163.com/08c6a482c0d4429e97f93241a9b67cb5/clipboard.png)

git log命令显示从最近到最远的提交日志。

如果嫌输出信息太多，看得眼花缭乱的，可以试试加上--pretty=oneline参数：

![img](https://images2018.cnblogs.com/blog/825265/201804/825265-20180409112551557-1780753715.png)

![img](e:/%E6%9C%89%E9%81%93%E4%BA%91%E7%AC%94%E8%AE%B0/geminiyu233@163.com/f97eae3b02e04d8f9c28e1c8b28d2ae1/clipboard.png)

你看到的一大串类似3628164...882e1e0的是commit id（版本号），一大串数字防止跟别人的版本号冲突

**4.2 \**git reset\****

首先，Git必须知道当前版本是哪个版本，在Git中，用HEAD表示当前版本，也就是最新的提交3628164...882e1e0（注意我的提交ID和你的肯定不一样），上一个版本就是HEAD^，上上一个版本就是HEAD^^，当然往上100个版本写100个^比较容易数不过来，所以写成HEAD~100。

现在，我们要把当前版本回退到上一个版本，就可以使用git reset命令：**$ git reset --hard HEAD^（注：--hard参数\**）\****

![img](https://images2018.cnblogs.com/blog/825265/201804/825265-20180409112609976-671017255.png)

![img](e:/%E6%9C%89%E9%81%93%E4%BA%91%E7%AC%94%E8%AE%B0/geminiyu233@163.com/b21c7cf83d2648a58c8b0efb63116bab/clipboard.png)

还可以继续回退到再上一个版本，不过且慢，然我们用git log再看看现在版本库的状态：

 

![img](https://images2018.cnblogs.com/blog/825265/201804/825265-20180409112642718-482992364.png)![img](e:/%E6%9C%89%E9%81%93%E4%BA%91%E7%AC%94%E8%AE%B0/geminiyu233@163.com/c34515ed496649e7959f56c35e96eeca/clipboard.png)

- 此时你反悔不想回退，想回到刚刚删除的那个未来版本，办法其实还是有的，只要上面的命令行窗口还没有被关掉，你就可以顺着往上找啊找啊，找到那个版本的commit id是3628164...，于是就可以指定回到未来的某个版本：

$ git re**set --hard 3628164**

**![img](https://images2018.cnblogs.com/blog/825265/201804/825265-20180409112727224-1818054951.png)**

![img](e:/%E6%9C%89%E9%81%93%E4%BA%91%E7%AC%94%E8%AE%B0/geminiyu233@163.com/61b7e74d508341129464d0b3e7cbba5a/clipboard.png)

版本号没必要写全，前几位就可以了。

- 上面的命令行窗口被关掉了！在Git中，总是有后悔药可以吃的。你必须找到commit id。Git提供了一个命令git reflog用来记录你的每一次命令：

![img](e:/%E6%9C%89%E9%81%93%E4%BA%91%E7%AC%94%E8%AE%B0/geminiyu233@163.com/ed781a5f011a4e3c8a9469e75457c0a1/clipboard.png)

**![img](https://images2018.cnblogs.com/blog/825265/201804/825265-20180409112801001-2141926226.png)**

**4.3 小结**

现在总结一下：

- HEAD指向的版本就是当前版本，因此，Git允许我们在版本的历史之间穿梭，使用命令git reset --hard commit_id。
- 穿梭前，用git log可以查看提交历史，以便确定要回退到哪个版本。
- 要重返未来，用git reflog查看命令历史，以便确定要回到未来的哪个版本。

**5 撤销修改**

场景1：当你改乱了工作区某个文件的内容，想直接丢弃工作区的修改时，用命令git checkout -- fileName。

场景2：当你不但改乱了工作区某个文件的内容，还添加到了暂存区时，想丢弃修改，分两步，第一步用命令git reset HEAD fileName，就回到了场景1，第二步按场景1操作。

场景3：已经提交了不合适的修改到版本库时，想要撤销本次提交，参考[版本回退](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/0013744142037508cf42e51debf49668810645e02887691000)一节，不过前提是没有推送到远程库。

**6 添加远程库**

**6.1 本地库与远程库关联**

git remote add origin https地址

添加后，远程库的名字就是origin，这是Git默认的叫法，也可以改成别的，但是origin这个名字一看就知道是远程库。

**6.2 把本地库的所有内容推送到远程库上**

$ git push -u（第一次提交到远程空库，以后可以忽略） <远程库名> <远程库分支名> （如：$ git push -u origin master）

**7 \**从远程库克隆\****

远程库已经准备好了，下一步是用命令git clone克隆一个本地库：

$ git clone https地址

**8 \**分支管理\****

分支在实际中有什么用呢？假设你准备开发一个新功能，但是需要两周才能完成，第一周你写了50%的代码，如果立刻提交，由于代码还没写完，不完整的代码库会导致别人不能干活了。如果等代码全部写完再一次提交，又存在丢失每天进度的巨大风险。

现在有了分支，就不用怕了。你创建了一个属于你自己的分支，别人看不到，还继续在原来的分支上正常工作，而你在自己的分支上干活，想提交就提交，直到开发完毕后，再一次性合并到原来的分支上，这样，既安全，又不影响别人工作。

**8.1 Git分支管理**

- 查看分支：git branch
- 创建分支：git branch <name>
- 切换分支：git checkout <name>
- 创建+切换分支：git checkout -b <name>
- 合并某分支到当前分支：git merge <name>
- 删除分支：git branch -d <name>
- 具体的分支切换原理可以参考：https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/001375840038939c291467cc7c747b1810aab2fb8863508000

**9 \**解决冲突\****

当Git无法自动合并分支时，就必须首先解决冲突。解决冲突后，再提交，合并完成。

用git log --graph命令可以看到分支合并图。

具体原理可以查看：

https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/001375840202368c74be33fbd884e71b570f2cc3c0d1dcf000

**10 Bug分支**

当你接到一个很急的bug，但是，等等，当前正在dev上进行的工作还没有提交，Git还提供了一个stash功能，可以把当前工作现场“储藏”起来，等以后恢复现场后继续工作。

现在在比如develop分支上创建一个bug分支，bug解决后合并到develop分支，并删除bug分支，现在要接着完成之前的工作。

- git stash //当前工作现场“储藏”起来
- $ git stash list //查看刚才的工作现场存到哪去了
- git stash apply //恢复后，stash内容并不删除，你需要用git stash drop来删除；
- git stash pop //恢复的同时把stash内容也删了

开发一个新feature，最好新建一个分支；

如果要丢弃一个没有被合并过的分支，可以通过git branch -D <name>强行删除

**11 Git与可视化工具小乌龟对应**

- git提交（c）->master //相当于“git add”，提交到本地仓库
- Git同步 //相当于git push origin master 提交到远程仓库（其中分支可选）

**12 重要**

当我想从远程仓库里拉取一条本地不存在的分支时：git checkout -b 本地分支名 origin/远程分支名，这个将会自动创建一个新的本地分支，并与指定的远程分支关联起来。如果出现提示：

fatal: Cannot update paths and switch to branch 'dev2' at the same time. Did you intend to checkout 'origin/dev2' which can not be resolved as commit?

表示拉取不成功。我们需要先执行：git fetch

然后再执行

git checkout -b 本地分支名 origin/远程分支名