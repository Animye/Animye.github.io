---
title: ionic
date: 2019-07-22 17:32:10
tags:
---

### 安装

## 使用的是 ionic1

1. npm install -g cordova
2. npm install -g ionic
3. ionic start myApp tabs --type=ionic1
4. 在项目根目录，终端输入 ionic serve,可以在浏览器中打开

<!-- more -->

## ionic 页面跳转

- ionic 常用的跳转一共有两种类型，

- 一种是通过 state 的名字
  --'tab.chat-detail'来跳转；
- 另一种则是通过 url--'/chats/:chatId‘来跳转。
- 先说第一种，通过 state 名字--'tab.chat-detail'跳转。
  (1)在 angularjs 里，使用：\$state.go(''tab.chat-detail'),
  (2)如果是 a 标签跳转，则使用：ui-sref=“tab.chat-detail”。
- 第二种跳转，通过 url---'/chats/:chatId‘来跳转。
  (1)在 angularjs 里，使用：\$location.path('/chats/1'),
  (2)如果是 a 标签跳转，则使用：ng-href=“/chats/1”。或 href=“/chats/1”

## 打包 ionic 项目

### 配置环境变量

```js
1. 安装 android studio
   [参考链接](https://developer.android.google.cn/studio)


2. 安装 JDK 配置 JAVA 环境
   [参考链接](https://www.oracle.com/technetwork/java/javase/downloads/index.html)
   **java 必须下载 1.8 版本**


// 命令行操作
 cd ~
// 新建并打开touch .bash_profile
open .bash_profile
// 复制到文件中，保存并关闭
// 注意：路径都是一样的，只需要修改版本号就可以export export JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk1.8.0_201.jdk/Contents/HomePATH=$JAVA_HOME/bin:$PATH:.CLASSPATH=$JAVA_HOME/lib/tools.jar:$JAVA_HOME/lib/dt.jar:.
export JAVA_HOME
export PATH
export CLASSPATH
// 更新source .bash_profile// 检测java -version


3. 安装 Android SDK Tools

[参考链接](https://www.cnblogs.com/jiangtengteng/p/6680654.html)

// 新建并打开touch .bash_profile (其实可以省略这个 因为都是和上面同一个文件里面 添加)
open .bash_profile
// 复制到文件中，保存并关闭
// 路径只需把文件拖入命令行中就会显示绝对路径
export ANDROID_HOME=/Users/xxxx/Downloads/android-sdk-macosx
export PATH=${PATH}:${ANDROID_HOME}/tools
export PATH=${PATH}:${ANDROID_HOME}/platform-tools
// 更新source .bash_profile
// 检测，控制台 输入 adb   出现command not found 就是错了


4. 安装 grddle
   [参考链接](http://services.gradle.org/distributions/)

// 命令行操作cd ~
//open .bash_profile 
// 路径要替换为你自己的,还有版本也要替换好
GRADLE_HOME=/Users/xxxx/opt/gradle-5.3;
export GRADLE_HOME
export PATH=$PATH:$GRADLE_HOME/bin
// 更新source .bash_profile
// 检测gradle -version

```

### 打包 android

1. ionic cordova platform remove android 移除安卓
2. ionic cordova platform add android 添加安卓
3. ionic cordova build android => debug 调试版打包(会在 xxx\platforms\android\build\outputs\apk 下生成 android-debug.apk 这种命令生成的 apk 是用于调试的。)
4. ionic cordova build android --release => release 发布版打包
5. ionic cordova run android => 把本地打的 debug 包 apk 安装在真机上
6. adb install xxx\platforms\android\build\outputs\apk\xxx.apk => 安装命令安装
   [参考链接](https://my.oschina.net/u/2949632/blog/1186414)

### 打包 ios

1. ionic cordova platform add ios（第一次）
2. ionic cordova platform rm ios
3. ionic cordova build ios --prod
4. ionic cordova plugin rm cordova-plugin-camera//移除插件
5. ionic cordova plugin add cordova-plugin-camera//添加插件

```js
创建ios平台文件
ionic cordova platform rm ios
ionic cordova platform add ios
ionic cordova resources ios//正常执行完上面两句，资源文件都已经被更新，如果没有更新则执行本行命令
ionic cordova build ios
```

StatusBar.styleDefault 状态栏默认样式，也就是电池信号黑色；
StatusBar.styleLightContent 状态栏内容浅色，貌似就是白色，适合深色背景；
StatusBar.styleBlackTranslucent 状态栏黑色半透明，我测了下，跟上面一样的效果，电池时间都是白色的，适合深色背景；
StatusBar.styleBlackOpaque 状态栏黑色不透明。我测了下，还是白色的，跟上面一样，适合深色背景；
StatusBar.hide 状态栏隐藏；
StatusBar.show 状态栏显示；

### 跨域问题

[参考文档](https://www.jianshu.com/p/ad27b8dcd098)

- 修改 ionic.config.json(旧版本 Ionic CLI 是 ionic.project)：

```js
{
  "name": "proxy-example",
  "app_id": "",
  "proxies": [
    {
      "path": "/api",
      "proxyUrl": "http://cors.api.com/api"
    }
  ]
}


```

### mac path 设置

```js
JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk1.8.0_211.jdk/Contents/Home
PATH=$JAVA_HOME/bin:$PATH:.
CLASSPATH=$JAVA_HOME/lib/tools.jar:$JAVA_HOME/lib/dt.jar:.
export JAVA_HOME
export PATH
export CLASSPATH




export ANDROID_HOME=/Users/mac/Library/Android/sdk
export PATH=${PATH}:${ANDROID_HOME}/tools
export PATH=${PATH}:${ANDROID_HOME}/platform-tools

export ANT_HOME=/Applications/apache-ant-1.10.6
export PATH=$ANT_HOME/bin:$PATH



GRADLE_HOME=/Users/mac/gradle-4.1
export GRADLE_HOME
export PATH=$PATH:$GRADLE_HOME/bin


export PATH=${PATH}:/usr/local/mysql-8.0.16-macos10.14-x86_64/bin:$PATH


export PUB_HOSTED_URL=https://pub.flutter-io.cn
export FLUTTER_STORAGE_BASE_URL=https://storage.flutter-io.cn
export PATH=/Users/mac/flutter-1.7.8/flutter/bin:$PATH
```
