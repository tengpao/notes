# 安装mangodb

```
cd /usr/local/src
wget https://fastdl.mongodb.org/linux/mongodb-linux-x86_64-amazon-3.2.5.tgz
#https://fastdl.mongodb.org/linux/mongodb-linux-x86_64-amazon-3.2.5.tgz?_ga=1.172563108.661626580.1461164249
tar -zxvf mongo...
mv mongo... /usr/local/mongodb
mkdir -p /home/m17 /home/mlog
cd /usr/local/mongodb
./bin/mongod --dbpath /home/m17/ --logpath /home/mlog/m17.log --fork --port 27017



```

* 查看mongo启动状态
```
ps -aux | grep 'mongo'
```