# 统一登录的Nginx配置文件

**建议目录/etc/nginx/conf.d/**

**修改2处server\_name为你的域名**

```
upstream sso {
    server localhost:30001;
}

server {  
    listen 80;  
    server_name sso.bigops.cn;
    rewrite ^(.*)$ https://$server_name$1 permanent; 
}  

server {
    listen 443 ssl;
    server_name  sso.bigops.cn;
    access_log  /opt/ngxlog/sso.access.log main;
    error_log  /opt/ngxlog/sso.error.log;

    location /signin {
        proxy_hide_header content-security-policy;
        proxy_hide_header X-Frame-Options;
        proxy_connect_timeout 700s;
        proxy_send_timeout 700s;
        proxy_read_timeout 700s;
        proxy_store off;
        proxy_cache off;
        proxy_buffering off;
        proxy_set_header Cache-Control no-store;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
        client_max_body_size 2000m;
        proxy_pass http://sso;
    }
}
```



