## linux 解压缩命令

#### .tar
```
解包： tar -xvf filename.tar

打包： tar -cvf filename.tar dirname
-x 解打包
-c 打包
-v 显示过程
-f 指定文件名
(注：tar是打包，不是压缩)
```
#### .tar.gz
```
解压： tar -zxvf filename.tar.gz

压缩： tar -zcvf filename.tar.gz dirname
```
#### .tar.bz2
```
解压： tar -jxvf filename.tar.bz2

压缩： tar -jcvf filename.tar.bz2 dirname
```
### .zip
```
解压： unzip filename.zip

压缩： zip filename.zip filename
      zip -r filename.zip dirname
```
