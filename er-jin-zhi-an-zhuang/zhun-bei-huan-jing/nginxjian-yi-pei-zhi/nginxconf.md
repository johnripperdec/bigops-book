# Nginx主配置文件nginx.conf

user  root root;

worker\_processes 8;

worker\_rlimit\_nofile 204800;



error\_log  /opt/ngxlog/error.log notice;

pid        /var/run/nginx.pid;



events {

    use epoll;

    worker\_connections  204800;

}



http {

    include       /etc/nginx/mime.types;

    default\_type  application/octet-stream;



    log\_format  main  "$remote\_addr $remote\_user \[$time\_local\] '$request\_method $host$request\_uri'"

                      "$request\_time $status $body\_bytes\_sent '$http\_referer'"

                      " '$http\_user\_agent' '$http\_x\_forwarded\_for'  '$request\_body'";



    access\_log  /opt/ngxlog/access.log  main;

    \#access\_log  /dev/null;



    keepalive\_timeout 30;

    sendfile    on;

    tcp\_nopush  on;

    tcp\_nodelay on;



    server\_names\_hash\_bucket\_size 128;

    large\_client\_header\_buffers 4 256k;

    client\_header\_buffer\_size 128k;

    client\_max\_body\_size 50m;

    client\_body\_buffer\_size 50m;

    client\_header\_timeout 1460;

    client\_body\_timeout 1460;

    send\_timeout 1460;

    

    fastcgi\_connect\_timeout 300;

    fastcgi\_send\_timeout 300;

    fastcgi\_read\_timeout 300;

    fastcgi\_buffer\_size 512k;

    fastcgi\_buffers 6 512k;

    fastcgi\_busy\_buffers\_size 512k;

    fastcgi\_temp\_file\_write\_size 512k;

    fastcgi\_intercept\_errors on; 

    proxy\_temp\_path /dev/shm/proxy\_temp;

    fastcgi\_temp\_path /dev/shm/fastcgi\_temp;

    client\_body\_temp\_path /dev/shm/client\_body\_temp;



    proxy\_connect\_timeout 30;

    proxy\_send\_timeout 30;

    proxy\_read\_timeout 60;

    proxy\_buffer\_size 4k;

    proxy\_buffers 4 32k;

    proxy\_busy\_buffers\_size 64k;

    proxy\_temp\_file\_write\_size 64k;

    proxy\_intercept\_errors  on;



    gzip on;

    gzip\_min\_length 1k;

    gzip\_buffers 4 16k;

    gzip\_comp\_level 2;

    gzip\_http\_version 1.0;

    gzip\_types text/plain text/xml text/css text/javascript application/json application/javascript application/x-javascript application/xml image/jpeg image/gif image/png;

    gzip\_vary on;

    gzip\_disable "MSIE \[1-6\]\.";



    add\_header Strict-Transport-Security "max-age=259200; includeSubdomains; preload";

    ssl\_session\_tickets on;

    ssl\_session\_cache shared:SSL:10m;

    ssl\_session\_timeout 1440m;



    ssl\_certificate /opt/bigops/config/nginx\_key/bigops.crt;

    ssl\_certificate\_key  /opt/bigops/config/nginx\_key/bigops.key.nopassword;



    ssl\_protocols TLSv1 TLSv1.1 TLSv1.2 TLSv1.3;

    ssl\_ciphers 'ECDHE-ECDSA-AES128-GCM-SHA256ECDHE-RSA-AES128-GCM-SHA256:ECDHE+AES128:RSA+AES128:ECDHE+AES256:RSA+AES256:ECDHE+3DES:RSA+3DES';

    ssl\_prefer\_server\_ciphers   on;



    \#charset gb2312;



    server {

        listen \*:80 default;

        server\_name \_ "";

        return 444;

        access\_log   off;

    }



    include /etc/nginx/conf.d/\*.conf;



}

