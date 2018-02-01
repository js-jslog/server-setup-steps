# server-setup-steps
A set of steps to rebuilding my server until I have ansible or docker working


# nginx config
This works
```
upstream jslog {
    server 127.0.0.1:3000;
    keepalive 8;
}

server {
        listen 80;
    server_name www.jslog.co.uk;
    access_log /var/log/nginx/jslog.log;
        location / {
        proxy_pass http://127.0.0.1:3000/;
        }
}

```
