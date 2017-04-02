# Laravel 的事件系统

1. 在 `App\Providers\EventServiceProvider` 添加
```php
protected $listen = [
        'App\Events\BlogView' => [
            'App\Listeners\BlogViewListener',
        ],
    ];
```

2. 执行如下命令
```
php artisan event:generate
```
在 `App\Events` 和 `App\Listeners` 会生成对应的文件

3. 事件 BlogView
```php
    public $post_id;

    public function __construct($post_id)
    {
        $this->post_id = $post_id;
    }
```
4. 监听器 BlogViewListener
```php
    public function handle(BlogView $event)
    {
        $post_id = $event->post_id;
        logger('文章-'.$post_id . "被查看");
        //可以统计文章阅读次数(把viewCount+1)，这里简便起见用的 logger
    }
```
5. 触发事件
```php
class BlogController extends Controller
{
    public function index($id)
    {
        //调用触发器
        event(new BlogView($id));
    }
}
```
