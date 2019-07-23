---
title: cordova-vue
date: 2019-07-23 09:23:42
tags:
---

## 使用原因

用 vue 配合 cordova 可以实现手机端打包，不用更换框架。可以使用 Cordova 里面的插件来调用手机的原生功能

 <!-- more -->

```js
本教程环境版本介绍：



JDK： JDK_1.8.0_64bit   （根目录有提供）

nodejs: v8.11.2  （建议用最新的稳定版本）

cordova: 8.0.0

android studio：目前最新版本3.1.3  （建议升级为最新）  下载地址：http://www.android-studio.org/





ionic3


ionic3=cordova+angular+ionicUI      （Ionic UI组件+ Javascript API+Ionic Native）


优点：它提供了漂亮的UI组件库、强大的JS APi以及基于调用原生的的Native APi,可以让我们快速开发跨平台的混合APP以及移动web页面。（推荐*）


缺点：angular   react   vue开发的移动端应用要打包成app的时候得重新再学习ionic




vue开发的项目直接可以打包成app，并且可以让vue调用原生的功能（拍照）





	阿里weex框架：不建议大家用weex  （不能直接把vue项目打包成app、学习weex成本高、weex不是特别成熟）


	cordova+vue：  （cordova非常成熟、插件也非常多、扩展性也强）  10年的历史



reactNative：基于react



cordova介绍：

cordova: 可以把html css js写的代码打包成app，还可以让js调用原生的api


ionic、cordova+vue、cordova+react 、cordova+angular




用cordova开发android 应用

1. 安装jdk 、配置jdk

2. 安装android studio

3. 安装nodejs


4. 安装cordova    npm  install  -g  cordova   /   cnpm install -g cordova


npm install -g cordova --registry=https://registry.npm.taobao.org




5. 创建项目      cordova create 项目名称

cordova create 项目名  com.公司名.项目名  类名 （建议）

cordova create cordovademo02  com.itying.cordova  Cordovademo


创建项目的时候注意包名称：发布上线打包的时候用到包名称，注意

修改应用包名名称参考：http://www.ionic.wang/article-index-id-91.html


修改应用包名名称：

  1. 修改config.xml里面的包名称

  2. 修改完成以后重新执行cordova platform add android




6. cd 到项目里面    cd cordovademo02

7. 把android的平台添加到项目里面     cordova platform add android


8. 把项目导入到 android studio 进行运行调试  （或者运行   cordova  run  android）   注意可能遇到的问题参考（安装遇到问题图文解决方案文件夹）



9. 运行项目 ：注意

1、android手机要连上电脑，并且 android手机必须开启调试模式（如何开启:百度搜 xxx手机开启调试模式）

2、android studio必须得安装手机对应的sdk

3、关闭360手机助手、xxx手机助手




10. 修改项目:  运行cordova prepare






用cordova开发ios 应用环境搭建：


1、安装nodejs 安装xcode


2、安装cordova    npm  install  -g  cordova   /   cnpm install -g cordova


 npm install -g cordova --registry=https://registry.npm.taobao.org


3.创建项目      cordova create 项目名称

cordova create 项目名  com.公司名.项目名  类名 （建议）

cordova create cordovademo02  com.itying.cordova  Cordovademo




4.cd  cordovademo02



5、把ios的平台添加到项目里面  cordova platform add ios


6、用xcode打开项目运行
参考ionic3教程  Mac电脑安装 ionic3.x cordova 以及创建证书、打包ios app、上传应用市场 app教程（5小讲）：



cordova安装插件：

如果我们要在自己的html里面调用手机原生的功能（拍照、扫描二维码、获取地理位置...）,借助cordova的插件





cordova官网：https://cordova.apache.org/



如何使用插件：

1、安装插件     cordova plugin  add  插件名称


2、复制文档使用





查看已经安装的插件：



cordova plugin list



卸载插件：


cordova plugin rm  cordova-plugin-network-information

1、设备插件的使用

https://cordova.apache.org/docs/en/latest/reference/cordova-plugin-device/index.html


1、安装cordova plugin add cordova-plugin-device

2、看文档使用。






2、使用网络相关的插件：

https://cordova.apache.org/docs/en/latest/reference/cordova-plugin-network-information/index.html

1、安装cordova plugin add cordova-plugin-network-information

2、看文档使用




3、定位插件：
https://cordova.apache.org/docs/en/latest/reference/cordova-plugin-geolocation/index.html


1、安装cordova plugin add cordova-plugin-geolocation
2、看文档使用
注意改代码以后要运行：cordova prepare
注意：要引入cordova.js

注意：项目里面不要有中文文件夹、不要有zip包 、不要有中文文件


4、拍照插件

https://cordova.apache.org/docs/en/latest/reference/cordova-plugin-camera/index.html



注意：ios拍照完成以后调用  navigator.camera.cleanup(onSuccess, onFail);




5、文件上传 或者下载



1、文件插件: https://cordova.apache.org/docs/en/latest/reference/cordova-plugin-file/index.html


2、文件传输插件：https://www.npmjs.com/package/cordova-plugin-file-transfer




cordova打包vue项目：


cordova: 可以把html css js写的代码打包成app，还可以让js调用原生的api



cordova+vue、cordova+react 、cordova+angular 、 cordova+jquery





创建vue项目的时候有两种方式：


vue init webpack 项目名称


vue init webpack-simple  项目名称




正式发布vue的项目：（把vue项目打包成浏览器能解析的代码）


npm run build   （把vue打包成浏览器能解析的代码）





把vue项目用cordova打包成app：


1. npm run build        （注意：图片 目录的路径）

2、把vue打包后的静态资源复制到cordova项目里面

3、运行 cordova prepare





注意：

vue init webpack-simple  项目名称

修改：webpack.config.js里面  publicPath


把publicPath: '/dist/'    改为  publicPath: 'dist/'


修改index里面引入dist的路径  去掉前面的  / (重要)




vue init webpack  项目名称

修改：config/index.js  把 assetsPublicPath: '/',		  修改成   assetsPublicPath: './',










扩展：http-server  轻量级的http服务器

npm install -g http-server


用法：cd到目录运行 http-server


看教程


https://pan.baidu.com/s/1VfqhpjohCIK-fTG-NqqllA


```
