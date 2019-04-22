---
title: NUXT vue 的服务器端渲染(ssr)
date: 2019-02-26 10:49:51
tags:
  - nuxt
  - vue
---

&#160; &#160; &#160; &#160;**只要是刷新以及通过地址栏访问页面，就会在服务器端生成一个页面返回给浏览器。**

# 安装

1. 确保安装了 npm 并且 版本在 5.2.0 以上，使用 npx create-nuxt-app <项目名> 创建 nuxt 项目
   <!-- more -->
2. 创建的过程中会有很多选项提供

- Project name nuxt-hello 回车
- Project description My outstanding Nuxt.js - - project 回车
- Use a custom server framework none
- Choose features to install Axios
- Use a custom UI framework none
- Use a custom test framework none
- Choose rendering mode Universal
- Author name (Sunny-zz) 回车
- Choose a package manager npm

3. 分析目录结构

- assets 用于组织未编译的静态资源如 LESS、SASS 或 - - JavaScript
- static 一般放一些图标，图片
- components 子组件
- layouts 布局组件 头 主体 底
- middleware 中间件
- pages 路由
- plugins 插件
- store vuex 状态树
- nuxt.config.js nuxt 环境配置文件

## 内容

### fetch 函数 替代 created

- fetch 函数 第一个参数是 `context`,只在页面组件中（即在 pages 文件夹下的组件）
- `context` 对象下都有哪些属性
  [参考地址](https://zh.nuxtjs.org/api/#%E4%B8%8A%E4%B8%8B%E6%96%87%E5%AF%B9%E8%B1%A1)
