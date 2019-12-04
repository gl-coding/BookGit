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

