# docker
Centos 7 .4 lnmp 的wordpress

文件全部放在/opt/dockerfile/lnmp 中

Dockerfile 文件为主的Dockerfile 
nginx-site.conf 为nginx的配置文件
start.sh  为启动脚本
supervisord.conf 这个得自己看把。



##################开始################################################
首先需要pull 一个centos 的镜像
#docker pull centos

构建
#docker build -t  liang/lnmp /opt/dockerfile/lnmp

如果没有问题就会出现一个Successfully built $(ID)

后面运行容器

#docker run --name liang -d -p 8888:8888 liang/lnmp
# docker run -it -d -p 100:8888 liang/lnmp
# docker run -it -d -p 97:8888 liang/lnmp
访问呢就访问http://IP:8888
多建立几个

[root@linux-node1 lnmp]# docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                                   NAMES
9dd6e39bb995        liang/lnmp          "/bin/bash /root/star"   2 minutes ago       Up 2 minutes        22/tcp, 80/tcp, 0.0.0.0:100->8888/tcp   hungry_morse
d969c90a3663        liang/lnmp          "/bin/bash /root/star"   2 minutes ago       Up 2 minutes        22/tcp, 80/tcp, 0.0.0.0:99->8888/tcp    evil_easley
ae545369a192        liang/lnmp          "/bin/bash /root/star"   2 minutes ago       Up 2 minutes        22/tcp, 80/tcp, 0.0.0.0:98->8888/tcp    loving_yalow
6dfa32e97e39        liang/lnmp          "/bin/bash /root/star"   2 minutes ago       Up 2 minutes        22/tcp, 80/tcp, 0.0.0.0:97->8888/tcp    hungry_mccarthy
242dbc56bf9d        liang/lnmp          "/bin/bash /root/star"   2 minutes ago       Up 2 minutes        22/tcp, 80/tcp, 0.0.0.0:96->8888/tcp    peaceful_hodgkin
cdd3e7fe5b50        liang/lnmp          "/bin/bash /root/star"   2 minutes ago       Up 2 minutes        22/tcp, 80/tcp, 0.0.0.0:95->8888/tcp    sharp_hopper
d64cbae392ff        liang/lnmp          "/bin/bash /root/star"   2 minutes ago       Up 2 minutes        22/tcp, 80/tcp, 0.0.0.0:94->8888/tcp    jovial_euclid
87657b6c7b74        liang/lnmp          "/bin/bash /root/star"   2 minutes ago       Up 2 minutes        22/tcp, 80/tcp, 0.0.0.0:93->8888/tcp    ecstatic_swirles
c58fcd28d14f        liang/lnmp          "/bin/bash /root/star"   2 minutes ago       Up 2 minutes        22/tcp, 80/tcp, 0.0.0.0:92->8888/tcp    sharp_yalow
110c183b8f58        liang/lnmp          "/bin/bash /root/star"   2 minutes ago       Up 2 minutes        22/tcp, 80/tcp, 0.0.0.0:91->8888/tcp    gloomy_ptolemy
4eba98c24d1f        liang/lnmp          "/bin/bash /root/star"   2 minutes ago       Up 2 minutes        22/tcp, 80/tcp, 0.0.0.0:90->8888/tcp    kickass_raman
ad8665e57551        liang/lnmp          "/bin/bash /root/star"   2 minutes ago       Up 2 minutes        22/tcp, 80/tcp, 0.0.0.0:89->8888/tcp    jovial_einstein
b5669fa6bbca        liang/lnmp          "/bin/bash /root/star"   2 minutes ago       Up 2 minutes        22/tcp, 80/tcp, 0.0.0.0:88->8888/tcp    adoring_fermat
8c0773c8c7a2        liang/lnmp          "/bin/bash /root/star"   2 minutes ago       Up 2 minutes        22/tcp, 80/tcp, 0.0.0.0:87->8888/tcp    distracted_sinoussi
7c20e03c3685        liang/lnmp          "/bin/bash /root/star"   3 minutes ago       Up 3 minutes        22/tcp, 0.0.0.0:83->80/tcp              determined_almeida
43693d688cd5        liang/lnmp          "/bin/bash /root/star"   36 minutes ago      Up 36 minutes       22/tcp, 80/tcp, 0.0.0.0:80->8888/tcp    liang2
[root@linux-node1 lnmp]# 

那么都测试一下把
[root@linux-node1 lnmp]# curl -I http://192.168.57.142:90/wp-admin/install.php
HTTP/1.1 200 OK
Server: nginx/1.12.2
Date: Sat, 20 Jan 2018 14:40:06 GMT
Content-Type: text/html; charset=utf-8
Connection: keep-alive
X-Powered-By: PHP/5.4.16
Expires: Wed, 11 Jan 1984 05:00:00 GMT
Cache-Control: no-cache, must-revalidate, max-age=0

[root@linux-node1 lnmp]# curl -I http://192.168.57.142:91/wp-admin/install.php
HTTP/1.1 200 OK
Server: nginx/1.12.2
Date: Sat, 20 Jan 2018 14:40:10 GMT
Content-Type: text/html; charset=utf-8
Connection: keep-alive
X-Powered-By: PHP/5.4.16
Expires: Wed, 11 Jan 1984 05:00:00 GMT
Cache-Control: no-cache, must-revalidate, max-age=0

[root@linux-node1 lnmp]# curl -I http://192.168.57.142:92/wp-admin/install.php
HTTP/1.1 200 OK
Server: nginx/1.12.2
Date: Sat, 20 Jan 2018 14:40:13 GMT
Content-Type: text/html; charset=utf-8
Connection: keep-alive
X-Powered-By: PHP/5.4.16
Expires: Wed, 11 Jan 1984 05:00:00 GMT
Cache-Control: no-cache, must-revalidate, max-age=0

[root@linux-node1 lnmp]# curl -I http://192.168.57.142:93/wp-admin/install.php
^[[A^[[DHTTP/1.1 200 OK
Server: nginx/1.12.2
Date: Sat, 20 Jan 2018 14:40:17 GMT
Content-Type: text/html; charset=utf-8
Connection: keep-alive
X-Powered-By: PHP/5.4.16
Expires: Wed, 11 Jan 1984 05:00:00 GMT
Cache-Control: no-cache, must-revalidate, max-age=0

[root@linux-node1 lnmp]# curl -I http://192.168.57.142:94/wp-admin/install.php
HTTP/1.1 200 OK
Server: nginx/1.12.2
Date: Sat, 20 Jan 2018 14:40:19 GMT
Content-Type: text/html; charset=utf-8
Connection: keep-alive
X-Powered-By: PHP/5.4.16
Expires: Wed, 11 Jan 1984 05:00:00 GMT
Cache-Control: no-cache, must-revalidate, max-age=0




