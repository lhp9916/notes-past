## 文件上传

配置文件 config/filesystems.php

```php
'disks' => [

        'local' => [
            'driver' => 'local',
            'root' => storage_path('app'),
        ],

        'public' => [
            'driver' => 'local',
            'root' => storage_path('app/public'),
            'url' => env('APP_URL') . '/storage',
            'visibility' => 'public',
        ],
        //自定义存储目录
        'upload' => [
            'driver' => 'local',
            'root' => storage_path('app/upload'),
        ],
    ],
```

示例：
```php
public function upload(Request $request)
    {
        $file = $request->file('source');

        //文件是否上传成功
        if ($file->isValid()) {
            $originalName = $file->getClientOriginalName();//原文件名
            $ext = $file->getClientOriginalExtension();//扩展名
            $type = $file->getMimeType();//MimeType
            $realPath = $file->getRealPath();//临时决定路径
            $fileName = date('Y-m-d-H-i-s') . '-' . uniqid() . $ext;

            //上传到指定的磁盘下面
            //use Illuminate\Support\Facades\Storage;
            $bool = Storage::disk('upload')->put($fileName, file_get_contents($realPath));
            if ($bool) {
                echo '上传成功';
            }
        }
    }
```
