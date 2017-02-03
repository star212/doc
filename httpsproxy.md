# 关于用http代理服务器代理https协议的问题

### 问题描述
* 手机上需要挂代理来测试页面，如果页面上有登陆的需求。就有可能需要代理https的协议。那么问题来了，如何让http代理服务器代理https协议呢？

### 以charles为例

* 首先 charles 有一个白名单，在ssl的tab下。需要添加一条要访问https的域名的记录。
* 在手机上安装charles的证书。<http://www.charlesproxy.com/documentation/using-charles/ssl-certificates/> 文中的ssl.zip文件。下载并解压缩到一个服务器目录，让手机能访问到。然后下载安装即可。
