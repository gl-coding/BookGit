# 第1节：Linux基础

命令：touch

语法：#touch 文件的名字文件名可以是一个完整的路径

如果后面的参数文件名指定了路径，则表示在指定的路径下创建；如果只是传递一个文件名，则表示在当前目录创建文件。

例如：

1、在当前路径下创建一个文件名字叫php50.txt。

命令：#touch php50.txt



pwd****：显示当前路径**

 

cd ：切换目录

用法：cd

cd ../ 切换到上级目录

cd /  切换到根目录

cd ~ （或只有cd ）切换到当前用户主目录(home底下以用户名命名的文件夹) /root目录

mkdir 创建目录

mkdir 目录名 -p  递归创建目录

 

**rmdir** **删除空目录**（谨慎使用）

 

用法：rmdir 目录名

也可用：rm -rf 目录名

 

**ls** **查看目录或文件信息**

 

主要选项：

-l 列出目录或者文件的详细信息。比如权限、修改时间等等

-a 列出当前目录下所有文件，包括隐藏文件（已点开头的都是隐藏文件）

 

**vi** **文本编辑器**

 

键入i 进入编辑状态

退出编辑按ESC键

不保存退出： :q!

保存退出：  :wq

输入/，进入搜索

输入:set nu，显示每一行的行数

按键盘G，可以直接定位到最末尾

 

**cp** **复制**

 

用法：cp ［选项］文件名或目录 目标地址

-R 拷贝目录及目录下所有目录和文件

cp a.txt b.txt  将a文件复制，且另命名为b文件（目录名）

 

**mv** **移动**

 

用法：mv 文件名或目录 目标目录

mv a.txt ../  将a文件移动到上级目录（将一个文件移动到另一个目录没有重命名）

mv a.txt ../b.txt  将a文件移动到上一级并改名为b文件（将一个文件移动到另一个目录并重命名）

 

**rm** **删除文件或目录**

 

-f 强制删除

-r 删除目录  

常用：rm -rf 文件或目录

 

**find** **查找文件**

 

用法：find [路径] [选项]

常用选项有：

find . -name *.log  在当前目录查找以.log结尾的文件

find / -name log  在根目录查找log命名的目录

 

**grep** **过滤**

 

在指定文件中查找字符（串）并打印该行

用法：grep 字符串 文件名     

grep band file 在file文件中找寻band字符串

 

**cat** **显示文本文件内容**

 

用法：cat 文件名  cat 文件名字

 

 

**head** **查看前几行**

 

用法： head -n 5 文件名

 

**tail** **从指定点开始将文件写到标准输出**

 

tail -n 5 文件名 查看后几行

tail -f error.log 不断刷新，看到最新内容

 

**ps** **查看进程（动态）**

 

-ef 显示所有运行进程，并显示启动进程的命令

 

**netstat** **查看网络状况 （net status的简写）**

 

netstat -apn 查看所有端口

an，按一定顺序排列输出

p，表示显示哪个进程在调用

 

**|** **管道符 （竖线，英文输入法状态下shift+键盘上的的|\）**

 

在命令之间建立管道，将前面命令的输出作为后面命令的输入

通过命令查找tomcat进程：ps -ef | grep tomcat

通过命令查找到占用此端口的进程编号：netstat -apn|grep 8080

 

**echo** **打印文件内容或编辑文件内容**

 

常用选项有：

-n 不换行输出

-e 可以使用转义字符（\n回车，\t tab键）

示例：

echo “I am studying linux”>>xujun.txt 追加文件尾部内容

echo $? 假如返回值为0的时候，表示上一次命令成功。假如是1到255的话，则是失败

echo -e “wo\tshi\tshei”> xujun.txt

 

**touch** **创建一个空白文件，假如当前目录有同样的文件，则会更新文件的时间戳**

 

-a 修改access（访问）时间

-m 修改modify（修改）时间这两个参数了解即可

 

**uname** **查看系统**

 

-m 查看系统是几位操作系统

-r 查看系统的内核版本

-a 查看详细的系统内核版本和系统的操作系统

 

**rz** **上传**

 

假如系统里面没有这个命令，则使用yum install lrzsz 安装

-y 覆盖

直接输入rz，就可以上传文件

 

**sz** **下载**

 

假如系统里面没有这个命令，则使用yum install lrzsz 安装

-y 覆盖

sz -y test.txt

 

**su** **切换用户**

 

su root

 

**history** **查看命令历史记录**

 

 

**chmod** **权限赋予命令**

 

-R 递归改变目录下所有子目录和文件的权限

数字方式：r=4 w=2 x=1

 

chmod 777 lemon

  

**tar** **解压，压缩tar.gz**

tar -czvf test.tar.gz test

将test文件夹压缩成test.tar.gz

 

tar -xzvf test.tar.gz

将test.tar.gz解压得到test文件夹

 

**zip** **解压，压缩zip**

 

zip –r test.zip test

将test文件夹压缩成test.zip，必须带r 才会把文件压缩进去，不然会生成一个空的文件夹

 

unzip test.zip

将test.zip文件夹解压

 

**关闭防火墙**

 

开启：service iptables start

关闭：service iptables stop

 

**永久关闭防火墙**

 

开启：chkconfig iptables on 

关闭：chkconfig iptables off