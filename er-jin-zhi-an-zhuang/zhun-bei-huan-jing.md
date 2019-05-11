# 操作系统

理论上支持所有Linux操作系统，建议使用：

* CentOS 6 x86 64位
* CentOS 7 x86 64位

# 依赖仓库

系统基本仓库、epel仓库、remi仓库。

**CentOS 5 x86 64位运行**

> wget -O /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-5.repo
>
> wget -O /etc/yum.repos.d/epel.repo http://mirrors.aliyun.com/repo/epel-5.repo

**CentOS 6 x86 64位运行**

> wget -O /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-6.repo
>
> wget -O /etc/yum.repos.d/epel.repo http://mirrors.aliyun.com/repo/epel-6.repo

**CentOS 7 x86 64位运行**

> wget -O /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-7.repo
>
> wget -O /etc/yum.repos.d/epel.repo http://mirrors.aliyun.com/repo/epel-7.repo

**remi仓库**

> remi包含最新版本 PHP 和 MySQL 包的 Linux 源，由 Remi 提供维护。请按照 [向导](https://rpms.remirepo.net/wizard/ "向导") 的指示安装配置。

# 依赖软件

Nginx、PHP、MySQL、OpenSSL、Medusa等。

如果没有Nginx、PHP，运行以下命令安装，如果有忽略。

> yum -y install nginx php



