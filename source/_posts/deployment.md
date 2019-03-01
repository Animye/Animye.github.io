---
title: Project deployment
date: 2019-02-25 13:15:09
tags:
  - 项目部署
---

#### 项目部署到服务器

一、 `github`免费服务

- 将你的原代码上传到 git 仓库，在仓库内建立一个分支`gh-pages`，通过插件或手动将 dist 文件夹下的所有文件上传到该分支，访问 用户名.github.io/仓库名，即能看到自己的项目了
- 注意：package.json 文件下要写一个 homepage：该仓库地址
  <!-- more -->
  - 如何将 dist 下的文件 上传到 `gh-pages`
  1. 手动建立新分支
  2. 使用`gh-pages`包即插件 帮助我们自动上传

二、 `netlify`免费服务

- 只需要将源代码上传到 git 仓库，在 netlify 网站找到对应的仓库不需要添加 homepage，选择正确的文件及命令即可
