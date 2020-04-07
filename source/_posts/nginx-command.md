---
title: Nginx 常用命令及其配置
comments: false
---
## Nginx 常用的命令及其配置
<!--more-->
```
nginx -s reload  重载配置文件
nginx -s reopen  重新打开日志
nginx -t         检查配置文件是否正确
nginx -t -c      检查指定配置文件是否正确

nginx -v         版本信息
nginx -V         版本信息和编译选项

nginx -s quit    等任务处理完退出nginx
nginx -s stop    停止服务


```

```
error_page 403 xxx.html;

error_page 500 502 503 504 xx.html;

隐藏服务器返回的真实状态码信息
error_page 404 =200 /40x.html;

error_page 404-/40x.html;

allow 192.168.1.1;

deny all;

内层块中的allow all会覆盖外层块中的deny all的设置

```

```
location =/js 精准匹配
location ~ 正则表达式完成，区分大小写
location ~* 正则表达式，不区分大小写
location ^~ 不使用正则表达式，完成以指定模式开头的location 匹配

location @ 定义一个location块，只能被nginx内部配置指令访问


普通location遵循最大前缀匹配，匹配度最高的location 将会被执行

```

```
error_log 
debug info notice warn error crit

error_log /dev/null; 关闭错误日志
```

```
开启目录列表功能

autoindex on;
autoindex_exact_size; 文件大小
autoindex_localtime; 文件时间

server {
    listen 80;
    server_name 192.168.78.2;
    root html;
    index index.php;
    
}
```

```
 if 指令判断符号
 
 ==     判断是否相等
 !=     判断不相等
 
 ~      区分大小写正则匹配
 ~*     不区分大小写正则匹配
 
 !~     区分大小写正则不匹配
 ！~*   不区分大小写正则不匹配

-f      判断文件存在
!-f     判断文件不存在

-d      判断目录存在
!-d     判断目录不存在

-x      判断可执行文件
!~x     判断不可执行文件

```

更多请参考 nginx 官方网站
一键生成 [nginx配置](https://nginxconfig.io/)

