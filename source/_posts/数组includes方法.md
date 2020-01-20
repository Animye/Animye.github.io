---
title: 数组includes方法
date: 2019-11-28 08:49:37
updated: 2019-12-28 08:49:37
tags:
---

#### 定义

- includes() 方法用来判断一个数组是否包含一个指定的值，如果是返回 true，否则 false。

```js
[1, 2, 3].includes(2); // true
[1, 2, 3].includes(4); // false
[1, 2, 3].includes(3, 3); // false
[1, 2, 3].includes(3, -1); // true
[1, 2, NaN].includes(NaN); // true
```

#### 借助 includes()方法求两个数组的交集（适用于对象数组）

```js
var a = [1, 2, { s: 3 }, { s: 4 }, { s: 5 }].map(item => JSON.stringify(item));
var b = [{ s: 2 }, { s: 3 }, { s: 4 }, "a"].map(item => JSON.stringify(item));

var diff = a.filter(v => b.includes(v)).map(item => JSON.parse(item));

// diff: [{s: 3},{s: 4}]
```

<!-- more -->

#### 借助 includes()方法求两个数组的差集（适用于对象数组）

```js
var a = [1, 2, { s: 3 }, { s: 4 }, { s: 5 }].map(item => JSON.stringify(item));
var b = [{ s: 2 }, { s: 3 }, { s: 4 }, "a"].map(item => JSON.stringify(item));

var diff = a
  .concat(b)
  .filter(v => !a.includes(v) || !b.includes(v))
  .map(item => JSON.parse(item));

// diff: [1, 2, {s:5}, {s:2}, "a"]
```
