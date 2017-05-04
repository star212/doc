## 服务器配置

### 新系统 centos6.4
* 更新源 <http://mirrors.163.com/.help/centos.html>
* <https://blog.itnmg.net/centos-yum-source/>
* 阿里云<http://mirrors.aliyun.com/help/centos>
* yum update
* yum clean all
* yum makecache
* yum install vim

### 压缩解压
* tar cvzf xxx.tar.gz xxx/ 压缩
* tar zxvf FileName.tar.gz 解压

### 安装apache + php + mysql
* yum install httpd mod_ssl
* yum install php mod_fcgid
* yum install mysql mysql-server php-mysql
* chkconfig --list httpd 启动状态查看
* chkconfig --levels 235 mysqld on
* <?php phpinfo();?>
* apache 报错
	```
	Starting httpd: httpd: apr_sockaddr_info_get() failed for MyCloudServer
	httpd: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
	```

#### mysql
* 备份文件中可以查看使用的mysql版本，以及phpmyadmin和php的版本
* 之前导出的sql文件报错了，备份不完全。
* 采用服务器上的mysql数据库文件进行恢复。
	- 先用2013年的备份安全的文件恢复表结构
	- 再用数据库文件覆盖（/var/lib/mysql）
	- 修改拥有者`chown mysql:mysql *.*`

### 安装phpmyadmin
* yum install epel-release
* yum install phpmyadmin
* vim /etc/httpd/conf.d/phpMyAdmin.conf 修改ip，并Allow from 58.64.177.26保留这句，其他注释
* %s/127\.0\.0\.1/58.64.177.26/g
* vim /etc/phpMyAdmin/config.inc.php 修改auth_type为http

### 安装ispconfig
* <https://www.vultr.com/docs/install-ispconfig-on-centos-6-x64>


### 安装memcached
* yum install memcached
* service memcached start
* vim /etc/sysconfig/memcached

