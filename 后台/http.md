## options请求方法

这个请求方法在**跨域请求中出现**，他的作用是先发一个options方法确认服务器是否可以接受跨域请求，如果跨域跨域请求的话，在发送原本的请求。所以在后端如果有请求会被跨域请求的话需要使用下面的代码进行操作，否则可能导致收到正确请求，也就收不到客户端发送来的内容了。（客户端发的内容在options请求确认成功后在发一个请求中）

```php
// 检测是否是options请求方法
if ($this->request->isOptions()){
    //设置请求头，允许跨域访问
    header('Access-Control-Allow-Origin:*');
    header('Access-Control-Allow-Methods: GET, POST, PATCH, PUT, DELETE, OPTIONS');
    header('Access-Control-Allow-Headers: Origin, Content-Type, X-Auth-Token');
    return ''; //向客户端随便返回什么数据，关键是上面的响应头告诉客户端，服务器允许跨域访问。
}
……//正常请求方法
```

