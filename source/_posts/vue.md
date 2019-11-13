---
title: vue
date: 2019-07-23 10:04:08
tags:
---

## vue 项目介绍

#### 组件

只要是后缀名为 .vue 的文件都称为组件，可以把组件理解成之前 html 内的某个 div，整个 vue 项目就是由很多小的组件组合的。
组件可以复用。组件的名称都是大写字母开头的，或者大驼峰方式 例如:HeaderTop

   <!-- more -->

组件内有三个标签

1. `tempate` (必须)：div 的结构
2. `script`
3. `style` ： 结构的样式

#### 安装环境

使用官方提供的脚手架 vue-cli ,版本是 2.x

- `npm install -g vue-cli`
- `vue init webpack my-project`
- 配置
  Project name :项目名称 ，如果不需要更改直接回车就可以了。注意：这里不能使用大写
  Project description:项目描述，默认为 A Vue.js project,直接回车，不用编写。
  Author：作者，如果你有配置 git 的作者，他会读取。
  Install vue-router? 是否安装 vue 的路由插件，我们这里需要安装，所以选择 y
  Use ESLint to lint your code? 是否用 ESLint 来限制你的代码错误和风格。我们这里不需要输入 n，如果你是大型团队开发，最好是进行配
  setup unit tests with Karma + Mocha? 是否需要安装单元测试工具 Karma+Mocha，我们这里不需要，所以输入 n。
  Setup e2e tests with Nightwatch?是否安装 e2e 来进行用户行为模拟测试，我们这里不需要，所以输入 n

使用官方提供的脚手架 vue-cli ,版本是 3.x

- 使用命名 `npm i -g @vue/cli` 全局安装一个 vue 命令
- 使用 `vue create projectName` 新建一个 vue 项目了

#### 针对 vue 命令创建出来的 vue 项目，改版成一个 hello world

对 src 内的文件进行处理

- 找到 app.vue ，删除 `template` 里面的所有内容，以 `<h1>hello world</h1>` 替代，删除 `style` 内的所有内容， 删除 `script` 内的部分内容只留下默认导出对象，以及对象下的 name 属性。
- 找到 components 文件夹直接删除
- 直接去浏览器查看

#### 写另外一个组件，引入到 App.vue 中

- 在 src 文件夹内新建一个文件夹叫 components ，里面新建一个 Button.vue
- 在 App.vue 中的 script 标签内的最上方使用默认导入导入你的 Button.vue，在默认导出的的对象内添加一个 components 属性，该属性的属性值是一个对象，对象内直接写上导入的组件名
- 在 App.vue 的 template 标签内直接写以组件名为标签名的标签即可，一般写成单闭合标签即可，就相当于使用了组件。

## Vue 的基础语法

#### 模板语法

vue 允许在 template 内写 js

- 在两个标签中间 使用{{js语法}} ，这个 js 语句必须有返回值
- 在开始标签内 需要使用指令 v-bind 如何使用 例子如下

  ```js
  <h1 v-bind:class='js语法' />
  // v-bind:  指令可以简写成   :
  ```

#### class 与 style 绑定

vue 组件处理样式的方案

###### class 的绑定

- 对象语法 例子: 加上了 active class 名
  ```js
  <div v-bind:class='{ active: true }' />
  ```
- 数组语法 例子: 加上了 active 以及 bg class 名
  ```js
  <div v-bind:class="[true ? 'active' : '', 'bg']" />
  ```
- 原始语法 例子:加上了 active
  ```js
  <h1 v-bind:class=" true ? 'active' : 'bg' " />
  ```

###### style 的绑定

- 对象语法 例子

  ```js
  <div v-bind:style="{ color: 'red', fontSize: '20px' }" />
  ```

- 数组语法 例子
  ```js
  <div v-bind:style='[styles, otherStyles]' />
  // styles 和 otherStyles 指的对象  {color: 'red'}
  ```

#### Vue 组件的 data(state)

只要页面发生改变就需要设置 data ，由 data 去控制页面的变化。

- 如何创建一个 data，在组件导出的对象下，添加一个属性 data，该属性的属性值为一个函数，该函数必须返回一个对象，对象内写的就是组件的数据。
- 创建好的 data ，在组件的 template 内可以直接使用
- 创建好的 data ，在其他地方使用的时候需要加 this.xxx
- 想要修改 data ，直接对属性进行重新赋值即可

#### Vue 组件的事件处理

使用 v-on 指令绑定事件 可以简写成@ 例子

```html
<button @click="funName">按钮</button>
```

事件函数(funName) 需要在组件默认导出的对象下添加一个 methods 属性,该属性的属性值是一个对象，该对象下的方法就可以被当做事件函数。在 template 内 methods 对象下的方法可以直接使用。
methods 的函数内只要使用了 this 那么这个函数就不能写成箭头函数，必须写成普通函数。

#### 条件渲染

页面中某个元素出现或者消失

1. none --- flex | block | inline-block | inline ,需要使用 v-show 指令 例子:

   ```html
   <div v-show="数据" class="box"></div>
   <!-- 如果 数据的值为 false 的话 div 消失，true 的话出现 -->
   ```

2. 元素在页面中 remove 或者 create ，需要使用指令 v-if ，一般搭配 v-else 一起使用 例子:

   ```html
   <div v-if="showBox1" class="box1">git 图</div>
   <div v-else class="box2"></div>
   ```

   注意 v-if 和 v-else 必须紧挨着，作为兄弟结构

#### 列表渲染

我们页面展示的内容(列表内容),一般都是获取后台数据，将后台数据处理生生页面中的结构。后台的数据一般都是 array。
v-for 经常搭配 v-if 使用,等待后台数据的过程此时展示 gif 图，
在 vue 中实现列表渲染直接使用 v-for 指令 例子
template

```html
<div class="goods" v-for="(cart,index) in carts" :key="cart.id">
  <span>名称: {{cart.goodsName}}</span>
  <span>索引值: {{index}}</span>
</div>
```

v-for 生成的标签必须加上 key 属性，属性值不许保证不重复。跟 vue 底层处理虚拟 dom 有关。一般来说 key 的值都是后台数据的 id 的值

script

```js
data() {
    return {
      carts: [
        {
          id: "xdg12",
          goodsName: "mac book pro",
          price: 12000,
          num: 1
        },
        {
          id: "djashg12",
          goodsName: "奥迪A8",
          price: 1200000,
          num: 1
        }
      ]
    };
  ...
```

#### Vue 组件的 prop

组件的复用：就是小的组件在大组件中反复使用。需要父组件传递对应的信息给子组件。如何传递，就需要使用 vue 组件 prop。如何使用 prop

- 在父组件内使用子组件的时候，可以给子组件创造属性(相当传递的数据) 例如 Header 组件内写成`<Button text="登录"/>`
- 在子组件内的默认导出对象下可以添加一个 props 属性，用来获取父组件传递过来的数据,该属性的属性值是一个数组(也可以是一个对象),数组内写父组件创造的属性名 例如

```js
export default {
  name: 'btn',
  props: ['text']
}
```

写好之后其实 text 就相当于了子组件的一个数据了

- prop 可以设置默认值，直接在 子组件内判断即可 例如
  ```html
  <button class="btn">
    {{text ? text : '默认按钮'}}
  </button>
  ```
- prop 设置默认值的方式还有一种,需要把 props 的属性值写成对象类型,对象下的属性就代表父组件传递过来的属性，该属性的属性值需要写成对象形式，该对象可以有 type default validator ... 属性。 type 属性意思是父组件传递过来的值的类型。 default 属性代表的是默认值。validator 属性是检测父组件传递过来的值是否满足条件，该属性需要写成能一个函数，并返回一个布尔值！

#### 组件的自定义事件

父组件给子组件绑定的自定义事件(父组件向子组件传递函数)

- 在父组件内 使用 @自定义事件名 = "父组件的函数" 向子组件传递函数
- 在子组件内使用 `$emit('自定义函数名')` 接收
- 假如父组件的函数定义的时候写了参数，那么子组件调用的时候就需要传递参数 如何使用 `$emit('自定义函数名','参数1','参数2'。。。)`

例子:
父组件

```html
<button type="signup" text="注册" @clickFun="signUp" />
```

子组件

```js
this.$emit('clickFun')
```

子组件在 template 中直接使用 `$emit('自定义事件名')`

#### 插槽

当父组件想向子组件传递一些 html 结构让子组件展示，此时需要使用插槽。 如何使用

- 在父组件内将需要子组件展示的 html 结构写到子组件的闭合标签内部。例如

  ```html
  <Modal title="对话框" okText="OK" cancelText="Cancel">
    <!-- 插槽的父组件内的写法 -->
    <span>123456</span>
  </Modal>
  ```

- 在子组件内使用 slot 标签接收父组件传递过来的 html 结构 例如

  ```html
  <div class="modal-content">
    <!-- slot代表父组件传递过来的结构-->
    <slot></slot>
  </div>
  ```

  插槽可以添加命名称，称作为具名插槽。(作用就是将父组件传递过来的 html 结构，按需处理，有的结构放在 header 有的结构放在 footer)

- 在父组件内的子组件闭合标签内，使用 template 标签嵌套某个 html 结构，并且给该 template 标签写上 v-slot:名

- 在子组件内 使用 `<slot name="父组件内的 template 标签的v-slot的值"></slot>`

#### 组件之间的交互

- 父组件和子组件之间的交互
  - prop
  - 组件的自定义事件
- 子组件和父组件之间的交互
  子组件修改父组件的状态(data),先在父组件内声明修改自己 data 的方法，把方法传递给子组件执行即可
  - 组件的自定义事件
  - prop
- 兄弟组件之间的交互
  - 将需要交互的 data 定义在共同的祖先组件内
  - 把祖先的 data 和 修改 data 的方法当作 prop 或自定义事件传递给子组件
- vuex(终极解决方案)

#### Vue 组件的计算属性 computed

当个你有了一个 data ，但是使用的时候并不是直接使用 data 数据而是使用 data 数据的变形，此时需要定义一个 computed,computed 的用法和 data 一样 例如

```js
 computed: {
    commentNum() {
      return this.comments.length;
    },
    currentComments() {
      return [...this.comments].reverse();
    }
  }
```

#### 插件的使用

- shortId 简短的 id，辅助生成不重复 id
  - 安装包 `npm i shortid`
  - import 引入
  - 使用

#### Vue 组件内的过渡和动画

transition 和 transition-group

#### Vue 的路由

vue 项目内的页面跳转，本身 vue 内不带路由功能，需要自己添加。

- 安装 vue 路由 `npm i vue-router`
- 新建一个 src/router.js
- 在 router.js 内给 vue 项目安装上路由功能
  ```js
  import Vue from 'vue'
  import VueRouter from 'vue-router'
  Vue.use(VueRouter)
  ```
- 创建路由 `new VueRouter({routes:xxxxx,mode: xxxx})`

  ```js
  const routes = [
    {
      component: '组件名',
      path: '地址'
    }
  ]
  const router = new VueRouter({
    routes,
    mode: 'history'
  })
  ```

- 将创建好的路由导出

  ```js
  export default router
  ```

- 到项目的 main.js 内导入路由并使用

  ```js
  import router from './router'
  new Vue({
    router
  })
  ```

- 在 Vue 项目所有组件内都可以使用路由了

  ```html
  <!-- 使用 router-view 标签展示路由 -->
  <router-view></router-view>
  <!-- 使用 router-link 标签实现路由的跳转 -->
  <router-link to="路由页面的path"></router-link>
  ```

#### Vue 项目部署

- 先确保本地的 localhost:8080 下的项目能正常运行
- 在项目下打开命令行执行 `npm run build` ,把你做好的项目打包到项目下的 dist 文件夹下
- 默认情况下，Vue CLI 会假设你的应用是被部署在一个域名的根路径上，例如 https://www.my-app.com/。如果应用被部署在一个子路径上，你就需要用这个选项指定这个子路径。例如，如果你的应用被部署在 https://www.my-app.com/my-app/，则设置 publicPath 为 /my-app/。
  更改 publicPath，修改 vue cli 的配置环境

  - 在项目根目录下 新建一个文件 vue.config.js ,该文件会自动被加入到 vue 的配置环境中。
  - 在文件内写

    ```js
    module.exports = {
      publicPath:
        process.env.NODE_ENV === 'production' ? '/你的子目录地址/' : '/'
    }
    ```

- publicPath 配置完毕需要重新编译打包生成新的 dist 文件夹在重新部署到你的 github 上

#### Vuex

状态管理模式 ----> 状态共享到 store,通过 store 共享给其他的所有组件, 组件也可以直接修改共享状态
如何创建 store

- 安装 vuex `npm i vuex`
- 在项目下的 src 文件夹下新建一个 store.js。内部写

  ```js
  import Vue from 'vue'
  import Vuex from 'vuex'
  Vue.use(Vuex) //详细参考 官方文档中 插件一节(mixins)
  const store = new Vuex.Store({
    // state 是该项目共享数据的地方
    state: {
      count: 0
    },
    // mutations 内写的都是函数  该函数的作用是修改 state 的方法，而且该函数只能接收两个参数,第一个参数是 state 也就是上面定义好的共享数据,第二个参数是载荷数据(payload),指的是修改 state 需要的其他参数。
    mutations: {
      changeCount(state, newCount) {
        // 将 count 修改成任意值
        state.count = newCount
      }
    }
  })
  export default store
  ```

- 进入到项目下的 main.js 文件内，导入 store, 并且在 new Vue 中添加一条属性叫 store 值为你导入的 store

组件中使用 store

- 直接使用 \$store.state 获取共享的数据即可
- 一般 store 内的数据需要配合 computed 使用

组件内动态修改 store

- 使用 \$store 下的 commit 方法去触发创建好的 mutation 函数 `$store.commit('changeCount')`
  - 修改 store 的时候有可能需要传递参数。如何传递----> `$store.commit('changeCount',1000)`
  - 注意 传递的参数只能有一个，想要传递多个的话，把多个参数合并成对象传递

#### Vuex 关键字

###### state 属性

存放公共状态的属性，vue 组件内获取方式 `$store.state`

###### mutations 属性

存储修改 state 的方法的对象

- mutation 函数内可以接收两个参数 1.state 2.payload
- 该函数必须是同步函数
- 通过 store 的 commit 方法触发 mutation 函数

###### actions 属性

存储异步操作函数的对象,修改 state 时需要发送请求,但是请求不能写到 mutation 函数内

- action 函数内可以接收两个参数 1.context 2.payload
- 该函数必须是异步函数, 如果没有异步操作不需要写 action 函数
- 通过 store 的 dispatch 方法触发 action 函数

###### getters 属性

store 的计算属性, vue 组件内获取方式 `$store.getters`

- getters 函数内可以接收三个参数 1.state(自己模块的 state) 2.getters(store 内的其他 getters) 3. rootState (根目录的 state)
- 用法和写法与组件的 computed 一样

#### 错误提示

- `<Dem> - did you register the component correctly?`
- `Failed to compile.` 编译失败 `Module not found: Error: Can't resolve './components/Dem' in 'D:\digitalcity授课\2019\1903\1903\vue-demo\src'`

使用 sass
`npm install node-sass --save-dev`
`npm install sass-loader --save-dev`
[sass](https://www.cnblogs.com/gudi/p/8075631.html)
[scope](https://segmentfault.com/a/1190000015932467)

#### vue 跨域

- vue cli3

- 建立 vue.config.js 文件

```js
module.exports = {
  devServer: {
    // 配置代理服务器
    proxy: {
      '/api': {
        target: 'https://www.wanandroid.com',
        changeOrigin: true,
        ws: true,
        pathRewrite: {
          '^/api': ''
        }
      }
    }
  }
}
```

this.\$el.textContent

#### VUE 全局过滤器 filter

1.1 过滤器科用在两个地方：双花括号插值 和 v-bind 表达式 中。过滤器应该被添加在 js 表达式的尾部，由管道符号指示

```js
// 双花括号中
{
  {
    message | capitalize
  }
}

// 在v-bind 中
;<div v-bind:id=' rawId | formatId'></div>
```

1.2 定义过滤器

- 在组件选项中定义本地过滤器

```js
//  参数1：表示要过滤的内容
//  参数2：表示传递给过滤器的格式

filters: {

  capitalize: function (value) {
    if (!value) return ''
    value = value.toString()
    return value.charAt(0).toUpperCase() + value.slice(1)
  }

}
```

- 在创建 Vue 实例前定义全局过滤器

```js
//  参数1：过滤器名称
//  参数2：过滤器的逻辑

Vue.filter('capitalize', function(value) {
  if (!value) return ''
  value = value.toString()
  return value.charAt(0).toUpperCase() + value.slice(1)
})

new Vue({
  // ...
})
```

#### vuex 在模块中 getters 和 actions 命名重复会冲突，用命名空间即可解决

```js
export default {
  namespaced: true,
  state,
  actions,
  mutations
}
```
