# 开始go

tags:[go,疑问,问题,待研究]

工具站项目现在需要后端支持了，所以开始了后端的选型  
第一反应是用SpringBoot，后转念一想，公司正好有一项目需要用go来开发，我这个为什么不选择用go呢，把公司和个人的需求结合起来，双收益  
后来又思考到了Java与go，python等语言的对比，感觉好像Java很重，庞大，为什么会有这种感觉？go，python，node等都有快速入手的方式，Java怎么好像没有？maven不就是干这事的么？是我们没用对？这些还真有待于后面验证，再回来解答这个问题  

对于今天，则开始go的旅程

第一步，mac安装上go环境
百度之，两种方式，一种去官网下载安装包，浏览器加载半天无响应，于是选择了第二种，brew install go方式安装
由于长时间没用brew，需要更新，也不快。。  
扛不住了，电脑更新着，我先睡了。。  

-29号  

第二步，用go和gin跑起来一个helloworld  
上次的更新完成了，go也安装完成，命令行执行 go version ``go version go1.15.6 darwin/amd64``  
之前了解到了工作中用到的夜莺是用gin这个web框架开发的，我就开始gin的学习吧  
百度找到了两个链接，内容几乎一致  
第一步go get github.com/gin-gonic/gin  
get没响应，连接github超时，于是换代理  
``
$ go env -w GO111MODULE=on
$ go env -w GOPROXY=https://goproxy.cn,direct
``
之后正常get  
第二步写一个main主类，main.go，里面开启一个端口输出helloworld  
执行 ``go run main.go``  
报错 ``main.go:3:8: cannot find module providing package github.com/gin-gonic/gin: working directory is not part of a module``  
百度关键词 ``working directory is not part of a module``  
go mod init godemo  
再次执行 ``go run main.go``  
成功启动，看到helloworld  

-2021年1月3号  

开始尝试了解一下gin的api  
根据夜莺的ams源码，也尝试了解了一点http.server
我目前的理解是，http.server是一个http服务框架，gin是一个web框架，  
http.server可以用gin的对象作为handler来处理web请求  
目前是没有体会到用http.server的好处，推断肯定是可控性较强，有待以后体会  
接下来，我可以开始先直接用gin完成一个web接口的开发了  

-1月6号

疑问点：对go的模块管理还不能够完全理解和掌握
