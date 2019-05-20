### **下载文件页面**

[http://www.bigops.com/dl.html](http://www.bigops.com/dl.html)

### **下载文件到/opt目录，并解压文件**

> tar zxvf bigops-1.0.0.tar.gz

### 检查运行环境

> sh /opt/bigops/bin/check\_env.sh

### 启动安装向导

> sh /opt/bigops/bin/start.sh

**检查服务是否启动**

> \# netstat -nptl\|egrep '30002\|30003'
>
> tcp6       0      0 127.0.0.1:30002         :::\*                    LISTEN      2710/java
>
> tcp6       0      0 127.0.0.1:30003         :::\*                    LISTEN      2710/java

**访问安装向导**

[http://work.bigops.com/wizard/](http://work.bigops.com/wizard/)

![](/assets/Xnip2019-05-20_16-05-02.jpg)

