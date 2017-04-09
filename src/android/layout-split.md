# 分类整理 layout 布局文件

一直以来项目中布局文件都是放在 `layout` 一个文件中，随着项目越做越大，布局文件也变得非常多，很有必要进行分类整理。
## 解决方案
利用Gradle脚本可以指定Resource文件目录的特性，我们可以手动修改layout文件的路径。
```
sourceSets {
        main {
            res.srcDirs = [
                    'src/main/res/layouts/home',
                    'src/main/res/layouts/main',
                    'src/main/res'
            ]
        }
    }
```

![](http://onru0wbs0.bkt.clouddn.com/android/2017-04-09-16-25-40.jpg)


![](http://onru0wbs0.bkt.clouddn.com/android/2017-04-09-16-27-51.jpg)

[参考链接1](http://www.jianshu.com/p/c2c8461999be)
[参考链接2](http://www.jianshu.com/p/fcc831e87b3d)
[参考链接3](http://blog.csdn.net/u011156012/article/details/50575117)
