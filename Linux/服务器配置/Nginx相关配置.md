# Nginx相关配置

#### 安装
> 安装nginx需要指定zlib的目录,而这个目录是zlib的源码目录,使用curl下载zlib源码包,`./configure --with-zlib=/usr/local/src/zlib-1...`然后方可`make && make install`

#### 配置
```
# 将php请求转发到fastcgi,include fastcgi_params不管用,需要改成下面一行
location ~ \.php$ {
    root           /home/tommie/www;
    fastcgi_pass   127.0.0.1:9000;
    fastcgi_index  index.php;
    fastcgi_param  SCRIPT_FILENAME  /scripts$fastcgi_script_name;
    #include        fastcgi_params;
    include        fastcgi.conf;
}
```