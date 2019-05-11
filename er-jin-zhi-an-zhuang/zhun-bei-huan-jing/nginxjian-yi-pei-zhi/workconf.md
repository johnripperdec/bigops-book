# 核心系统work的Nginx配置文件，建议路径/etc/nginx/conf.d/

### 修改server\_name为你的域名

```
upstream workbe {
    server localhost:30003;
}

server {
    listen  80;
    server_name  work.bigops.cn;
    access_log  /opt/log/nginx/work.access.log main;
    error_log  /opt/log/nginx/work.error.log;
    root  /opt/bigops/workfe;
    index index.html index.htm;

    location ~* ^/dist/.*\.(ico|gif|jpg|jpeg|png)$ {
        expires 1d;
        access_log off;
        log_not_found off;
    }

    location /api {
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
        proxy_pass http://workbe;
    }

}
```



