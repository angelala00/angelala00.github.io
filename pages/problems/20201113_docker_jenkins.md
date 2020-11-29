# Docker方式安装jenkins

docker search jenkins
docker pull jenkins
mkdir /opt/jenkins
docker run -d -p 8000:8080 -p 50000:50000 -v /opt/jenkins:/var/jenkins_home --name jenkins --restart always --privileged=true  -u root jenkins
docker: Error response from daemon: Mounts denied: 
The path /opt/jenkins is not shared from the host and is not known to Docker.
You can configure shared paths from Docker -> Preferences... -> Resources -> File Sharing.
See https://docs.docker.com/docker-for-mac for more info.

chmod 777 /opt/jenkins/
还是同样错
按照提示，找到Docker -> Preferences… -> File Sharing.添加Sharing
再执行可以了
中间遇到问题，重复执行docker命令的时候，报如下错
docker run -d -p 8000:8080 -p 50000:50000 -v /opt/jenkins:/var/jenkins_home --name jenkins --restart always --privileged=true  -u root jenkins
docker: Error response from daemon: Conflict. The container name "/jenkins" is already in use by container "2d8264041a160ec31564f56fc7fad4836bcdea0c39fce6886959e6beb262a4bb". You have to remove (or rename) that container to be able to reuse that name.
docker rm containerId
再执行即可
Jenkins在Docker方式启动成功
疑问，docker run命令第二次执行报错，需要删除原来的容器，这里需要重新理解一下，

访问http://localhost:8000可访问启动后的jenkins首页
密码cat /opt/jenkins/secrets/initialAdminPassword
安装推荐插件，全部安装失败，暂时跳过
设置用户名密码，全admin
进入系统，
系统管理，提示有新版本可以升级，我当前是2.60.3，提示可升级版本是2.249.3，暂时忽略
系统管理，插件管理，无可用插件，

到这里暂停
待后续有需要再回来继续，比如部署项目配置啥的，比如更新插件啥的


方法二
官网找到了这个，拉取的镜像不一样
docker pull jenkinsci/blueocean
docker run \
  -u root \
  --rm \
  -d \
  -p 8080:8080 \
  -p 50000:50000 \
  -v /opt/jenkins:/var/jenkins_home \
  -v /var/run/docker.sock:/var/run/docker.sock \
  jenkinsci/blueocean

阿里云按方法二安装后，装插件一步骤，提示无法连接到jenkins