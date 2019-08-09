---
title: scroll
date: 2019-08-09 08:59:21
tags:
---

## 获取滚动条的位置

### 在 VUE 中获取滚动条的位置存到 sessionStorage 中，刷新页面从 sessionStorage 中取出来

<!-- more -->

```js
  mounted() {
    // right 是自己写的dom节点的名字
    this.$refs.right.addEventListener("scroll", this.handleScroll, true);
    if (this.$route.path === "/safe/lien/system/41") {
      this.$refs.right.scrollTo(0, (sessionStorage.safeLienSystem = 0), true);
    } else {
      this.$refs.right.scrollTo(0, sessionStorage.safeLienSystem, true);
    }
  },
  methods: {
    handleScroll(e) {
      sessionStorage.safeLienSystem = e.target.scrollTop;
    }
  }
```
