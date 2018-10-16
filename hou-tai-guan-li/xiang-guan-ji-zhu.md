#### 本篇介绍项目中用到的相关技术、组件及其使用过程中常遇到的问题的解决方案

# Axios

---

### 简介

Axios 是一个基于 `promise` 的 HTTP 库，可以用在浏览器和 `node.js` 中。

使用说明：[https://www.kancloud.cn/yunye/axios/234845](https://www.kancloud.cn/yunye/axios/234845)

Axios在本项目中的使用：

安装

# mock.js

---

# vuex

---

# scss/less

---

# Element-ui

---

# iconfont

---

# Eslint

---

# js-cookie

---

# Nprogress

---

### 简介 {#h3-4}

进度条库是前端中常见的库之一。NProgress.js是一款轻量级的进度条组件，使用简便。本项目中使用Nprogress，用于页面切换时的页面加载进度显示。

官网：[http://ricostacruz.com/nprogress/](#)

NProgress.js

![](/assets/nprogress.gif)

### 安装 {#h3-4}

main.js或对应js文件中引入[nprogress.js](http://ricostacruz.com/nprogress/nprogress.js)和[nprogress.css](http://ricostacruz.com/nprogress/nprogress.css)到项目中。

```
    import NProgress from 'nprogress'  
    import 'nprogress/nprogress.css'
```

### 基本用法 {#h3-5}

```
    NProgress.start(); 
    NProgress.done();
```

### 更多用法 {#h3-8}

* [https://github.com/rstacruz/nprogress](https://github.com/rstacruz/nprogress)
* [https://www.cnblogs.com/y114113/p/6289629.html](https://www.cnblogs.com/y114113/p/6289629.html)  



