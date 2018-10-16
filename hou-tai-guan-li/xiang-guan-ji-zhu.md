#### 本篇介绍项目中用到的相关技术、组件及其使用过程中常遇到的问题的解决方案

# Axios

---

### 简介

Axios 是一个基于 `promise` 的 HTTP 库，可以用在浏览器和 `node.js` 中。

使用说明：[https://www.kancloud.cn/yunye/axios/234845](https://www.kancloud.cn/yunye/axios/234845)

Axios在本项目中的使用：

### 安装

使用 npm:

```
npm install axios
```

使用 cdn:

```
<script src="https://unpkg.com/axios/dist/axios.min.js"></script>
```

### 基本用法

下面介绍axios在本项目中的使用方式

utils文件夹下request.js

```
import axios from 'axios'  // 引入
const service = axios.create({
  baseURL: 'http://domain.name.com/project',   // 后台接口域名
  timeout: 5000
})
```

请求拦截，设置每个请求头携带headers用于登录验证及登录状态判断

```
service.interceptors.request.use(
  config => {
    if (store.getters.token) {
      config.headers['Authorization'] = getToken()
    }
    config.headers['Accept'] = '*, *'
    return config
  },
  error => {
    Promise.reject(error)
  }
)
```

响应拦截，判断响应数据状态码，给出对应提示信息

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

使用 npm:

```
npm install nprogress
```

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
  ### 



