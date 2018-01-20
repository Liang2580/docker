# docker



Centos 7 .4 lnmp 的wordpress

文件全部放在/opt/dockerfile/lnmp 中
Dockerfile 文件为主的Dockerfile 

nginx-site.conf 为nginx的配置文件

start.sh  为启动脚本

supervisord.conf 这个得自己看把。



##################开始############


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

docker ps |awk '{print $1}'

9dd6e39bb995
d969c90a3663



curl -I http://192.168.57.142:94/wp-admin/install.php |grep HTTP 
HTTP/1.1 200 OK

curl -I http://192.168.57.142:98/wp-admin/install.php |grep HTTP 
HTTP/1.1 200 OK

curl -I http://192.168.57.142:97/wp-admin/install.php |grep HTTP 
HTTP/1.1 200 OK

curl -I http://192.168.57.142:96/wp-admin/install.php |grep HTTP 
HTTP/1.1 200 OK

curl -I http://192.168.57.142:95/wp-admin/install.php |grep HTTP 
HTTP/1.1 200 OK


netstat -nltp |grep dock |awk '{print $4}'

:::80

