---

title: 数组includes方法
date: 2019-11-28 08:49:37
tags:

---
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
测试用法women 

