---
title: Rotation chart
date: 2019-02-26 17:42:29
tags:
  - 轮播图
---

## JQ 轮播图

<img src="https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1550593881237&di=76955775ab7b210d91dbe6827fb27c24&imgtype=0&src=http%3A%2F%2Fimg95.699pic.com%2Fphoto%2F50051%2F6573.jpg_wh860.jpg" width="300" hegiht="100"  />

<!-- more -->

```
<!DOCTYPE html>
  <style>
    .lunbo {
      position: relative;
      width: 670px;
      height: 329px;
    }
    .lunbo img {
      position: absolute;
      opacity: 0;
      transition: all 0.75s;
    }
    .lunbo .active {
      opacity: 1;
      z-index: 1;
    }
    .list {
      cursor: pointer;
      position: absolute;
      z-index: 2;
      display: flex;
      bottom: 0;
      left: 50%;
      margin-left: -100px;
    }
    .list li {
      list-style: none;
      width: 40px;
      line-height: 40px;
      border-radius: 50%;
      background-color: pink;
      text-align: center;
      color: #fff;
      transition: all 0.75s;
    }
    .list .change {
      background-color: #fff;
      color: #000;
    }
    button {
      position: absolute;
      z-index: 3;
      top: 50%;
      width: 40px;
      height: 40px;
    }
    .right {
      right: 0;
    }
  </style>
  <body>
    <div class="lunbo">
      <img src="./images/gracetan_01.jpg" alt="" class="active" />
      <img src="./images/gracetan_02.jpg" alt="" />
      <img src="./images/gracetan_03.jpg" alt="" />
      <img src="./images/gracetan_04.jpg" alt="" />
      <ul class="list">
        <li class="change">1</li>
        <li>2</li>
        <li>3</li>
        <li>4</li>
      </ul>
      <button class="left"><</button>
      <button class="right">></button>
    </div>
    <script src="https://cdn.bootcss.com/jquery/3.3.1/jquery.min.js"></script>
    <script>
      let fun = 0
      $('.btn').click(function() {
        console.log(1)
        if (fun === 0) {
          fun = 1
          $('.box').css({ 'background-color': 'brown' })
        } else {
          fun = 0
          $('.box').css({ 'background-color': 'pink' })
        }
      })
      $('li').click(function() {
        const ind = $(this).index()
        num = ind
        $(this)
          .parent()
          .siblings()
          .eq(ind)
          .addClass('active')
          .siblings()
          .removeClass('active')
        $(this)
          .parent()
          .children()
          .eq(ind)
          .addClass('change')
          .siblings()
          .removeClass('change')
      })
      let num = 0
      let imgNum = $('img').length
      $('.right').click(function() {
        num = num + 1
        if (num > imgNum - 1) {
          num = 0
        }
        $(this)
          .parent()
          .find('img')
          .eq(num)
          .addClass('active')
          .siblings()
          .removeClass('active')
        $(this)
          .parent()
          .find('ul')
          .children()
          .eq(num)
          .addClass('change')
          .siblings()
          .removeClass('change')
      })
      $('.left').click(function() {
        num = num - 1
        if (num < 0) {
          num = imgNum - 1
        }
        $(this)
          .parent()
          .find('img')
          .eq(num)
          .addClass('active')
          .siblings()
          .removeClass('active')
        $(this)
          .parent()
          .find('ul')
          .children()
          .eq(num)
          .addClass('change')
          .siblings()
          .removeClass('change')
      })
      var stop = null
      function run() {
        stop = setInterval(function() {
          num = num + 1
          if (num > imgNum - 1) {
            num = 0
          }
          $('img')
            .eq(num)
            .addClass('active')
            .siblings()
            .removeClass('active')
          $('li')
            .eq(num)
            .addClass('change')
            .siblings()
            .removeClass('change')
        }, 1000)
      }
      run()
      $('.lunbo').mouseenter(function() {
        clearInterval(stop)
      })
      $('.lunbo').mouseleave(function() {
        run()
      })
    </script>
  </body>
</html>
```
