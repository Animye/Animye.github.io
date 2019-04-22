---
title: CSS 基础
date: 2019-02-26 13:32:59
tags:
  - css
---

&#160; &#160; &#160; &#160;**层叠样式表(英文全称：Cascading Style Sheets)是一种用来表现 HTML（标准通用标记语言的一个应用）或 XML（标准通用标记语言的一个子集）等文件样式的计算机语言。CSS 不仅可以静态地修饰网页，还可以配合各种脚本语言动态地对网页各元素进行格式化。**

  <!-- more -->

# 容易忘

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

# 单文本超出显示三个点

```js
<style>white-space:nowrap; overflow:hidden; text-overflow:ellipsis</style>
```

1. 宽度
2. 不换行
3. 溢出隐藏 oh
4. 设置文本超出显示三个点

# 媒体查询

```js
@media screen and(min-width:500px) and (max-width:700px){

}
//指的是500到700
```
