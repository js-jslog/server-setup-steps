1. Modify host key from ctrlRight (is it this which breaks the alt-tab)
2. install chromium
3. install vim8
4. `ssh-keygen -t rsa -b 4096`
5. sudo apt-get install connect-proxy
6. set vim to be default editor by adding the following to .bashrc
```
export EDITOR='vim'
```
7. create the following at ~/.ssh/config
```
IdentityFile ~/.ssh/id_rsa
Host *
  ForwardAgent yes

Host *github.com
  ProxyCommand connect -H websensegateway:8080 %h %p
  port 443
  Hostname ssh.github.com
  User git
```
8. install chromium
9. `sudo apt-get install git`
10. `sudo apt-get install curl`
11. install nvm
12. `nvm install stable`
13. `sudo apt-get install npm`
14. `npm install -g eslint`
15. `npm install -g eslint-config-airbnb-base`
16. `sudo apt-get install default-jdk`
17. create the following folder structure under ~
```
~
 - rsl
  - ansible-rsl
  - local_disk
   - data
  - logs
  - shared_disk
   - data
  - tomcat `checkout R6.12_T7.0.70`
  - webapps
   - R6_24
   - vani_devt
    - local_overrides.js `figure out what to put in here from ansible`
    - META_INF/context.xml `figure out what to put in here from ansible`
   - cdn
   - protected_properties.js `figure out what to put in here from ansible`
```
