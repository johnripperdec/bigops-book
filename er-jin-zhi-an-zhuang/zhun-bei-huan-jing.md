# 操作系统

理论上支持所有Linux操作系统，建议使用：

* CentOS 6 x86 64位
* CentOS 7 x86 64位

# 依赖仓库

epel仓库、remi仓库

**CentOS 6 x86 64位运行**

> wget -O /etc/yum.repos.d/CentOS-Base.repo [http://mirrors.aliyun.com/repo/Centos-6.repo](http://mirrors.aliyun.com/repo/Centos-6.repo)
>
> wget -O /etc/yum.repos.d/epel.repo [http://mirrors.aliyun.com/repo/epel-6.repo](http://mirrors.aliyun.com/repo/epel-6.repo)

**CentOS 7 x86 64位运行**

> wget -O /etc/yum.repos.d/CentOS-Base.repo [http://mirrors.aliyun.com/repo/Centos-7.repo](http://mirrors.aliyun.com/repo/Centos-7.repo)
>
> wget -O /etc/yum.repos.d/epel.repo [http://mirrors.aliyun.com/repo/epel-7.repo](http://mirrors.aliyun.com/repo/epel-7.repo)

**remi仓库**

> remi包含最新版本 PHP 和 MySQL 包的 Linux 源，由 Remi 提供维护。请按照 [向导](https://rpms.remirepo.net/wizard/ "向导") 的指示安装配置。

# 依赖软件

Nginx、PHP、MySQL、OpenSSL、Medusa等。

如果没有Nginx、PHP，运行以下命令安装，如果有忽略。

> sed -i 's/enabled=0/enabled=1/' /etc/yum.repos.d/remi.repo 
>
> yum-config-manager --enable remi-php72
>
> yum -y install nginx php php-mysql php-gd php-fpm php-mbstring mcrypt php-mcrypt git openssl-devel pcre-devel php-bcmath php-xml php-xmlrpc php-ldap zlib zlib-devel

优化PHP，根据情况运行。

> ln -s /usr/lib64/mysql/libmysqlclient.so /usr/lib/libmysqlclient.so
>
> sed -i 's/user = apache/user = nginx/g' /etc/php-fpm.d/www.conf
>
> sed -i 's/group = apache/group = nginx/g' /etc/php-fpm.d/www.conf
>
> sed -i 's/;listen.owner = nobody/listen.owner = nginx/g' /etc/php-fpm.d/www.conf
>
> sed -i 's/;listen.group = nobody/listen.group = nginx/g' /etc/php-fpm.d/www.conf
>
> sed -i 's/;rlimit\_files = 1024/rlimit\_files = 51200/g' /etc/php-fpm.d/www.conf
>
> sed -i 's\#^listen =.\*\#listen = /var/run/php-fpm.socket\#g' /etc/php-fpm.d/www.conf
>
> sed -i "s@^pm.start\_servers.\*@pm.start\_servers = 10@" /etc/php-fpm.d/www.conf
>
> sed -i "s@^pm.min\_spare\_servers.\*@pm.min\_spare\_servers = 10@" /etc/php-fpm.d/www.conf
>
> sed -i "s@^pm.max\_spare\_servers.\*@pm.max\_spare\_servers = 30@" /etc/php-fpm.d/www.conf
>
> sed -i "s@^pm.max\_children.\*@pm.max\_children = 30@" /etc/php-fpm.d/www.conf
>
> sed -i 's/;cgi.fix\_pathinfo=1/cgi.fix\_pathinfo=1/g' /etc/php.ini 
>
> sed -i 's/^post\_max\_size.\*/post\_max\_size = 16M/g' /etc/php.ini
>
> sed -i 's/^max\_execution\_time.\*/max\_execution\_time = 300/g' /etc/php.ini
>
> sed -i 's/^max\_input\_time.\*/max\_input\_time = 300/g' /etc/php.ini
>
> sed -i 's/^;date.timezone.\*/date.timezone = PRC/g' /etc/php.ini
>
> sed -i 's/^memory\_limit.\*/memory\_limit = 512M/g' /etc/php.ini







