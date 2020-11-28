# Docker安装
阿里云ECS，美国弗吉尼亚州，centos7.4安装docker


1.sudo yum install -y yum-utils device-mapper-persistent-data lvm2 
2.sudo yum-config-manager --add-repo https://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo
这里原以为本来是国外的服务器，不设置ali的代理可能也不会慢，后面执行到第三步的时候找不到镜像，回来执行了这一步，后面才能继续，疑问点是，代理服务会有比国外镜像仓库多的镜像么？
3.sudo yum install docker-ce
4.
sudo systemctl enable docker
sudo systemctl start docker

后面没有继续

直接试了
docker pull mysql
速度还挺快

参考https://www.cnblogs.com/myzony/p/9071210.html