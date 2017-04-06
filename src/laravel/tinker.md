# 使用 tinker 调试

Laravel artisan 的 tinker 是一个 REPL (read-eval-print-loop)，REPL 是指 交互式命令行界面，它可以让你输入一段代码去执行，并把执行结果直接打印到命令行界面里。

## 基本使用

打开 tinker
```
php artisan tinker
```
使用模型工厂来填充数据
```php
factory(App\User::class, 10)->create();

App\User::all();

App\User::count();
```

创建一个新用户
```php
$user = new App\User;
$user->name = "Wruce Bayne";
$user->email = "iambatman@savegotham.com";
$user->save();
```
删除一个用户，要删除 id 为 1 的用户：
```php
$user = App\User::find(1);
$user->delete();
```

## 查阅某个类/方法的注释文档
通过 tinker，你可以在 REPL 中查看某个 类/方法 的注释文档。但是文档内容取决于这个 类/方法 是否有一个文档注释块（DocBlocks）。
```
//查阅 dd 的注释文档
doc dd
```

## 查看源码
我们还可以直接在 REPL 中打印出某个 类/方法 的源代码
```
//查看 dd 的源码
show dd
```
[参考链接](http://laravelacademy.org/post/4935.html)