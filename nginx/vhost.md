## nginx 配置虚拟主机
`nginx` 配置虚拟主机十分简单，只需添加 `server` ,修改 `server_name` 、`root` 即可。
```
server {
    listen 80;
    server_name wordpress.dev;
    access_log /data/wwwlogs/access_nginx.log combined;
    root /data/www/wordpress;
    index index.html index.htm index.php;
    location /nginx_status {
        stub_status on;
        access_log off;
        allow 127.0.0.1;
        deny all;
        }
    location ~ [^/]\.php(/|$) {
        #fastcgi_pass remote_php_ip:9000;
        fastcgi_pass unix:/dev/shm/php-cgi.sock;
        fastcgi_index index.php;
        include fastcgi.conf;
        }
    location ~ .*\.(gif|jpg|jpeg|png|bmp|swf|flv|ico)$ {
        expires 30d;
        access_log off;
        }
    location ~ .*\.(js|css)?$ {
        expires 7d;
        access_log off;
        }
    }
```

默认 `nginx.conf`
```
server {
    listen 80;
    server_name _;
    access_log /data/wwwlogs/access_nginx.log combined;
    root /data/wwwroot/default;
    index index.html index.htm index.php;
    location /nginx_status {
        stub_status on;
        access_log off;
        allow 127.0.0.1;
        deny all;
        }
    location ~ [^/]\.php(/|$) {
        #fastcgi_pass remote_php_ip:9000;
        fastcgi_pass unix:/dev/shm/php-cgi.sock;
        fastcgi_index index.php;
        include fastcgi.conf;
        }
    location ~ .*\.(gif|jpg|jpeg|png|bmp|swf|flv|ico)$ {
        expires 30d;
        access_log off;
        }
    location ~ .*\.(js|css)?$ {
        expires 7d;
        access_log off;
        }
    }
```
