---
title: javaScript  原生JS 基础
date: 2019-02-26 13:43:46
tags:
  - 原生JS
---

&#160; &#160; &#160; &#160;**JavaScript 是一种直译式脚本语言，是一种动态类型、弱类型、基于原型的语言，内置支持类型。它的解释器被称为 JavaScript 引擎，为浏览器的一部分，广泛用于客户端的脚本语言，最早是在 HTML（标准通用标记语言下的一个应用）网页上使用，用来给 HTML 网页增加动态功能。现在 是互联网上最流行的脚本语言，这门语言可用于 HTML 和 web，更可广泛用于服务器、PC、笔记本电脑、平板电脑和智能手机等设备。**
**JavaScript 是 Web 的编程语言，是前端开发必须掌握的三门语言之一，即：**

1. HTML 定义了网页的内容
2. CSS 描述了网页的布局
3. JavaScript 实现了网页的行为

   <!-- more -->

## 基础

1. 语句：JavaScript 程序的执行单位为行（line），也就是一行一行地执行。一般情况下，每一行就是一个语句。语句以分号结尾，一个分号就表示一个语句结束。多个语句可以写在一行内。
2. 表达式：指一个为了得到返回值的计算式。语句和表达式的区别在于，前者主要为了进行某种操作，一般情况下不需要返回值；后者则是为了得到返回值，一定会返回一个值。凡是 JavaScript 语言中预期为值的地方，都可以使用表达式。比如，赋值语句的等号右边，预期是一个值，因此可以放置各种表达式。
3. 标识符：指的是用来识别各种值的合法名称，最常见的标识符就是变量名，以及后面要提到的函数名。JavaScript 语言的标识符对大小写敏感，所以 a 和 A 是两个不同的标识符。
   **JavaScript 有一些保留字，不能用作标识符：arguments、break、case、catch、class、const、continue、debugger、default、delete、do、else、enum、eval、export、extends、false、finally、for、function、if、implements、import、in、instanceof、interface、let、new、null、package、private、protected、public、return、static、super、switch、this、throw、true、try、typeof、var、void、while、with、yield。**
4. 区块：JavaScript 使用大括号，将多个相关的语句组合在一起，称为“区块”（block）。单独使用区块并不常见，区块往往用来构成其他更复杂的语法结构，比如 for、if、while、function 等。
5. 条件语句：JavaScript 提供 if 结构和 switch 结构，完成条件判断，即只有满足预设的条件，才会执行相应的语句。
6. typeof 运算符
   JavaScript 有三种方法，可以确定一个值到底是什么类型。
   typeof 运算符
   instanceof 运算符
   Object.prototype.toString 方法
7. null 和 undefined 区别是这样的：null 是一个表示“空”的对象，转为数值时为 0；undefined 是一个表示"此处无定义"的原始值，转为数值时为 NaN。

```js
下面是返回undefined的经典场景;
// 变量声明了，但没有赋值
var i;
i; // undefined

// 调用函数时，应该提供的参数没有提供，该参数等于 undefined
function f(x) {
  return x;
}
f(); // undefined

// 对象没有赋值的属性
var o = new Object();
o.p; // undefined

// 函数没有返回值时，默认返回 undefined
function f() {}
f(); // undefined
```

8. false：转换规则是除了下面六个值被转为 false，其他值都视为 true。
   undefined
   null
   false
   0
   NaN
   ""或''（空字符串）
   **布尔值往往用于程序流程的控制，注意，空数组（[]）和空对象（{}）对应的布尔值，都是 true。**
9. 数值精度：根据国际标准 IEEE 754，JavaScript 浮点数的 64 个二进制位，从最左边开始，是这样组成的。
   第 1 位：符号位，0 表示正数，1 表示负数
   第 2 位到第 12 位（共 11 位）：指数部分
   第 13 位到第 64 位（共 52 位）：小数部分（即有效数字）
10. NAN：NaN 是 JavaScript 的特殊值，表示“非数字”（Not a Number），主要出现在将字符串解析成数字出错的场合。
    **需要注意的是，NaN 不是独立的数据类型，而是一个特殊数值，它的数据类型依然属于 Number，使用 typeof 运算符可以看得很清楚。NaN 不等于任何值，包括它本身。**

## 内存空间

```js
var a = 10; // 变量对象
var b = { a: 10 }; // 变量b存在于变量对象中，{a: 10} 作为对象存在于堆内存中
```

![avatar](/assets/img/变量对象.png)

## 变量

- 分两种一种是基本类型，一种是引用类型

  `基本类型就是基础数据类型 ,引用类型就是复杂数据类型obj及其引申出的`
  基本类型：在内存中占据实际大小的空间，赋值的时候，会在内存中创建一份新的副本。
  引用类型：指向对象的指针而不是对象本身，赋值的时候，只是创建了一个新的指针指向对象。
  确定一个变量是哪种基本类型用 typeof 操作符。
  确定一个变量是哪种引用类型用 instanceof 操作符。
  [参考链接](https://www.jianshu.com/p/66f3aef3e131)

## 数据类型

### 五种基础数据类型

- number
- null
- undefind
- string
- boolean

### 一种复杂数据类型

- object

### 内置对象

#### Array

##### 数组的方法

**由于空位的处理规则非常不统一，所以建议避免出现空位。**

1. push(要添加的元素) 向数组内部的最后添加的元素，原来的数组不变，该方法返回新数组的长度
2. unshift() 向数组前面添加元素，原来的数组不变，该方法返回新数组的长度
3. concat(另一个数组) 将两个数组拼接，原来的数组不变，并返回新得到的数组
4. pop() 删除数组中的最后一项，原数组不变，并返回被删除的数组
5. shift(添加的元素) 向数组前面删除，原数组不变，并返回被删除的数组
6. slice(a,b) 对数组进行截取，从下标 a 开始到 b 结束（包括开始不包括结束），原数组不变，返回被截取的数组，这个方法可以用来做数组的拷贝，这个方法可以只写开始不写结束，意思是从开始直接截取到最后，包括最后一项
7. splice(a,b,c) 对数组进行添加和删除 a.代表添加或删除的位置（下标） b.代表删除的个数 c.代表要添加的元素（可以省略） 原数组改变，返回被删除元素组成的数组，没有删除的话返回[](空数组)
8. join(a) 将数组的每一项以 a 作为连接符，拼接成字符串，原数组不变，返回新得到的字符串， a 默认为逗号
9. reverse() 将数组数据颠倒，原数组改变，并返回颠倒后的新数组。
10. indexOf(要查找的元素),查找数组内是否包含某个元素，如果包含返回第一个匹配的下标，否则返回-1，原数组不会改变（只能针对非对象数组）
11. filter() 过滤 将一个数组根据条件生成另一个数组，原数组不变，返回新生成的数组 例：XXX.filter(function
    (ele,index,array){return 条件}) ele 代表数组中的某一项 index 代表的书该项的下标 array 代表原数组
    **如果数组中的某一项满足条件的话，就放入到新生成的数组内**
    return 的作用：当查找到某一项的时候，只要 return 后面的值为 true，那么新生成的数组内就会添加到该项
12. forEach 数组的遍历
13. find() 数组的查找，通常使用在对象数组（数组里存放的是对象类型）上 例如：XXX.find(function
    (ele,index,array){return 条件 xx}) 在数组中查找符合 return 后面条件的第一个元素并返回，原数组不变，查找不到返回 undefined
    **数组 find 方法找到某一个对象，和数组内的某一个对象指向的是同一个地址，我们更改了 find 方法找到的对象，就相当于修改了数组内的对象，也就相当于修改了数组，那么数据就发生了变化，页面因此改变**
14. findIndex() 查找的是下标，查不到返回-1，跟 find 用法一样
15. every() 检测所有元素是否符合条件，符合条件返回 true，不符合返回 false，通常用来查询数组中是否都是同一个元素
16. includes() 使用该方法替换 indexOf ,方法返回一个布尔值，表示某个数组是否包含给定的值，与字符串的 includes 方法类似。ES2016 引入了该方法。
17. sort() 给数组排序 例如：xxx.sort(function(a,b){return a-b（正序）/b-a（倒序）}) a 和 b 代表的是数组相邻的两项 a-b 让相邻两项进行数学运算，如果小于 b 从小到大，反之从大到小， 原数组改变，返回值就是新数组
18. 数组实例的 entries()，keys() 和 values()
    keys()是对键名的遍历、values()是对键值的遍历，entries()是对键值对的遍历。
19. fill(),fill 方法使用给定值，填充一个数组。
    `['a', 'b', 'c'].fill(7)// [7, 7, 7]`
20. copyWithin(),在当前数组内部，将指定位置的成员复制到其他位置（会覆盖原有成员），然后返回当前数组。也就是说，使用这个方法，会修改当前数组。
    `Array.prototype.copyWithin(target, start = 0, end = this.length)`
    它接受三个参数。
    -target（必需）：从该位置开始替换数据。如果为负值，表示倒数。
    -start（可选）：从该位置开始读取数据，默认为 0。如果为负值，表示从末尾开始计算。
    -end（可选）：到该位置前停止读取数据，默认等于数组长度。如果为负值，表示从末尾开始计算。
    这三个参数都应该是数值，如果不是，会自动转为数值。
21. Array.from(),Array.from 方法用于将两类对象转为真正的数组
22. Array.of(),Array.of 方法用于将一组值，转换为数组。
    `Array.of(3, 11, 8) // [3,11,8]`
    `Array.of(3) // [3]`
    `Array.of(3).length // 1`
23. 数组实例的 flat()，flatMap(),
    数组的成员有时还是数组，Array.prototype.flat()用于将嵌套的数组“拉平”，变成一维的数组。该方法返回一个新数组，对原数据没有影响。
    flatMap()方法对原数组的每个成员执行一个函数（相当于执行 Array.prototype.map()），然后对返回值组成的数组执行 flat()方法。该方法返回一个新数组，不改变原数组。
24. reduce()
25. some() 检测所有元素是否符合条件，符合条件返回 true，不符合返回 false

```js
xxx.reduce(function(result,ele,ind,array){rerurn xxx},0)
result:代表最终结果
ele:代表数组的一项
ind:代表对应下标
最后的0:代表最终结果的初始值，是自己定义的
function的大括号内必须填写返回最后的结果
return 有一个额外的意思，就是当做下一次遍历数组的初始值
最后一次的return 就是result函数的返回值
每一次reduce内部的函数执行完毕后必须有返回值，原数组不变，返回新的值
```

- 已知一个数组随机

```js
const arr = [1, 2, 3, 4, 5];
const newArr = [];
for (let index = 0; index < arr.length; index++) {
  const num = Math.floor(Math.random() * arr.length);
  const val = arr[num];
  newArr.push(val);
  index--;
  arr.splice(num, 1);
}
console.log(newArr);
```

- 已知一个数组去重

```js
function removal(arr) {
  newArr = []
  for (let i = 0; i < arr.length; i++) {
    if (newArr.indexOf(arr[i]) == -1) {
      newArr.push(arr[i])
    }
  }
  return newArr
}
const arr = [1, 1, 1, 3, 4, 53, 636, 6, 5, 5]
console.log(removal(arr))
// function arr(array) {
//   return array.reduce((m, n) => {
//     if (m.indexOf(n) == -1) {
//       m.push(n)
//     }

//     return m
//   }, [])
// }
// const array = [1, 1, 1, 1, 1, 1, 2, 2, 3, 4, 5, 5, 6, 7]

//es6 set 方法
1.
const array = [1, 1, 1, 1, 1, 1, 2, 2, 3, 4, 5, 5, 6, 7]
[...new Set(array)]

console.log([...new Set(array)])
2.
function dedupe(array) {
  return Array.from(new Set(array));
}

dedupe([1, 1, 2, 3])

reduce 用法  用list生成对象
  const list = [
        {
          name: '谈话通知书'
        },
        {
          name: '被调查人权利义务告知书'
        },
        {
          name: '谈话笔录'
        }
      ]
      function generatelist(list, frefix) {
        return list.reduce((a, b, c, d) => {
          const key = frefix + `${c}`
          const content = {
            width: 300,
            height: 200,
            shape: 'shape',
            code: key,
            path: 'ssss',
            text: b.name,
            keyPoint: [0, 0],
            lines:
              c + 1 < d.length
                ? [
                    {
                      path: 'y30|x-150|y27',
                      hasArrow: true,
                      next: frefix + `${c + 1}`
                    }
                  ]
                : []
          }
          a[key] = content
          return a
        }, {})
      }
      generatelist(list, 99)
```

##### forEach 和 Map 的区别

- forEach 适合于你并不打算改变数据的时候，而只是想用数据做一些事情 – 比如存入数据库或则打印出来

```js
let arr = ["a", "b", "c", "d"];
arr.forEach(letter => {
  console.log(letter);
});
// a
// b
// c
// d
```

- map()适用于你要改变数据值的时候。不仅仅在于它更快，而且返回一个新的数组。这样的优点在于你可以使用复合(composition)(map(), filter(), reduce()等组合使用)来玩出更多的花样。map()适用于你要改变数据值的时候。不仅仅在于它更快，而且返回一个新的数组。这样的优点在于你可以使用复合(composition)(map(), filter(), reduce()等组合使用)来玩出更多的花样。

```js
let arr = [1, 2, 3, 4, 5];
let arr2 = arr.map(num => num * 2).filter(num => num > 5);
// arr2 = [6, 8, 10]
```

- 核心要点

能用 forEach()做到的，map()同样可以。反过来也是如此。
map()会分配内存空间存储新数组并返回，forEach()不会返回数据。
forEach()允许 callback 更改原始数组的元素。map()返回新的数组。

#### String

##### 字符串的方法

字符串对象共有 4 个方法，可以使用正则表达式：match()、replace()、search()和 split()。

1. spilt(a) 将字符串以 a 分割拆分成数组
2. charAt(数字) 获取字符串对应数字下标的字符
3. join()
4. every()
5. replace() 替换 用法：replace（"要被替换的字符串"，“替换的字符串”），替换原来的字符串不变，返回新的字符串，只会修改第一个匹配的
   **要被替换的字符串可以写成正则表达式**
   **正则表达式//后面可以添加关键字，g 全局匹配，i 字母不区分大小写**
6. match() 获取字符串中符合正则表达式的所有项（数组形式） 用法：Match(regexp)
7. 实例方法：includes(), startsWith(), endsWith()
   -includes()：返回布尔值，表示是否找到了参数字符串。
   -startsWith()：返回布尔值，表示参数字符串是否在原字符串的头部。
   -endsWith()：返回布尔值，表示参数字符串是否在原字符串的尾部。
   这三个方法都支持第二个参数，表示开始搜索的位置。
8. repeat() repeat 方法返回一个新字符串，表示将原字符串重复 n 次。
   参数如果是小数，会被取整。
   如果 repeat 的参数是负数或者 Infinity，会报错。
   但是，如果参数是 0 到-1 之间的小数，则等同于 0，这是因为会先进行取整运算。0 到-1 之间的小数，取整以后等于-0，repeat 视同为 0。
   参数 NaN 等同于 0。
   如果 repeat 的参数是字符串，则会先转换成数字。
9. 实例方法：padStart()，padEnd() ;ES2017 引入了字符串补全长度的功能。如果某个字符串不够指定长度，会在头部或尾部补全。padStart()用于头部补全，padEnd()用于尾部补全。
   padStart()和 padEnd()一共接受两个参数，第一个参数是字符串补全生效的最大长度，第二个参数是用来补全的字符串。
10. 实例方法：trimStart()，trimEnd()
    ES2019 对字符串实例新增了 trimStart()和 trimEnd()这两个方法。它们的行为与 trim()一致，trimStart()消除字符串头部的空格，trimEnd()消除尾部的空格。它们返回的都是新字符串，不会修改原始字符串。
11. matchAll() matchAll()方法返回一个正则表达式在当前字符串的所有匹配

##### 字符串转义

- 反斜杠（\）在字符串内有特殊含义，用来表示一些特殊字符，所以又称为转义符。

```js
\0 ：null（\u0000）
\b ：后退键（\u0008）
\f ：换页符（\u000C）
\n ：换行符（\u000A）
\r ：回车键（\u000D）
\t ：制表符（\u0009）
\v ：垂直制表符（\u000B）
\' ：单引号（\u0027）
\" ：双引号（\u0022）
\\ ：反斜杠（\u005C）
```

#### 数学对象

1. Math.floor(数) 下舍 把括号内的数字进行下舍并返回结果，原数字不会改变
2. Math.ceil(数) 上进
3. Math.round(数) 四舍五入
4. Math.random() 0-1 的随机数
5. Math.max(1,2,3,...) 查找最大值
6. Math.min 查找最小值
7. Math.PI
8. Number.isInteger() Number.isInteger()用来判断一个数值是否为整数。
9. Math.trunc() Math.trunc 方法用于去除一个数的小数部分，返回整数部分。
   对于非数值，Math.trunc 内部使用 Number 方法将其先转为数值。
   对于空值和无法截取整数的值，返回 NaN。
10. Math.sign() 方法用来判断一个数到底是正数、负数、还是零。对于非数值，会先将其转换为数值。 -参数为正数，返回+1； -参数为负数，返回-1； -参数为 0，返回 0； -参数为-0，返回-0; -其他值，返回 NaN。
    `与数值相关的全局方法:`
11. parseInt() parseInt 方法用于将字符串转为整数。
    `parseInt('123') // 123`
12. parseFloat() parseFloat 方法用于将一个字符串转为浮点数。
13. isNaN() isNaN 方法可以用来判断一个值是否为 NaN。
14. isFinite() isFinite 方法返回一个布尔值，表示某个值是否为正常的数值。
    isFinite(Infinity) // false
    isFinite(-Infinity) // false
    isFinite(NaN) // false
    isFinite(undefined) // false
    isFinite(null) // true
    isFinite(-1) // true
    **除了 Infinity、-Infinity、NaN 和 undefined 这几个值会返回 false，isFinite 对于其他的数值都会返回 true。**
15. Number.isInteger() 方法用来判断给定的参数是否为整数。

#### 正则表达式

##### 正则表达式的规则

```js
[0-9] 一位数字
[a-z] 一位小写字母
[A-Z] 一位大写字母
```

#### 数据结构的栈和队列操作

[参考资料](https://www.cnblogs.com/anniey/p/7127872.html)

### 栈

执行上下文就是使用栈

- 栈是一种先进后出的数据结构，比如往筒子里放入羽毛球，想要取出来，必须从最后一个开始。
  数组方法 push()--入栈和 pop()--出栈

### 队列

- 队列是一种先进先出的数据结构，类似排队 办理业务，先到的先办理，后到的后办理。
  `JS为数组提供了方法可以实现队列功能， 入队unshift()、 出队pop()；`

### 闭包的形成需要两个条件

- 在函数内部创建新的函数

- 新的函数在执行时，访问了函数的变量对象

### js 的方法

为 button 元素添加点击事件。 当用户点击按钮时，在 id="demo" 的 p 元素上输出 "Hello World" :

```js
document.getElementById("myBtn").addEventListener("click", function() {
  document.getElementById("demo").innerHTML = "Hello World";
});
```

#### 判断语句之：问号判断

```js
两个条件判断：

enabled == '1'  ?  '是' : '否'

若enabled == '1'成立'是'为真

三个条件判断：

enabled == '1'  ?  '已审核' : enabled == '0'  ? '未审核 ' ： '已锁定'

若enabled == '1'成立'已审核'为真，否则执行 enabled == '0'  ? '未审核 ' ： '已锁定'

```
