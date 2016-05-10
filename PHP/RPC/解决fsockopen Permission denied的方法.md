


各种坑，直接用php运行文件没有问题，在浏览器中运行一直提示fsockopen Permission denied，解决办法是运行以下命令：
```
$ sudo setsebool -P httpd_can_network_connect 1
```

在第一个帖子中找到第二个帖子，找到了解决答案
http://bbs.csdn.net/topics/390909178
http://blog.csdn.net/pennyliang/article/details/7342042