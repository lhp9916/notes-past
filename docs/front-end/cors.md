# 跨域请求

### 一、JSONP

前端：
```javascript
$(document).ready(function(){
    $.ajax({
        type:"GET",
        url:"http://127.0.0.1:8000/api/test",
        dataType:"jsonp",
        jsonp:"callback",
        success:function(data){
            //to do
        }
    });
});
```

服务端：
```php
$jsonp = $_GET('callback');    
return $jsonp . "(" . $json_data . ")";
```
JSONP只能用于GET方法。

### 二、CORS

CORS 是一个W3C标准，全称是"跨域资源共享"（Cross-origin resource sharing）。[参考阮一峰老师博客](http://www.ruanyifeng.com/blog/2016/04/cors.html)。
只需要在服务端添加这两行即可，前台无需任何变化。
```php
header("Access-Control-Allow-Origin: *");
header("Access-Control-Allow-Methods: GET, POST");
```
