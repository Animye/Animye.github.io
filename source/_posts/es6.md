---
title: ES6
date: 2019-08-01 11:47:07
tags:
---

## ES6 含义

- ES6 既是一个历史名词，也是一个泛指，含义是 5.1 版以后的 JavaScript 的下一代标准，涵盖了 ES2015、ES2016、ES2017 等等，而 ES2015 则是正式名称，特指该年发布的正式版本的语言标准。本书中提到 ES6 的地方，一般是指 ES2015 标准，但有时也是泛指“下一代 JavaScript 语言”。

<!-- more -->

[es6 学习地址](https://www.jianshu.com/p/cfb0893c34f1)
[promise 学习地址](https://www.jianshu.com/p/fe5f173276bd)
[阮一峰 es6](http://es6.ruanyifeng.com/#docs/intro)

## Set 实例的属性和方法

- Set 结构的实例有以下属性。

`Set.prototype.constructor：构造函数，默认就是Set函数。`
`Set.prototype.size：返回Set实例的成员总数。`
`Set 实例的方法分为两大类：操作方法（用于操作数据）和遍历方法（用于遍历成员）。下面先介绍四个操作方法。`

`Set.prototype.add(value)：添加某个值，返回 Set 结构本身。`
`Set.prototype.delete(value)：删除某个值，返回一个布尔值，表示删除是否成功。`
`Set.prototype.has(value)：返回一个布尔值，表示该值是否为Set的成员。`
`Set.prototype.clear()：清除所有成员，没有返回值。`
`Array.from方法可以将 Set 结构转为数组。`

- 遍历操作
  Set 结构的实例有四个遍历方法，可以用于遍历成员。

Set.prototype.keys()：返回键名的遍历器
Set.prototype.values()：返回键值的遍历器
Set.prototype.entries()：返回键值对的遍历器
Set.prototype.forEach()：使用回调函数遍历每个成员
**由于 Set 结构没有键名，只有键值（或者说键名和键值是同一个值），所以 keys 方法和 values 方法的行为完全一致。**
