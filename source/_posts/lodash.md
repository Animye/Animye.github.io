---
title: lodash
date: 2019-07-26 10:04:57
tags:
---

## 概念

- Lodash 就是这样的一套工具库，它内部封装了诸多对字符串、数组、对象等常见数据类型的处理函数，其中部分是目前 ECMAScript 尚未制订的规范，但同时被业界所认可的辅助函数。

[官网](https://www.lodashjs.com/)

## 模块的组成

Array， 适合于数组类型，比如填充数据、查找元素、数组分片等操作
Collocation， 适用于数组和对象类型，部分适用于字符串，比如分组、查找、过滤等操作
Function， 适用于函数类型，比如节流、延迟、缓存、设置钩子等操作

<!-- more -->

Lang， 普遍适用于各种类型，常用于执行类型判断和类型转换
Math， 使用与数值类型，常用于执行数学运算
Number， 适用于生成随机数，比较数值与数值区间的关系
Object， 适用于对象类型，常用于对象的创建、扩展、类型转换、检索、集合等操作
Seq， 常用于创建链式调用，提高执行性能（惰性计算）
String， 适用于字符串类型
lodash/fp 模块提供了更接近函数式编程的开发方法，其内部的函数经过包装，具有 immutable、auto-curried、iteratee-first、data-last（官方介绍）等特点。
Fixed Arity，固化参数个数，便于柯里化
Rearragned Arguments， 重新调整参数位置，便于函数之间的聚合
Capped Iteratee Argument， 封装 Iteratee 参数

## 在 vue 中使用

### 使用 npm 安装

```js
npm install --save lodash
npm install --save-dev babel-plugin-lodash

import _ from 'lodash';
import { add } from 'lodash/fp';

const addOne = add(1);
_.map([1, 2, 3], addOne);
```

[参考资料](https://www.cnblogs.com/e0yu/p/10843420.html)
