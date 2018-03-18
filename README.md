# server-setup-steps
A set of steps to rebuilding my server until I have ansible or docker working

## user setup
- `useradd -m <new user>`
- `passwd <new user>`
- (install vim)
  - `sudo add-apt-repository ppa:jonathonf/vim`
  - `sudo apt-get update`
- `sudo apt-get install vim`
- `export EDITOR=vim`
- `visudo`
- (copy the `root ALL=(ALL...` line but for <new user>)
- login as new user
- `sudo apt-get install git`
- `ssh-keygen -t rsa -b 4096`
- add new ssh key to github
- `cd ~ && git clone git@github.com:js-jslog/dotfiles.git`
- `cd ~/dotfiles && ./setup.sh`

## docker
- `sudo apt-get install curl`
- `sudo apt-get install software-properties-common`
- `curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -`
- `sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"`
- `sudo apt-get update`
- `sudo apt-get install -y docker-ce`
  
# jslog
- `git clone git@github.com:js-jslog/jslog.git`
- `cd jslog && ./docker-deploy.sh`

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
