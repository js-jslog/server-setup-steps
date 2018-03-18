# server-setup-steps
A set of steps to rebuilding my server until I have ansible or docker working

## user setup
`useradd -m <new user>`
`passwd <new user>`
(install vim)
`sudo add-apt-repository ppa:jonathonf/vim`
`sudo apt-get update`
`sudo apt-get install vim`
`export EDITOR=vim`
`visudo`
(copy the `root ALL=(ALL...` line but for <new user>)

## nginx config
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
