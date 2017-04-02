# NPM

由于 Node 的官方模块仓库网速太慢，模块仓库需要切换到阿里的源。

```
npm config set registry https://registry.npm.taobao.org/

npm config get registry

```
安装 cnpm
```
npm install -g cnpm --registry=https://registry.npm.taobao.org
```
```
// 显示全局安装的包，屏蔽错误信息
npm list -g --depth=0  2>/dev/null
```
