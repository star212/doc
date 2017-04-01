## 用途
* 和服务端联调的时候，服务端同学的本地环境采用的是8080端口，预发和线上都是才用80端口
* def dev 启动的服务不能开在80端口，但是我们调试的时候，需要用到80端口的情况下。
* 避免与本地的已经存在的80端口冲突。

## 解决方案
* 通过手机发起一个请求的流程如下：
![screenshot.png](http://ata2-img.cn-hangzhou.img-pub.aliyun-inc.com/04507772540b8c1c2bd8c9b7b30296a1.png)
* 除了apache以外我们可以用其他的一些工具都可以做到比如node，nginx。但是如上文所说apache是mac的标配。
* 如图所示，我们在apache上建立了3个vhost。通过不同的域名来访问。[如何新建vhosts](https://httpd.apache.org/docs/2.4/vhosts/examples.html)
* 在httpd.conf中（一般在/etc/apache2/ 下），建议再打开如下2个模块，打开方法为取消注释：

```
LoadModule vhost_alias_module libexec/apache2/mod_vhost_alias.so
LoadModule proxy_module libexec/apache2/mod_proxy.so
```

* 第一个模块可以使vhosts支持alias，别名解析。第二个模块为开启代理。[proxypass的配置文档](http://httpd.apache.org/docs/current/mod/mod_proxy.html#proxypass)
* 这里推荐使用proxypass，但是也有另外的方案：

```
<VirtualHost *:80>
    ServerAdmin xing.qux@alibaba-inc.com
    ServerName local.daily.taobao.net
    ServerAlias gmall.taobao.com
    ServerAlias local.m.taobao.com

    RewriteEngine on
    RewriteRule ^/(.*)         http://%{HTTP_HOST}:3333/$1 [P]

    ErrorLog "/private/var/log/apache2/error_log"
    CustomLog "/private/var/log/apache2/access_log" common
</VirtualHost>
```
* 以上方案通过rewrite模块实现，[详细说明](http://httpd.apache.org/docs/current/rewrite/flags.html#flag_p)

* 在配置apache的过程中，我们还会用到几个有用的命令：

```
sudo apachectl restart #重启服务
sudo apachectl configtest #检查配置是否正确
```

* `/var/log/apache2` 这个目录下会有apache的访问信息和错误日志。可以方便我们去排查各种问题。

## 总结
* 经过以上配置，基本上是一劳永逸，无需再改动或小改动就可以适应不同域名以及各种端口号的情况了。


