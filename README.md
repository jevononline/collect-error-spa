## trash-can-broom

🧹生产环境前端错误收集与定位平台

在生产环境部署的js的代码，通常都是压缩混淆过的，线上出现了错误debug非常困难。source-map文件虽然可以将压缩混淆的过后的文件，进行还原但是如果source-map文件部署到线上，有泄漏源码的风险。


![977470e2-2f5b-11e7-8551-8099a4038f6f.jpg](https://i.loli.net/2020/05/22/PZdjSvaYfwC4M1W.jpg)

这个项目的思路就是，将生产环境的js文件所对应的source-map文件单独发布部署到内网环境，通过收集生产环境所产生的错误信息（错误类型，错误的行数，错误的列数），然后结合内网环境的source-map文件，还原并定位错误的具体位置。

##

启动错误平台（模拟生产环境产生的错误）

```shell

cd production

npm install --global http-server

http-server dist

```

启动错误收集定位的后端服务

```shell
cd error-server

npm run serve
```


错误信息展示平台，启动错误收集定位的后台页面

```shell

cd error-show-platform

npm run serve