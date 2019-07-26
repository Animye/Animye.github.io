---
title: function
date: 2019-07-25 09:16:32
tags:
---

## 函数

### 函数的防抖和节流

[参考资料 1](https://www.jianshu.com/p/c8b86b09daf0)
[参考资料 2](https://blog.csdn.net/duola8789/article/details/78871789)
[参考资料 3](https://www.jianshu.com/p/f9f6b637fd6c)

  <!-- more -->

#### 防抖

- 概念：就是指触发事件后在 n 秒内函数只能执行一次，如果在 n 秒内又触发了事件，则会重新计算函数执行时间。
  打个比方，坐公交，司机需要等最后一个人进入才能关门。每次进入一个人，司机就会多等待几秒再关门。

```js
/**
 * 空闲控制 返回函数连续调用时，空闲时间必须大于或等于 wait，func 才会执行
 *
 * @param  {function} func        传入函数，最后一个参数是额外增加的this对象，.apply(this, args) 这种方式，this无法传递进函数
 * @param  {number}   wait        表示时间窗口的间隔
 * @param  {boolean}  immediate   设置为ture时，调用触发于开始边界而不是结束边界
 * @return {function}             返回客户调用函数
 */
const debounce = function(func, wait, immediate) {
  let timeout, args, context, timestamp, result

  const later = function() {
    // 据上一次触发时间间隔
    let last = Number(new Date()) - timestamp

    // 上次被包装函数被调用时间间隔last小于设定时间间隔wait
    if (last < wait && last > 0) {
      timeout = setTimeout(later, wait - last)
    } else {
      timeout = null
      // 如果设定为immediate===true，因为开始边界已经调用过了此处无需调用
      if (!immediate) {
        result = func.call(context, ...args, context)
        if (!timeout) {
          context = args = null
        }
      }
    }
  }

  return function(..._args) {
    context = this
    args = _args
    timestamp = Number(new Date())
    const callNow = immediate && !timeout
    // 如果延时不存在，重新设定延时
    if (!timeout) {
      timeout = setTimeout(later, wait)
    }
    if (callNow) {
      result = func.call(context, ...args, context)
      context = args = null
    }

    return result
  }
}
```

#### 节流

- 概念：所谓节流，就是指连续触发事件但是在 n 秒中只执行一次函数。节流会稀释函数的执行频率。
- 举个例子，乘坐地铁，过闸机时，每个人进入后 3 秒后门关闭，等待下一个人进入。

```js
/**
 * 频率控制 返回函数连续调用时，func 执行频率限定为 次 / wait
 *
 * @param  {function}   func      传入函数
 * @param  {number}     wait      表示时间窗口的间隔
 * @param  {object}     options   如果想忽略开始边界上的调用，传入{leading: false}。
 *                                如果想忽略结尾边界上的调用，传入{trailing: false}
 * @return {function}             返回客户调用函数
 */
const throttle = function(func, wait, options) {
  let context, args, result
  let timeout = null
  // 上次执行时间点
  let previous = 0
  if (!options) options = {}
  // 延迟执行函数
  let later = function() {
    // 若设定了开始边界不执行选项，上次执行时间始终为0
    previous = options.leading === false ? 0 : Number(new Date())
    timeout = null
    result = func.apply(context, args)
    if (!timeout) context = args = null
  }
  return function(..._args) {
    let now = Number(new Date())
    // 首次执行时，如果设定了开始边界不执行选项，将上次执行时间设定为当前时间。
    if (!previous && options.leading === false) previous = now
    // 延迟执行时间间隔
    let remaining = wait - (now - previous)
    context = this
    args = _args
    // 延迟时间间隔remaining小于等于0，表示上次执行至此所间隔时间已经超过一个时间窗口
    // remaining大于时间窗口wait，表示客户端系统时间被调整过
    if (remaining <= 0 || remaining > wait) {
      clearTimeout(timeout)
      timeout = null
      previous = now
      result = func.apply(context, args)
      if (!timeout) context = args = null
      //如果延迟执行不存在，且没有设定结尾边界不执行选项
    } else if (!timeout && options.trailing !== false) {
      timeout = setTimeout(later, remaining)
    }
    return result
  }
}
```

### return

#### return 和 return false 的区别

1. return;返回 null，起到中断方法执行的效果，只要不 return false 事件处理函数将会继续执行，表单将提交
2. return false;，事件处理函数会取消事件，不再继续向下执行。比如表单将终止提交

- retrun true； 返回正确的处理结果。
- return false；返回错误的处理结果，终止处理。
- return；把控制权返回给页面。
