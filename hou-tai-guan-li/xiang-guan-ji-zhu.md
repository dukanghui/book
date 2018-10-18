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

```
├─src
│  ├─api                    
│  │ ├─index.js    
│  ├─utils
│  │ ├─index.js     
│  │ ├─request.js
```

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

目录

```
├─src
│  ├─mock                     
│  │  ├─index.js   
│  │  ├─main.js       
│  ├─main.js
```

新建mock文件夹及对应js文件并在src/main.js中引入。

```
import './mock'
```

### 基本用法 {#h3-5}

```
// mock/index.js
import Mock from 'mockjs'
import mainAPI from './main'
Mock.mock(/\/getSystemLog/, 'get', mainAPI.getSystemLog)
export default Mock
```

```
// mock/main.js
import Mock from 'mockjs'
const result = []
for (let i = 0; i < 10; i++) {
  result.push(Mock.mock({
    id: '@increment',
    name: '@first',
    num: '@integer(1, 1000)',
    time: '@datetime',
    title: '@title(2, 4)',
    'state|1': ['true', 'false'],
    image_uri,
    parentAlgoName: '@integer(1, 3)',
    childAlgoName: '@integer(1, 2)',
    userName: 'superadmin',
    createTime: '@datetime',
    'handle|1': ['登录', '修改结果', '添加轮播图']
  }))
}
export default {
  getSystemLog: () => ({
    data: {
      pageIndex: 1,
      total: result.length,
      result: result
    }
  })
}
```

##### tips

* mock.js常用场景为后台接口不存在或者需等待
* 当不需要mock.js时，需注释src/main.js中的导入代码

# vuex

---

### 简介 {#h3-4}

##### 官方定义：

Vuex 是一个专为 Vue.js 应用程序开发的状态管理模式。它采用集中式存储管理应用的所有组件的状态，并以相应的规则保证状态以一种可预测的方式发生变化。

##### 什么情况下我应该使用 Vuex？

* 如果您不打算开发大型单页应用，使用 Vuex 可能是繁琐冗余的。
* 确实是如此——如果您的应用够简单，您最好不要使用 Vuex。
* 一个简单的[store 模式](https://cn.vuejs.org/v2/guide/state-management.html#简单状态管理起步使用)就足够您所需了。
* 但是，如果您需要构建一个中大型单页应用，您很可能会考虑如何更好地在组件外部管理状态，Vuex 将会成为自然而然的选择。

当通信双方不是父子组件甚至压根不存在相关联系，或者一个状态需要共享给多个组件时，就会非常麻烦，数据也会相当难维护，这对我们开发来讲就很不友好。`vuex`应运而生。

引用 Redux 的作者 Dan Abramov 的话说就是：

###### Flux 架构就像眼镜：您自会知道什么时候需要它。

### 安装 {#h3-4}

使用 npm:

```
npm install vuex
```

### 基本用法 {#h3-5}

目录

```
├─src
│  ├─store   
│  │  ├─modules
│  │  │  ├─user.js               
│  │  ├─getters.js   
│  │  ├─index.js       
│  ├─main.js
```

main.js引入

```
import store from './store'
new Vue({
  el: '#app',
  router,
  store,
  components: { App },
  template: '<App/>'
})
```

store/index.js文件

```
import Vue from 'vue'
import Vuex from 'vuex'
import getters from './getters'
import user from './modules/user'

Vue.use(Vuex)

const store = new Vuex.Store({
  modules: {
    user
  },
  getters
})

export default store
```

store/getters.js用于获取vuex中的数据，也可以用this.$store.state.obj来获取

```
const getters = {
  token: state => state.user.token
}
export default getters
```

tips：vuex中的数据刷新页面会丢失，可以配合cookie或者localstorage/sessionstorage来使用

本项目中使用vuex配合js-cookie存储token

# scss/less

---

Sass 是一款强化 CSS 的辅助工具，它在 CSS 语法的基础上增加了变量 \(variables\)、嵌套 \(nested rules\)、混合 \(mixins\)、导入 \(inline imports\) 等高级功能，这些拓展令 CSS 更加强大与优雅。使用 Sass 以及 Sass 的样式库（如[Compass](http://compass-style.org/)）有助于更好地组织管理样式文件，以及更高效地开发项目。

当项目中有引用scss文件，npm run dev 可能会出错，需要先下载引入sass

`npm install node-sass sass-loader --save-dev --registry=https://registry.npm.taobao.org`

# Element-ui

---

element-ui是饿了么前端团队推出的一款桌面端的UI框架，配合vue使用能够大大加快后台管理系统的开发速度。

官网：[http://element-cn.eleme.io/\#/zh-CN/component/installation](http://element-cn.eleme.io/#/zh-CN/component/installation)

## 安装 {#an-zhuang}

### npm 安装 {#npm-an-zhuang}

推荐使用 npm 的方式安装，它能更好地和[webpack](https://webpack.js.org/)打包工具配合使用。

```
npm i element-ui -S
```

### 基本用法 {#h3-5}

```
import Element from 'element-ui'
import 'element-ui/lib/theme-chalk/index.css'
Vue.use(Element)
```

# iconfont

---

# 

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



