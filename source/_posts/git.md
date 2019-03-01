---
title: shell 命令 和 git 基础操作
date: 2019-02-19 10:21:31
tags:
  - shell
  - git
---

<img src="http://i0.hdslb.com/bfs/archive/0fb66998d81910d1bcabe2c649cd083511524dfa.jpg" width="300" hegiht="100"  />

## 基本 shell 命令

- cd 命令 目录跳转 ./ 当前文件夹 ../上级
  - cd d: 跳转到 d 盘 cd ~ 跳转到用户主目录
- ls 命令 查看当前文件夹下的所有内容 参数 -a 也可以查看隐藏文件
  <!-- more -->
- pwd 查看当前所处位置
- mkdir a 在当前目录下创建一个 a 文件夹
- touch index.html 在当前目录下创建一个 index.html 文件必须带后缀名
- rm 文件名 删除当前目录下的文件 参数 -r 可以删除文件夹 -f 强制删除 多个参数可以 -rf
- rm -rf ./\* 删除当前目录下的所有文件以及文件夹
- ctrl + c 取消当前操作命令
- clear 命令
- cat 文件 查看当前目录下该文件的内容
- cp 拷贝命令 cp 文件 目录 将该文件拷贝到目录下 参数 -r 可以拷贝文件夹
  - cp 文件 名 拷贝后重命名
- mv 移动命令 mv 文件|文件夹 目录 将该文件或文件夹移动到目录下
  - mv 文件|文件夹 名 重命名

## git 操作

### 生成 ssh 秘钥，用于系统和 github 连接

- 在命令行中 执行 ssh-keygen
- 进入到用户主目录下 cd ~
- 再进入到 .ssh 文件夹下 cd .ssh
- 使用 cat 命令查看公钥 cat id_rsa.pub 复制里面的文本
- 打开 github 网站点击用户下面的 settings SSH and GPG keys
- 添加 ssh 即可

### git 操作之克隆网上仓库到本地 (http)

点击仓库下的绿色按钮 `clone or download` 选择 http 地址,打开命令行,跳转到某个目录(放项目的文件夹)下,执行 `git clone 地址` 命令 ---> 将网上的项目克隆到了本地,使用编辑器打开该项目进行编辑 修改 html 文件,我们想要将修改的内容让 git 记录,只有在 git 仓库内才能对该仓库进行操作

- 进入到仓库的文件夹下
- git add 修改的文件名(.代表所有修改的文件) ---> 将对仓库内文件的修改让远端 git 记录
- git commit -m'版本信息(此次修改的标题)' ---> 将此次修改做成一个 git 版本，方便 git 记录。

  **第一次使用 git 时候做版本会失败,因为 git 不知道你是谁，使用**

  `git config --global user.name "git用户名"`

  `git config --global user.email "git邮箱"`

  **告诉 git 你是谁。再次执行 git commit**

- git push 将我们的修改提交到远端

**假如配置个人信息失败 如何修改 再次执行上面的 配置语句 也可以去 用户主目录下 .gitconfig 文件**

**_*git 三部曲 git add . git commit -m'' git push*_**

### git 操作之本地建好的项目想存储到 git(远端没有仓库)

1. git 远端新建一个同名仓库 里面什么都不放(初始化的时候不要添加 `README.md` 文件)
2. 进入到本地的项目文件夹，打开终端，执行 `git init` 操作 (初始化本地文件夹为 git 仓库)
3. 执行 `git add .`
4. 执行 `git commit -m'版本留言'`
5. 执行 `git push` 会报错，没有远端目标
6. 执行 `git remote add origin git@github.com:Sunny-zz/test.git` 设置远端目标
7. 执行 `git push -u origin master` 讲本地仓库推送到设置好的远端仓库
8. 以后想修改的话 直接执行 git 三步

### git 操作之 git pull

团队合作或者通过其他的方式导致网上的版本优先于本地的版本之后如何操作，当我们不知道远端有新版的时候执行了 git 三步之后 push 的时候会提示，更新被拒绝，因为远程仓库包含您本地尚不存在的提交。此时解决方案如下

- 执行 `git pull` 将远端的新版本拉取到本地，此时会出现两种情况

  1. 如果远端的新版本和你本地修改的版本是同一个文件的话会发生合并冲突，需要你自己到对应文件内处理冲突

     接下来就是用 git 三步提交

  2. 远端的修改和本地的修改不是同一个文件那么 `git pull` 的时候 git 会帮你自动合并，但是需要你添加一个合并的版本留言(有默认的留言信息)，直接执行 `ctrl + x` 退出即可，相当于 git 自动帮你这合并做成了版本并且提交了版本里留言，接下来直接使用 `git push` 推送即可。

     mac 上弹出 vim 编辑器使用 英文的 `shift z z` 即可保存退出

### git 操作相关命令

- `git log` 查看当前仓库的版本 版本非常多显示不全,使用回车看下面的 按 q 键退出
- `git status` 查看当前仓库的状态
- 任何命令 加上 `--help` 可以查看命令可以带那些参数

### git 操作之版本回退

- `git log --pretty=oneline` 查看版本信息 参数的意思是在一行显示
- 使用 `git reset --hard` 版本号前四位 实现本地版本回退
- 使用 `git push -f` 强制推送到远端
- 想要回到之前的版本 使用 `git reflog --all` 查看之前的所有版本修改 找到对应的版本号
- 使用 `git reset --hard` 版本号前四位 实现版本跳转
- 执行 `git push` 推送到远端

### git 操作之分之操作

#### 将其他仓库内的项目托管到 git 服务器

1. 新建分支 `git branch gh-pages` 分支名必须叫做 `gh-pages` 可以使用 `git branch` 查看本地有哪些分支并且处于哪个分支 可以加 -r 参数可查看远端分支，新建分支之后，新分支内的内容默认和主分支一样，但是之后单独对某个分之操作是不影响其他分支的
2. 切换到 新创建的分支 `gh-pages git checkout gh-pages` ,在该分支下修改 某个文件,并执行 git 三步，第一次将本地分支上传到远端的时候会失败并提示如何上传，使用 `git push --set-upstream origin gh-pages` 上传。 创建新的分支之后也可以直接使用该命令将新分支直接上传

   你的 `gh-pages` 分支下的 `index.html` 就可以使用 git 免费服务器访问了 网址如下

   `用户名.github.io/仓库名`

   不是访问 master 分支下的 index.html

3. 将 `gh-pages` 分之内做好的页面合并到主分支，切换到 master 分支，合并其他分支上的更新
   `git merge gh-pages` 合并的时候必须保证主分支上的内容没有修改或要提交的

#### 写好的项目如何托管到 git 服务器

1. 网上新建一个同名的空仓库
2. 将本地的项目文件夹初始化为 git 仓库
3. 执行 git 三步上传 由于是第一次上传需要添加远端地址并上传
4. 新建 `gh-pages` 分支 并切换到该分支上传到远端
   `git checkout -b gh-pages` 新建一个分支并切换过去
5. 项目就能访问了

#### 我想要更新我的项目 (master 分支上一般放项目的源码)

1. 进入到 master 分支进行更新，添加新功能并上传
2. 更新 gh-pages 分支，切换到 gh-pages 分支 使用 `git pull origin master` 拉取主分支上的更新 使用 `git push` 上传

#### 删除分支操作

首先得切换到主分支

- `git branch -d` 分支名 删除本地分支
- `git branch -d -r origin/分支名` 删除远端分支
- 删除分支之后 需使用 `git push origin :分支名` 提交到远端

## node 相关

### linux 系统下 将 node 添加到 linux 的环境变量

1. 找到 node 路径
   `/home/zzt/.nvm/versions/node/v9.2.0/bin`
2. 打开.bashrc 添加 `export PATH="\$PATH:/home/zzt/.nvm/versions/node/v9.2.0/bin"` 到最后一行保存
3. 重启命令行

## webpack 编译 es6 语法

- 将项目初始化为 npm 项目 使用 `npm init -y` 命令
- 在项目下安装 webpack 工具 `npm install webpack webpack-cli`
- 将项目下存储 js 文件的文件夹改名成 src
- 在项目的根目录下新建文件 webpack.config.js,将官网首页的代码复制粘贴
- 在 package.json 添加一条脚本命令 `build:"webpack"`
- 在命令行中该项目下执行 `npm run build`
- 在 index.html 引入打包好的 dist 下面的 bundle.js

**要确保打包的入口文件是 index.js,也就是说 src 下必须有 index.js**
