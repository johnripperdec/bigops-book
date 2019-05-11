# 主配置文件nginx.conf，**建议存放目录/etc/nginx/**

```
user  root root;
worker_processes 8;
worker_rlimit_nofile 204800;

error_log  /opt/ngxlog/error.log notice;
pid        /var/run/nginx.pid;

events {
    use epoll;
    worker_connections  204800;
}

http {
    include       /etc/nginx/mime.types;
    default_type  application/octet-stream;

    log_format  main  "$remote_addr $remote_user [$time_local] '$request_method $host$request_uri'"
                      "$request_time $status $body_bytes_sent '$http_referer'"
                      " '$http_user_agent' '$http_x_forwarded_for'  '$request_body'";

    access_log  /opt/ngxlog/access.log  main;
    #access_log  /dev/null;

    keepalive_timeout 30;
    sendfile    on;
    tcp_nopush  on;
    tcp_nodelay on;

    server_names_hash_bucket_size 128;
    large_client_header_buffers 4 256k;
    client_header_buffer_size 128k;
    client_max_body_size 50m;
    client_body_buffer_size 50m;
    client_header_timeout 1460;
    client_body_timeout 1460;
    send_timeout 1460;

    fastcgi_connect_timeout 300;
    fastcgi_send_timeout 300;
    fastcgi_read_timeout 300;
    fastcgi_buffer_size 512k;
    fastcgi_buffers 6 512k;
    fastcgi_busy_buffers_size 512k;
    fastcgi_temp_file_write_size 512k;
    fastcgi_intercept_errors on; 
    proxy_temp_path /dev/shm/proxy_temp;
    fastcgi_temp_path /dev/shm/fastcgi_temp;
    client_body_temp_path /dev/shm/client_body_temp;

    proxy_connect_timeout 30;
    proxy_send_timeout 30;
    proxy_read_timeout 60;
    proxy_buffer_size 4k;
    proxy_buffers 4 32k;
    proxy_busy_buffers_size 64k;
    proxy_temp_file_write_size 64k;
    proxy_intercept_errors  on;

    gzip on;
    gzip_min_length 1k;
    gzip_buffers 4 16k;
    gzip_comp_level 2;
    gzip_http_version 1.0;
    gzip_types text/plain text/xml text/css text/javascript application/json application/javascript application/x-javascript application/xml image/jpeg image/gif image/png;
    gzip_vary on;
    gzip_disable "MSIE [1-6]\.";

    add_header Strict-Transport-Security "max-age=259200; includeSubdomains; preload";
    ssl_session_tickets on;
    ssl_session_cache shared:SSL:10m;
    ssl_session_timeout 1440m;

    ssl_certificate /opt/bigops/config/nginx_key/bigops.crt;
    ssl_certificate_key  /opt/bigops/config/nginx_key/bigops.key.nopassword;

    ssl_protocols TLSv1 TLSv1.1 TLSv1.2 TLSv1.3;
    ssl_ciphers 'ECDHE-ECDSA-AES128-GCM-SHA256ECDHE-RSA-AES128-GCM-SHA256:ECDHE+AES128:RSA+AES128:ECDHE+AES256:RSA+AES256:ECDHE+3DES:RSA+3DES';
    ssl_prefer_server_ciphers   on;

    #charset gb2312;

    server {
        listen *:80 default;
        server_name _ "";
        return 444;
        access_log   off;
    }

    include /etc/nginx/conf.d/*.conf;

}
```



