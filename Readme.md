```
docker build -t my_ssh .
docker run -td -p 2000:22 --name host1 my_ssh
docker run -td -p 2001:22 --name host2 my_ssh
 ssh root@192.168.99.100 -p 2001 -o ProxyCommand="ssh root@192.168.99.100 -p 2000 exec nc %h %p 2>/dev/null"
```
