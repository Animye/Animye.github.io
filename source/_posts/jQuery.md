---
title: jQuery 基础
date: 2019-02-26 13:42:29
tags:
  - jQuery
---

&#160; &#160; &#160; &#160;**如果你了解 JavaScript 语言，那将对你掌握 jQuery 如虎添翼，因为 jQuery 本身就是 JavaScript，只不过是把 JavaScript 代码包装成拿过来就能实现特定功能的代码库！**

<!-- more -->

# jQuery 里面的方法

- `siblings(可以放选择器)` 查找同一级别的兄弟元素，不限个数
- `parent()` 查找父级元素（即向上）
- `find(里面必须写选择器)` 查找后代元素
- `children()` 查找所有的子级元素
- `parents(里面必须写选择器)` 查找祖先元素
- `index()` 返回某个人在父级中的位置（也就是属于第几个子集然后数字是从零开始）
- `next()` 找到相邻的下一个兄弟元素
- `prev()` 找到相邻的上一个兄弟元素
- `eq()` 选择器
- `addClass("class名")` 添加类名
- `removeClass("class名")` 删除类名
  **添加和删除必须一起使用**
- `toggle("class名")` 替换类名
- `attr("属性名")` 获取某个属性对应的属性值
- `attr("属性名"，"属性值")` 修改/设置某个属性对应的属性值
- `html("属性名")` 获取元素内部的 html 内容
- `html("属性名"，"属性值")` 修改/设置某个元素内部的 html 内容
  **heml 的属性 开始标签内部写的东西都称之为属性 （）里可以直接写 html 字符串，html 方法可以将 html、的标签拆成 HTML 标签，但是 text 方法不行**
- `val()` 获取 input 输入框内输入的内容
- `val(“xx”，“xx”)` 修改/设置 input 输入框内输入的内容
- `text()` 获取标签内的文本内容
- `text(“xx”，“xx”)` 修改/设置标签内的文本内容
- `trim()` 该方法会将一个值的左右两侧的空字符全部去掉
  **空字符：空格、回车、TAB**

- `scrollTop()` 获取滚动条距页面顶部的距离
- `xx.offset().top/left` 某个元素距离文档（body）顶部的距离，xx 代表某个 html 元素，xx 位于顶部的距离
  **有了上述值之后，我们解决问题的方案就变成了点击按钮获取对应的 box 距离顶部的距离，将该距离设置成浏览器窗口的滚动条距离顶部的距离**
- `width()` 获取宽
- `height()` 获取高
- `innerwidth()` 包括 padding
- `outwidth` 包括 border
- `trigger("事件名（例如click）")` 可以模拟其他元素事件触发，可以执行其他元素事件里面执行的内容

```js
$("button").trigger("click")
}
```

- `prop("checked")` 获取 checkbox 的当前状态，选中得到 true 反之得到 false
- `removeAttr()` 删除该属性

## 动画

- `show(时间)` 消失
- `hide(时间)` 出现
- `toggle(时间)` 切换
  **css 动画会在元素消失出现的时候再次执行**
- `slideUp(时间)` 消失
- `slideDown(时间)` 出现
- `slideToggle(时间)` 切换
- `fadeIn(时间)` 消失 渐变
- `fadeOut(时间)` 出现
- `fadeToggle(时间)` 切换
- `fadeTo(时间,透明度)` 切换
  **让 div 在 1 秒后变成 0.5 透明度无法用 toggle 切换**

- `stop()`将 stop 之间的动画全部停止
- `delay()`将动画延迟执行
  **delay 和 stop 同时使用，stop 放后面**

### 动画的回调

- 所有的 jquery 动画方法，都可以写成回调（当某个动画执行完毕之后想要执行其他的事），jquery 的动画不会影响其他的语句的执行，也就是写在动画的后面的语句不会在动画执行完毕之后再执行。

```js
.XXX(1000,function(){动画执行完毕之后做的事})
```

#### 自定义动画

- **jquery 动画当给同一个元素写不同的动画时，不需要写成回调形式，也是先后执行的**
- animate（{样式}，时间）回调
  **animate 不能给转换加动画，只能给值是数字的样式加动画**

```js
.animate({"width":"100px"},1000)
```

### 绑定一次性的事件

- 执行完事件做的事之后给按钮加上：disabled

```js
$('button').attr('disabled', true)
```

- one 绑定事件 执行一次

```js
$("button").one("click",function(){
  console.log(1)
})
}
```

- 先定义一个全局变量 在事件内判断 修改

```js
var num=0
$("button").click(function(){
  if(num===0){
    console.log(1)
    num=1
  }
})
}
```

- 使用 off 解绑

```js
$("button").click(function(){
  console.log(1)
  $("button").off("click")
})
}
```

### 阻止 a 的默认跳转行为

1. 事件内 event.preventDefault()
2. 事件内最后面加 return false
3. 标签内 href="javascript:void(0)"
4. 标签内 href="javascript:;"

### dom 操作

```js
$("li")
//新建li标签
$("<li>"),$("<button>删除</button>")
用 .text()设置标签内的文本内容
或者用.html()设置  这种方法能用模板字符串
xx.remove()
//删除xx元素
父级.append(元素)
//将后面元素添加到另一个元素内部，当做最后一个子级
父级.prepend(元素)
//将后面元素添加到另一个元素内部，当做第一个子级
元素.after(元素)
//将后面元素添加到前面元素，当做其后一个兄弟
元素.before(元素)
//将后面元素添加到前面元素，当做前面一个兄弟
.empty()
//清空一个标签
appendTo(),prepend(),insertAfter(),insertBefore()
//与上面功能一样，但是使用方法是相反的
```
