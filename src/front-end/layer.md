# layer——优雅的web弹层组件

在web应用交互体验中，弹出框是一个十分重要功能，可是浏览器原生的alert却是这般模样，

![](http://oncsg1snd.bkt.clouddn.com/images/20160928/alert.jpg)

这模样在现代化的web页面中实在不忍直视，今天给大家推荐一个优雅的web弹层的组件——layer。先一睹为快

![墨绿风格](http://oncsg1snd.bkt.clouddn.com/images/20160928/molv.jpg)

我简单介绍下用法和我的封装 `dialog.js`
```
var dialog = {
    //错误弹出层
    error: function (message) {
        layer.open({
            content: message,
            icon: 2,
            title: '错误提示',
        });
    },

    //成功弹出层
    success: function (message, url) {
        layer.open({
            content: message,
            icon: 1,
            yes: function () {
                location.href = url;
            }
        });
    },

    //确认弹出框
    confirm: function (message, url) {
        layer.open({
            content: message,
            icon: 3,
            btn: ['是', '否'],
            yes: function () {
                location.href = url;
            },
        });
    },

    //无需跳转到指定页面的确认弹出框
    toConfirm: function (message) {
        layer.open({
            content: message,
            icon: 3,
            btn: ['确定'],
        });
    },
}
```
具体用法，先引入js文件，（注意，layer依赖jquery）
```
<script type="text/javascript" src="js/jquery-3.1.1.js"></script>
<script type="text/javascript" src="js/layer/layer.js"></script>
<script type="text/javascript" src="js/dialog.js"></script>
```

接着在js代码中调用，
```javascript
dialog.error("登录失败！");
dialog.toConfirm("确定删除？");
```
![](http://oncsg1snd.bkt.clouddn.com/images/20160928/error.jpg)
![](http://oncsg1snd.bkt.clouddn.com/images/20160928/confirm.jpg)

详细的介绍和文档参见 [官网](http://layer.layui.com/)，layer——希望对你有帮助。