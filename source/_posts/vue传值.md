---
title: vue传值
date: 2020-05-16 10:18:44
tags:
  - nuxt
---

## vue 调用方法

### vue 子组件调用父组件的方法

<!-- more -->

#### 方式一

- 父组件定义方法
- 子组件`this.$parent.父组件方法();`

#### 方式二

- 父组件定义方法，并用 props 传递过来 `<child :fatherMethod="fatherMethodOther"></child>`
- 子组件 props 接收并调用

```js
export default {
  props: {
    fatherMethod: {
      type: Function,
      default: null
    }
  },
  methods: {
    childMethod() {
      if (this.fatherMethod) {
        this.fatherMethod("hello");
      }
    }
  }
};
```

#### 方式三

- 父组件定义方法，并用 v-on 传递 `<child @fatherMethod="fatherMethodOther"></child>`
- 子组件运用\$emit 接收 `this.$emit('fatherMethod', 'hello');`

### vue 父组件调用子组件方法

#### 方式一

- 运用 refs
- 子组件定义方法名
- 父组件在子组件上添加 ref`<HelloWorld ref="mychild"></HelloWorld>`
- 父组件调用 `this.$refs.mychild.子组件方法名();`

### vue 兄弟组件传递方法

- 兄弟组件之间的通讯有一个方法是通过父组件进行交互，那么解决的思路就是子组件调用父组件的方法，然后父组件调用另一个子组件的方法，这样就实现了兄弟组件的交互功能。
- 在 child2 里用 this.\$emit('fun')传到父组件里

- 在父组件里，给 child1 组件加上 ref="child1Container"属性

- 在 methods 里定义 fun 方法（this.\$refs.child1Container.某个方法（））

1. 父组件 parent.vue 中的子组件加一个 ref 属性，就相当于给这个子组件取了一个别名。注意，这个是加在需要调用的子组件上的。

```vue
// 父组件
<template>
  <child1 ref="child1Container"></child1>
  <child1 @save="save"></child1>
</template>

<script>
import Header from "./components/child1";
import SubRoute from "./components/child2";

export default {
  name: "App",
  components: {
    child1,
    child2
  },
  methods: {
    save() {
      this.$refs.child1Container.aaa();
    }
  }
};
</script>
```

```vue
// 子组件 1
<template>
  <div>我是子组件 11111</div>
  <div @click="aaa"></div>
</template>

<script>
export default {
    name: 'App',
    methods: {
        aaa(){
            console.log('我是子组件1里面的方法")
        }
    }
}
</script>
```

```vue
// 子组件 2
<template>
  <div>我是子组件 22222</div>
  <div @click="save"></div>
</template>

<script>
export default {
  name: "App",
  methods: {
    save() {
      this.$emit("save");
    }
  }
};
</script>
```

### vue 传值没有限制

#### 方式一

- 运用 bus

```js
  async mounted() {
    this.initData()
    Bus.$on('initData', this.initData)
  },
```

- 接收不传值`Bus.$emit(initData)`接收传值`Bus.$emit('initData','传值')`

#### 方式二

- 运用 vuex
