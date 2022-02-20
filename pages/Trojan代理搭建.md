---
title: Trojan代理搭建
date: 2020-7-12 14:41:41
tags: [科学上网,Trojan代理]
password: "0210"
hidden: true
categories: 
- 科学上网
description: 新兴代理协议Trojan + nginx的搭建过程
---

## Trojan

trojan是最近兴起的网络工具，出来时间的比较短，
它主要原理是把流量伪装成常见的https流量，虽然v2ray也能实现伪装https，
但是与trojan比起来多了很多层加密，所以连接速度也会慢慢上很多。
目前trojan使用的人数应该是比不上v2ray的，官方客户端也很简陋，就是个控制台，
生态也不是很完善。
## 声明

目前翻墙还是违法的，虽然有各种伪装翻墙手段，但是既然翻墙了就有可能会被GFW检测到，
同时也可能会被网警查到。**所以请不要翻墙干违法的事情，身为国家公民，有义务去维护国家利益，
而不是损害国家利益。** ~~所以原则上不建议翻墙~~ ，但是有的时候还有有需要的，比如github
翻墙加载下载速度都比直连快;-)
- ## 准备
  
  trojan项目官网：[https://github.com/trojan-gfw](https://github.com/trojan-gfw)
  
  |trojan win客户端下载 | 安卓 | linux | mac | ios|
  |--------------------|---|-------|---|---|
  |[trojan](https://github.com/trojan-gfw/trojan/releases)|[igniter](https://github.com/trojan-gfw/igniter/releases)| [trojan](https://github.com/trojan-gfw/trojan/releases)|[trojan-mac](https://github.com/trojan-gfw/trojan/releases)|iphone/ipad 建议使用shadowrocket|
#### 服务端

前置条件
- 需要一台国外的vps，系统建议centos7；vps商家新手建议 <font color=#00ffff size=3>vultr</font>
- 域名；域名可以从国外namesilo或者namecheap购买，或者国内腾讯云，阿里云购买
- 域名的证书，可从**let's ENcrypt**获取免费证书，或者腾讯云阿里云都提供免费证书
- 使用bitvise或者xshell连接linux服务器
  
  安装trojan服务端,以centos7为例
  ```
  sudo bash -c "$(curl -fsSL https://raw.githubusercontent.com/trojan-gfw/trojan-quickstart/master/trojan-quickstart.sh)"
  ```
  安装完成后，trojan配置文件是在 `/usr/local/etc/trojan/config.json`
  
  初始内容是
  ```
  {
    "run_type": "server", 
    "local_addr": "0.0.0.0",
    "local_port": 443,
    "remote_addr": "127.0.0.1",
    "remote_port": 80,
    "password": [
        "password1",
        "password2"
    ],
    "log_level": 1,
    "ssl": {
        "cert": "/path/to/certificate.crt",
        "key": "/path/to/private.key",
        "key_password": "",
        "cipher": "ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-CHACHA20-POLY1305:ECDHE-RSA-CHACHA20-POLY1305:DHE-RSA-AES128-GCM-SHA256:DHE-RSA-AES256-GCM-SHA384",
        "cipher_tls13": "TLS_AES_128_GCM_SHA256:TLS_CHACHA20_POLY1305_SHA256:TLS_AES_256_GCM_SHA384",
        "prefer_server_cipher": true,
        "alpn": [
            "http/1.1"
        ],
        "reuse_session": true,
        "session_ticket": false,
        "session_timeout": 600,
        "plain_http_response": "",
        "curves": "",
        "dhparam": ""
    },
    "tcp": {
        "prefer_ipv4": false,
        "no_delay": true,
        "keep_alive": true,
        "reuse_port": false,
        "fast_open": false,
        "fast_open_qlen": 20
    },
    "mysql": {
        "enabled": false,
        "server_addr": "127.0.0.1",
        "server_port": 3306,
        "database": "trojan",
        "username": "trojan",
        "password": ""
    }
  }
  ```
- `local_port`是要监听的端口，默认443，不要改
- `remote_addr`和`remote_port`:非trojan协议是，请求将转发
  的地址和端口。可以填有效的ip/端口 。**如果你要在本机搭建网站请保持默认不要更改。**
- `password`密码，需要几个账号就，几个密码，**最后一行不要有逗号**
- `cert`&`key`,证书和域名，腾讯云申请的证书请选择nginx版的
- `key_password`，证书如果有密码就填上，无不要填
- `alpn`混淆默认就好
  
  修改好配置文件后，保存，然后输入linux命令设置开机启动：
  ```
  systemctl enable trojan
  ```
  再启动trojan：
  ```
  systemctl start trojan
  ```
  检查是否在运行：``ss -lp | grep trojan``,有输出内容则正常
  ，输出为空，可能是
- config.json文件语法出错
- 开了selinux，请先关闭在启动。关闭:``setenforce 0``
  
  ``service iptables status``查看防火墙状态
  ，如果在运行请放行端口 
  ```
  firewall-cmd --permanent --add-service=https # 端口是443
  firewall-cmd --permanent --add-port=端口号/tcp # 其他端口号
  firewall-cmd --reload # 重新加载防火墙
  ```
  或者永久关闭防火墙（**不建议**）
  ```
  # 永久关闭防火墙
  
  chkconfig iptables off  
  
  # 永久关闭后重启
  
  chkconfig iptables on　　
  ```
### 在本服务器安装网站伪装
GFW是根据特征值来封锁的，如果你长时间大流量访问一个网站，它来查看发现网站不存在
，这明显有问题，所以建议设置伪装站。如果原本有nginx部署的网站，也可以参考此来伪装

安装nginx
```
##安装
yum install -y epel-release && yum install -y nginx
##设置开机自启并启动
systemctl enable nginx; systemctl start nginx
##放行防火墙
firewall-cmd --permanent --add-service=http
##防火墙重新加载配置
firewall-cmd --reload
```

伪装网站模版可以百度搜索下载
直接上传到`/usr/share/nginx`下

nginx配置文件路径`/etc/nginx/nginx.conf`

把原始的`nginx.conf`改成如下所示
ps:**只改动server{}块，其他不要动，把原来的是server{}改掉，再添加一个强制转发https/443端口的server{}块**
```
server {
      listen 127.0.0.1:80;
      server_name example.com;#域名
      root  /usr/share/nginx/example.com;#网页文件夹路径
      index index.html; #自己的网页主页
      
      ssl_certificate   /etc/pki/nginx/server.crt;#改成自己的证书路径
      ssl_certificate_key   /etc/pki/nginx/private/server.key;#改成自己的证书秘钥路径
      ssl_protocols TLSv1.1 TLSv1.2 TLSv1.3;
      ssl_ciphers ECDHE-RSA-AES128-GCM-SHA256:HIGH:!aNULL:!MD5:!RC4:!DHE;
      ssl_prefer_server_ciphers on;
      ssl_session_cache shared:SSL:10m;
      ssl_session_timeout 10m;

      # Load configuration files for the default server block.
      include /etc/nginx/default.d/*.conf;

      location / {
          index index.html;
      }

      error_page 404 /404.html;
          location = /40x.html {
      }

      error_page 500 502 503 504 /50x.html;
          location = /50x.html {
      }
  }

server {
  listen 80 default_server;
  listen [::]:80 default_server;
  server_name example.com;
  rewrite ^(.*)$ https://${server_name}$1 permanent; 
  }
```
把上面的example.com改成自己的域名

**改好后保存，``nginx -t``检查配置文件是否有错误，没错误输入`nginx -s reload`重新加载配置文件**
### 客户端配置
- `local_port`改成你想要的端口
- `remote_addr`改成你服务器域名，也就是nginx里面填的域名
- `remote_port`服务器监听的端口，443
- `password`服务器trojan设置的密码
  其他可以不用改，然后保存就可以启动了。
  无法运行请先**先双击“VC_redist.x86.exe”安装依赖，然后再运行**
  
  设置系统代理上网
  --
  打开设置->网络和Internet->代理
  
  ![](https://cdn.cacher.io/attachments/u/3d41edeyhrwt3/KqKlwMUGmQyW92puGrF5XayMFTssHEVq/代理.PNG)
  
  使用代理服务器
  地址`127.0.0.1`端口填trojan客户端填的`local_port`
  
  下面一栏填入
  ```
  localhost;127.*;10.*;172.16.*;172.17.*;172.18.*;172.19.*;172.20.*;172.21.*;172.22.*;172.23.*;172.24.*;172.25.*;172.26.*;172.27.*;172.28.*;172.29.*;172.30.*;172.31.*;172.32.*;192.168.*
  ```
  请勿将代理服务器用于本地（Intranet）地址**选上**
  最后保存
### 有v2rayN客户端的
在v2rayN上添加Socks服务器
服务器地址填`127.0.0.1`,服务器端口填你上面填的端口，别名trojan，然后保存就可以使用了