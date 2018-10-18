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

全局的响应拦截可以避免每个接口中做判断，提高代码复用性

```
service.interceptors.response.use(response => {
  let data = response.data
  // 处理接口数据格式不正确
  if (response.config.direct) {
    return data
  }
  if (response.data.code === 401) {
    MessageBox.confirm('你已被登出，可以取消继续留在该页面，或者重新登录', '确定登出', {
      confirmButtonText: '重新登录',
      cancelButtonText: '取消',
      type: 'warning'
    }).then(() => {
      store.dispatch('FedLogOut').then(() => {
        location.reload()
      })
    })
  }
  // 判断错误信息
  if (response.data.code && response.data.code !== 200 && response.data.code !== 1) {
    let message = data.msg
    let str = '网络出现波动，请稍后重试'
    if (typeof message === 'string') {
      str = message
    }
    Message.closeAll()
    Message({
      message: str,
      type: 'warning',
      duration: 1200
    })
  }
  return data
}, error => {
  Message({
    message: error.message,
    type: 'error',
    duration: 1000
  })
  return Promise.reject(error)
})
export default service
```

全局http请求封装`get、post、put、delete`方法 \(utils文件夹下`http.js`文件\)

```
import axios from './request'
const online = {
  get (url, data) {
    return axios.get(url, {params: data})
  },
  post (url, data) {
    return axios.post(url, data)
  },
  put (url, data) {
    return axios.put(url, data)
  },
  delete (url, data) {
    return axios.delete(url, {params: data})
  }
}
export default online
```

接口函数封装 \(src/api文件夹下`index.js`文件\)

`qs`用于部分`post`接口请求参数封装

```
import http from '@/utils/http'
import qs from 'qs'

export function systemLogin (query) {
  return http.post('/login', query)
}

export function deleteSowingmapByStatus (query) {
  return http.put('/sowingmap/deleteSowingmapByStatus', qs.stringify(query))
}
```

以获取系统日志为例 `systemLog.vue` 文件

```
import { querysystemlog } from '@/api/index'
export default {
  data () {
    return {
      total: 0,
      pageNum: 1,
      pageSize: 10,
      tableData: []
    }
  },
  mounted () {
    this.getData()
  },
  methods: {
    getData () {
      querysystemlog({
        pageNum: this.pageNum,
        pageSize: this.pageSize
      }).then(res => {
        this.tableData = res.data.result
        this.total = res.data.total
      })
    }
  }
}
```

tips：推荐使用箭头函数，使代码更加简洁

# mock.js

---

### 简介

生成随机数据，拦截 Ajax 请求

* **前后端分离** 让前端攻城师独立于后端进行开发。
* **增加单元测试的真实性** 通过随机数据，模拟各种场景。
* **开发无侵入** 不需要修改既有代码，就可以拦截 Ajax 请求，返回模拟的响应数据。
* **用法简单** 符合直觉的接口。
* **数据类型丰富** 支持生成随机的文本、数字、布尔值、日期、邮箱、链接、图片、颜色等。
* **方便扩展** 支持支持扩展更多数据类型，支持自定义函数和正则。

### 安装 {#h3-4}

使用 npm:

```
npm install mock.js
```

main.js或对应js文件中引入`mock.js`到项目中。

```
import Mock from 'mockjs'
Mock.mock(/\/getSystemLog/, 'get', mainAPI.getSystemLog)
```

### 基本用法 {#h3-5}

```
import mainAPI from './main'
Mock.mock(/\/getSystemLog/, 'get', mainAPI.getSystemLog)
```

### 更多用法 {#h3-8}

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



