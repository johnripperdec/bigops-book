# 操作系统

理论上支持所有Linux操作系统，建议使用：

* CentOS 6 x86 64位
* CentOS 7 x86 64位

# 依赖仓库

### epel仓库、remi仓库

**CentOS 6 x86 64位运行**

> wget -O /etc/yum.repos.d/CentOS-Base.repo [http://mirrors.aliyun.com/repo/Centos-6.repo](http://mirrors.aliyun.com/repo/Centos-6.repo)
>
> wget -O /etc/yum.repos.d/epel.repo [http://mirrors.aliyun.com/repo/epel-6.repo](http://mirrors.aliyun.com/repo/epel-6.repo)

**CentOS 7 x86 64位运行**

> wget -O /etc/yum.repos.d/CentOS-Base.repo [http://mirrors.aliyun.com/repo/Centos-7.repo](http://mirrors.aliyun.com/repo/Centos-7.repo)
>
> wget -O /etc/yum.repos.d/epel.repo [http://mirrors.aliyun.com/repo/epel-7.repo](http://mirrors.aliyun.com/repo/epel-7.repo)

### **remi仓库**

> remi包含最新版本 PHP 和 MySQL 包的 Linux 源，由 Remi 提供维护。请按照 [向导](https://rpms.remirepo.net/wizard/ "向导") 的指示安装配置。

# 依赖软件

Nginx、OpenSSL、Medusa等。

> yum -y install nginx openssl openssl-devel medusa
>
> \#创建Nginx日志目录
>
> mkdir /opt/ngxlog/

MySQL，建议版本为5.7或5.8，如果已安装就忽略。也可以安装其他MySQL发行版。

> yum -y install mysql-community-server mysql-community-client mysql-community-devel

### **建议配置**

[MySQL建议配置](/er-jin-zhi-an-zhuang/zhun-bei-huan-jing/mysqljian-yi-pei-zhi.md)

[Nginx主文件建议配置](/er-jin-zhi-an-zhuang/zhun-bei-huan-jing/nginxjian-yi-pei-zhi/nginxconf.md)

[Nginx统一登录建议配置](/er-jin-zhi-an-zhuang/zhun-bei-huan-jing/nginxjian-yi-pei-zhi/ssoconf.md)

[Nginx核心系统建议配置](/er-jin-zhi-an-zhuang/zhun-bei-huan-jing/nginxjian-yi-pei-zhi/workconf.md)

