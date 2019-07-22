---
title: CSS 基础
date: 2019-02-26 13:32:59
tags:
  - css
---

&#160; &#160; &#160; &#160;**层叠样式表(英文全称：Cascading Style Sheets)是一种用来表现 HTML（标准通用标记语言的一个应用）或 XML（标准通用标记语言的一个子集）等文件样式的计算机语言。CSS 不仅可以静态地修饰网页，还可以配合各种脚本语言动态地对网页各元素进行格式化。**

  <!-- more -->

## 容易忘

- visibility：hidden 隐藏
- visibility：visible 显示
  **隐藏后仍然占据空间**
- vertical-aligh:middle 兄弟元素，兄弟之间居中（行级块）
- width:calc(670px \* 5) 计算宽度（兼容性差）
- cursor：auto 箭头
- cdn 指的是加速服务
- script 写在 body 最下方
- meta：vp 移动端 meta 声明
- display:inline 块边行
- vertical-aligh:-2px（可以负数） 垂直方向（用于对齐），必须有行
- text-decoration:none(无)/underline（下划线）/overline（上面）/lin-through(中间删除)
- data-locale 自定义
- :focus 获取焦点（如:hover 这类叫做伪类选择器）权重 10
- box-shadow:水平，垂直，模糊（越大越淡），阴影大小，颜色，inset 阴影

## 单文本超出显示三个点

```js
<style>white-space:nowrap; overflow:hidden; text-overflow:ellipsis</style>
```

1. 宽度
2. 不换行
3. 溢出隐藏 oh
4. 设置文本超出显示三个点

## 媒体查询

```js
@media screen and(min-width:500px) and (max-width:700px){

}
//指的是500到700
```

## flex 布局

### 容器的相关属性

```js
justify-content(项目在主轴方向上的对齐方式):center 居中
                                        space-between 第一个最左边，最后一个在最右边，其他间距相同
                                        space-around 左右一倍间距，中间两倍间距
                                        flex-start  全靠左
                                        flex-end 全靠右
aligh-items(项目在副轴上的对齐方式):center 居中
                                stretch
                                baseline
flex-direction(规定主轴的方向):row 横
                             row-reverse 横向反向
                             column 竖向
                             column-reverse 竖向反向
flex-wrap(项目在主轴方向排不开可以使用该属性换行): wrap 换行 nowrap 不换行
align-content(多轴线是副轴方向上的对齐方式)
```

### 项目相关的属性

```js
order 规定项目的排列顺序，值是数字（默认0），数字越大位置约靠后
flex-grow 规定项目的放大比例，默认是0，即存在剩余空间也不放大，设置为1，即占满剩余空间
flex-shrink 定义了项目的缩小比例，默认为1，即如果空间不足该项目缩小，设置为0，即项目不会缩小
flex-basis
flex-self 单个项目的对齐方式，属性允许单个项目在副轴上有与其他项目不一样的对齐方式，可覆盖aligh-items属性
```

xxx[] 属性选择器
input[placeholder] 即带 placeholder 的 input
