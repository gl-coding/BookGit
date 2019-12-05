# Nginx

### mac安装

```bash
`brew install nginx`
```

###启动nginx

```bash
`sudo nginx`
```

### 效果

nginx就安装好了，可以在浏览器访问了，默认端口为8080，

在浏览器输入 http://localhost:8080/ 

就能看到nginx在本计算机搭建的服务器

8080是nginx自带的默认网站设置的端口，

### 自己建站

现在我们自己来创建一个网站，设置端口和映射路径

打开终端，准备编辑nginx的配置文件：

```bash
sudo vim /usr/local/etc/nginx/nginx.conf
```

注意设置访问权限( user root owner; )，不然等会访问网站会出现403错误

```bash
#user  nobody;
user  root owner;
worker_processes  1;
```

重新设置端口以及设置反向代理

```bash
server {
    #设置端口
    listen       8080;
    server_name  localhost;

    #charset koi8-r;

    #access_log  logs/host.access.log  main;

    #自定义顿口和映射本地网站路径（设置反向代理路径和端口）
    location / {
        #root   html;
        proxy_pass http://127.0.0.1:4000;
        index  index.html index.htm;
    }
```
##启动

 启动代码格式：nginx安装目录地址 -c nginx配置文件地址

```bash
#/usr/local/nginx/sbin/nginx -c /usr/local/nginx/conf/nginx.conf
```

## 强制停止

```bash
# pkill -9 nginx
```

## 验证nginx配置文件是否正确

### 进入nginx安装目录sbin下，输入命令./nginx -t

看到如下显示

```bash
nginx.conf syntax is ok
nginx.conf test is successful
```

说明配置文件正确！

### 重新启动nginx

```bash
sudo nginx -s reload
```

#Nginx 配置多个服务共用80端口（反向代理）

使用场景：两个不同端口的微服务，当我们测试的时候，需要放到同一台服务器上，共享80端口访问

可以在nginx.conf中做如下配置：

```json
server {         

         listen       80;  

        server_name  apitest.aa.com;  

        location / {

            proxy_pass http://10.26.31.176:8081;   #微服务地址测试环境

            root   html;  

            index  index.html index.htm;  

         }   

  }

 

server {         

         listen       80;  

        server_name  api.aa.com;  

        location / {  

            proxy_pass http://10.26.31.176:8080;   #微服务地址线上环境

            root   html;  

            index  index.html index.htm;  

         }   

  }

```

做好上述配置，我们就可以愉快的进行测试了。

注意：修改完成之后，要重载下配置才能生效

##重载配置文件 需要进入nginx安装目录 执行如下命令

sbin/nginx -s reload


# 一个端口代理多个服务配置实例（动静分离）

修改JS文件总是要部署到服务器后才能通过浏览器调试，比较麻烦，如果已经是生产系统还不方便部署，担心修改的JS文件还有问题，导致原有的功能也不能正常使用，影响用户体验。一直想找一个可以加载本地JS进行调试办法，很幸运Nginx可以！
nginx.conf 配置实例 

```
worker_processes  1;
 
events {
    worker_connections  1024;
}
 
http {
    include       mime.types;
    default_type  application/octet-stream;
 
    sendfile        on;
    keepalive_timeout  5;
 
    server {
        listen       6001;
        server_name  localhost;
 
        # 本机接口服务（服务代理）
        location /services {
            #root   html;
            #index  index.html index.htm;
            proxy_pass http://localhost:8080;
        }
        
        # JS（静态文件代理）
        location /ecustom/workflow/form/js {
            root   E:/Workspaces/ecology-eclipse/ecology-essex/WebContent;
        }
        
        # OA测试系统（服务代理）
        location / {
            proxy_pass http://192.168.2.95:8080;
        }
    }
}
```

参数解释

worker_processes

进程个数

events.worker_connections

每个进程允许的最多连接数

http.include

导入文件内容

http.default_type

默认文件类型

http.sendfile

是否调用 sendfile 函数来输出文件

http.keepalive_timeout

连接超时时间

http.server.listen

监听端口

http.server.server_name

监听主机，可写通配符

http.server.location

监听地址（URL）

http.server.location.root

定义服务器的默认网站根目录位置

http.server.location.index

定义首页索引文件的名称

http.server.location.proxy_pass	定义代理服务器地址
http.server.error_page

错误页


# Nginx反向代理（https配置）

前言
写微信小程序要求, 请求必须是https, 所以研究下了这个东西, 用的时候要注意下

解压后双击nginx.exe运行, 此时访问localhost可看到英文界面.

全程无难度, 唯一注意:::下载解压目录别带中文

配置https:

首先得有证书（阿里云申请免费证书）, 把两个证书下载后放置到conf目录, 修改nginx.conf

配置文件这么写:

```
HTTPS server
#
server {
    listen       443 ssl;
    server_name   自己的域名

    ssl_certificate 1.....crt; # 改为自己申请得到的 crt 文件的名称
    ssl_certificate_key 2.....key; # 改为自己申请得到的 key 文件的名称
    
    ssl_session_cache    shared:SSL:1m;
    ssl_session_timeout  5m;
    ssl_ciphers  HIGH:!aNULL:!MD5;
    ssl_prefer_server_ciphers  on;
    location / {  
        root   html;
        index  index.html index.htm;
    }

}
```

location 千万不要忘记配置

# nginx 反向代理 常见错误处理

    由内外网分离，只有某台服务的某几个端口是外网可以访问，若需要从外网访问我内网的搭建的服务，此时我们需要借助nginx反向代理功能，nginx作为反向代理服务，通过外网指定端口透射到内网，并代理内网的服务。
    
    在使用的过程中，出现的几个问题，以及解决方案

一、配置nginx.conf ，导致ip和port被替换成代理的服务名http://neb ，而不是实际的ip和地址

![image-20191205164357080](/Users/guolei08/Library/Application Support/typora-user-images/image-20191205164357080.png)      

       问题：访问122.224.0.0:9400 , 但被转成了http://confluence/admin，导致请求的资源返回404
    
       解决：proxy_set_header X-Forwarded-Host $host;
                 proxy_set_header X-Forwarded-Server $host;
    
                 proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    
                 proxy_set_header Host $host:$server_port; 

二、nginx代理websocket需要特殊的配置

       proxy_set_header Upgrade $http_upgrade;
    
       proxy_set_header Connection "upgrade";       

三、nginx代理websocket，返回403错误      

       权限访问问题
    
       解决:在配置文件中增加
    
               proxy_set_header Origin "";

四、nginx反向代理，跨域配置

       add_header Access-Control-Allow-Origin *;  
       add_header Access-Control-Allow-Credentials true;
       add_header Access-Control-Allow-Methods GET,POST,OPTIONS;
