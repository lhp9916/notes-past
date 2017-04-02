# 打标签

#### 列出已有的标签
```
git tag
```
#### 查看相应标签的版本信息
```
git show v1.1
```
#### 新建标签
```
git tag -a v1.1 -m 'my version 1.1'
```
#### 分享标签
默认情况下，git push 并不会把标签传送到远端服务器上，只有通过显式命令才能分享标签到远端仓库。其命令格式如同推送分支，运行 git push origin [tagname] 即可
```
git push origin v1.1
```
如果要一次推送所有本地新增的标签上去，可以使用 --tags 选项
```
git push origin --tags
```
[参考链接](https://git-scm.com/book/zh/v1/Git-%E5%9F%BA%E7%A1%80-%E6%89%93%E6%A0%87%E7%AD%BE)
