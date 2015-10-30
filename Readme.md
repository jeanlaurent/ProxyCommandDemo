Build
```
docker build -t my_ssh .
```

throw a bunch of ssh host
```
docker run -td -p 2000:22 --name host1 my_ssh
docker run -td -p 2001:22 --name host2 my_ssh
```
Try to log to host2 through host1
```
ssh root@192.168.99.100 -p 2001 -o ProxyCommand="ssh root@192.168.99.100 -p 2000 exec nc %h %p 2>/dev/null"
```
or put `ssh/config` in 
```
Host *
  ProxyCommand ssh root@192.168.99.100 -p 2000 exec nc %h %p 2>/dev/null
```

Dockerfile from https://docs.docker.com/examples/running_ssh_service/, explaination on ProxyCommand from http://blog.ociru.net/2013/09/24/ssh-proxycommand
