# Docker方式安装MySQL

docker pull mysql:5.7 
这里开始尝试了没加5.7版本号，即最新版，结果外部访问不了，尝试配置了权限，没成，过程略，还是mysql不熟悉，再次尝试，加上5.7版本号重新执行即可，结论是，按教程一步一步来，最稳妥，前提是好教程，
sudo docker run -p 3306:3306 --name mysql -e MYSQL_ROOT_PASSWORD=123456 -d mysql:5.7
容器内连接
sudo docker exec -it mysql bash
mysql -uroot -p123456
容器外装mysql客户端口
为了方便，直接yum install mariadb*
容器外连接
mysql -h127.0.0.1 -uroot -p123456，这里加-h127.0.0.1和不加还不一样
远程连接，
网络配置开3306端口（阿里云安全组操作，略）
直接外网IP加3306即可连接

参考https://www.cnblogs.com/sablier/p/11605606.html