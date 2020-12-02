# git回滚某一次commit

tags:[git]

场景：由于某些原因想撤消掉某一次commit的改动，恰好这次的改动与前后的commit文件互不冲突，

于是根据自己的理解+百度+实操

* 1，查看历史记录，```git log -n``` （n是想要看最近几次，不确定可以多尝试几次）找到最近的几次提交，最好是找到要回滚的那一次提交的前一两次，人工确保是要操作的内容
* 2，打patch，```git format-patch -n```，会打出n个patch，每个patch对应一个commit
* 3，回退，```git reset –hard commit-id```，回退到要删除的commit之前一次commit-id
* 4，合并patch，可以把想要删掉的那一次的commit对应的patch删除掉 然后合并其它 ```git am *.patch```，也可直接按顺序合并每一次commit对应的patch
* 5，reset到master，```git reset 最新一次commitID```，这里没有尝试git reset master，参考的链接中没有这一步以及后面，所以同事在操作到这里 再一pull之后又全都回到最新代码了。
* 6，commit，把改动提交，相当于将刚才的操作作为一次修改，commit掉
* 7，push，到这一步之前，你所做的所有操作均可以恢复，所以不要怕操作错，大胆尝试，push之前可以确认好了再push

参考：https://blog.csdn.net/molaifeng/article/details/52671810

通过这次解决问题，对git reset的理解深刻了一层（以为理解了，想要写出来的时候，发现还是写不出来。。。）

git reset

git reset --hard

我用到的git reset三个使用场景
* 1，重新commit
* 2，本次中的第3步
* 3，本次中的第5步

应该是可以总结一下的，这里暂时放弃

下次总结的时候可参考如下url

https://www.jianshu.com/p/c2ec5f06cf1a