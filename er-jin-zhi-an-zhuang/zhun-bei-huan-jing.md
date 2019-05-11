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

Nginx、MySQL、OpenSSL、Medusa等。

> yum -y install nginx openssl openssl-devel medusa

如果有MySQL就忽略，如果没有就运行，也可以安装其他MySQL发行版。

建议版本5.8。

> yum -y install mysql-community-server mysql-community-client mysql-community-devel

MySQL数据库的配置，建议设置如下，以下为一部分配置。

\[client\]

default-character-set=utf8mb4

port=3306

socket=/var/lib/mysql/mysql.sock

\[mysql\] 

default-character-set=utf8mb4

\[mysqld\]

character-set-client-handshake=FALSE

character-set-server=utf8mb4

collation-server=utf8mb4\_unicode\_ci

init\_connect='SET NAMES utf8mb4'

sql\_mode=STRICT\_TRANS\_TABLES,NO\_ZERO\_IN\_DATE,NO\_ZERO\_DATE,ERROR\_FOR\_DIVISION\_BY\_ZERO,NO\_AUTO\_CREATE\_USER,NO\_ENGINE\_SUBSTITUTION

