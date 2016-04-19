# 搭建Git服务器以及管理多个ssh密钥

* 安装git（mac用brew，linux用yum或apt-get）
* 服务器端创建git仓库

```
mkdir project.git
git init --bare project.git
sudo chmod -R 0777 project.git #递归修改权限
cd project.git
sudo vim .git/config #在后面追加下面两行
```

> [receive]
>       denyCurrentBranch = ignore

* 在用户目录下的`.ssh/authorized_keys`的文件中追加收集用户的id_rsa.pub信息
* 客户端生成id_rsa密钥对，多个密钥需要追加

```
ssh-keygen -t rsa -C 'second@mail.com' #然后输入路径和文件名~/.ssh/id_rsa
#如果输入的文件非默认的id_rsa文件，那么需要添加下面一句
#然后把相应的.pub文件中内容追加到.ssh/authorized_keys文件中
ssh-add ～/.ssh/id_rsa_second
```

* 客户端克隆远程项目

```
git clone user@192.168.x.xx:/home/user/project.git
```

* 设置git钩子，在推送文件后将文件移动到web目录

```
cd /home/user/project.git/hooks
cat > post-receive <<EOF
>#!/bin/bash
>git --work-tree=/home/website/wwwroot checkout -f 
>EOF
chmod +x post-receive
```

###参考网址
* [廖雪峰Git](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/00137583770360579bc4b458f044ce7afed3df579123eca000)
* [Mac os搭建Git服务器](http://blog.csdn.net/liuyuyefz/article/details/17025905)
* [自动同步站点目录](http://my.oschina.net/cxz001/blog/194196)
* [使用多个SSH密钥对](http://blog.csdn.net/feng88724/article/details/9386909)
