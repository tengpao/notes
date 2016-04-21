# $_SERVER

```
$_SERVER['SCRPT_FILENAME'] == $_SERVER['DOCUMENT_ROOT'].$_SERVER['SCRIPT_NAME']
//与【__FILE__】不同的是，如果代码在包含文件中，__FILE__返回的是包含文件的路径
$_SERVER['PATH_INFO']   //返回请求地址文件名后面？前面的内容index.php/a-b-c/sldfk.php?f=1 返回/a-b-c/sldfk.php?f=1
$_SERVER['QUERY_STRING']   //请求index.php?id=1&age=20返回id=1&age=20字符串    快捷用法
$_SERVER['HTTP_REFERER']   //连接到当前页面的前一个地址

$_SERVER['DOCUMENT_ROOT']// 当前运行脚本所在的文档根目录
$_SERVER['REQUEST_URI']  // 请求的地址不含域名部分 包括第一个'/'
$_SERVER['PHP_SELF']     // index.php/会连同'/'一起返回/index.php/，其他都基本相同， 在php的cgi模式下与SCRIPT_NAME的区别：http://www.jb51.net/article/19883.htm
【$_SERVER['HTTP_HOST']】   $_SERVER['SERVER_NAME']   //获取域名通常前一个更可靠 http://it.oyksoft.com/post/3158/    http://mimiz.cn/index.php/php/php-http_host-server_name-difference/

【HTTP请求相关信息】
$_SERVER['REQUEST_METHOD']//访问页面时的请求方法
$_SERVER['SERVER_PROTOCOL'] //请求页面时通信协议的名称和版本
$_SERVER['HTTP_USER_AGENT'] //当前请求的 User_Agent: 头部的内容。
$_SERVER['HTTP_ACCEPT'] //当前请求的 Accept: 头部的内容。
$_SERVER['HTTP_ACCEPT_CHARSET'] //当前请求的 Accept-Charset: 头部的内容。
$_SERVER['HTTP_ACCEPT_ENCODING'] //当前请求的 Accept-Encoding: 头部的内容
$_SERVER['HTTP_CONNECTION'] //当前请求的 Connection: 头部的内容。例如：“Keep-Alive”。

【不常用的】
$_SERVER[SERVER_ADDR] //服务器ip地址
$_SERVER[REMOTE_ADDR] //客户端ip地址
$_SERVER['HTTPS']//如果通过https访问,则被设为一个非空的值(on)，否则返回off
$_SERVER['REMOTE_PORT'] //端口。
$_SERVER['SERVER_PORT'] #服务器所使用的端口
$_SERVER['argv'] //传递给该脚本的参数。
$_SERVER['argc'] //传递给程序的命令行参数的个数。
$_SERVER['PATH_TRANSLATED'] #当前脚本所在文件系统（不是文档根目录）的基本路径。
```

PHP_SELF: 当前所执行的脚本的文件名，这个值是相对于根目录来说。

如果请求http://example.com/test/test.php?k=v，则PHP_SELF的值为
/test/test.php。

SCRIPT_NAME： 当前执行的脚本的路径。

如果请求http://example.com/test/test.php?k=v，则SCRIPT_NAME的值
为/test/test.php。这个变量是在CGI/1.1中定义的。

SCRIPT_FILENAME： 当前执行的脚本的绝对路径。

如果请求http://example.com/test/test.php?k=v，则SCRIPT_FILENAME的值
为/var/www/test/test.php。

注意：如果一个脚本以相对路径，CLI方式来执行，例如../test/test.php，那么
$_SERVER['SCRIPT_FILENAME']的值为相对路径，即../test/test.php。

PATH_INFO：客户端提供的路径信息，即在实际执行脚本后面尾随的内容，但是会去掉Query String。

如果请求http://example.com/test/test.php/a/b?k=v，则PATH_INFO的值为/a/b。

CGI1.1标准中如下描述："The PATH_INFO string is the trailing part of thecomponent of the script URI that follows the SCRIPT_NAME part of the path."

REQUEST_URI：包含HTTP协议中定义的URI内容。

如果请求http://example.com/test/test.php?k=v，则REQUEST_URI
为/test/test.php?k=v

区别
PHP_SELF VS SCRIPT_NAME：

PHP_SELF和SCRIPT_NAME的值在大部分情况下都是一样的，但是访问
http://example.com/test/test.php/a/b?k=v这类URL时候，PHP_SELF
为/test/test.php/a/b，SCRIPT_NAME为/test/test.php，可以看出PHP_SELF
比SCRIPT_NAME多了PATH_INFO的内容。

REQUEST_URI VS SCRIPT_NAME：

在访问http://example.com/test/test.php?k=v后，REQUEST_URI
为/test/test.php?k=v，SCRIPT_NAME为/test/test.php，可以看出REQUEST_URI
比SCRIPT_NAME多了Query String。

如果http://example.com/test/test.php在服务器端做了rewrite：

  rewrite /test/test.php /test/test2.php;
那么REQUEST_URI为/test/test.php，SCRIPT_NAME为/test/test2.php。