---
title: vuetify
date: 2019-11-12 15:44:04
tags:
---

## vuetify 使用方法

### Vue 引入 vuetify 框架

#### 命令行安装

1. `npm install vuetify --save`

<!-- more -->

#### 在 main.js 中修改

```js
import Vuetify from "vuetify";
import "vuetify/dist/vuetify.min.css";
Vue.use(Vuetify);
new Vue({
  vuetify: new Vuetify(),
  el: "#app",
  components: { App },
  template: "<App/>"
});
```

#### 引入对应 icon 的 mdi

1. `npm install @mdi/font D`

#### 在 main.js 中修改

```js
import "@mdi/font/css/materialdesignicons.css";
```

#### 方法二：(请注意，这不是官方的 Google 存储库，可能无法接收更新)

`npm install material-design-icons-iconfont -D`

- 在 main.js 中引入 `import 'material-design-icons-iconfont/dist/material-design-icons.css'`

#### vuetify 使用时遇到的坑默认颜色显示不了

- 解决方法:在 App.vue 中：加上 v-app 就正常显示

```js
<v-app>
  <router-view />
</v-app>
```
