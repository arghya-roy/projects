jenkins_with_remote_server_ec2_nodejs_systemd.md
```
new items - freestyle
```
```
git - https://github.com/arghya-roy/node-app.git
```
```
Build Environment
       Provide Node & npm bin/ folder to PATH = checked
       nodejs installation = nodejs ( before that go to global
                                      configuration - nodejs
                                                      install automatically )
      Cache location = default
Build  
       execute shell - npm install
post build 
      publish over ssh-
           Source files = **/*
           Remote directory = .
           exec command = sudo systemctl stop index;
                          sudo systemctl start index ( before that we need to add
                                                       nodejs in systemd )
```
