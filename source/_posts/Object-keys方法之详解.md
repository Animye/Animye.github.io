---
title: Object.keys方法之详解
date: 2019-12-03 18:57:23
tags:
---

[参考地址](https://blog.csdn.net/weixin_43675447/article/details/99232258)

## 语法

```js
Object.keys(obj)

参数：要返回其枚举自身属性的对象

返回值：一个表示给定对象的所有可枚举属性的字符串数组
```

<!-- more -->

## 处理对象，返回可枚举的属性数组

```js
let person = { name: "张三", age: 25, address: "深圳", getName: function() {} };

Object.keys(person); // ["name", "age", "address","getName"]
```

## 处理数组，返回索引值数组

```js
let arr = [1, 2, 3, 4, 5, 6];

Object.keys(arr); // ["0", "1", "2", "3", "4", "5"]
```

## 处理字符串，返回索引值数组

```js
let str = "saasd 字符串";

Object.keys(str); // ["0", "1", "2", "3", "4", "5", "6", "7"]
```

## 常用技巧

```js
let person = { name: "张三", age: 25, address: "深圳", getName: function() {} };

Object.keys(person).map(key => {
  person[key]; // 获取到属性对应的值，做一些处理
});
```

## Object.values()和 Object.keys()是相反的操作，把一个对象的值转换为数组

## 使用 Object.values() 将 N 个类似的数据合并成一个

```js
const source = [
  { title: "问题1", id: 0, content: "A" },
  { title: "问题1", id: 1, content: "B" },
  { title: "问题1", id: 2, content: "C" },
  { title: "问题2", id: 3, content: "D" },
  { title: "问题3", id: 4, content: "E" }
];
const obj = {};
source.forEach(e => {
  const isHaveObj = obj[e.title];
  if (isHaveObj) {
    isHaveObj.totalId.push({ id: e.id });
    isHaveObj.content.push(e.content);
  } else {
    obj[e.title] = {
      title: e.title,
      totalId: [{ id: e.id }],
      content: [e.content]
    };
  }
});
const result = Object.values(obj);
```

## Object.entries()

- Object.entries 方法返回一个数组，成员是参数对象自身的（不含继承的）所有可遍历（enumerable）属性的键值对数组

```js
//遍历对象的属性
let obj = {
  one: 1,
  two: 2
};
for (let [k, v] of Object.entries(obj)) {
  console.log(`${JSON.stringify(k)} : ${JSON.stringify(v)}`);
}
```
