# 小程序app.json 配置

---

```
{
  "pages": [                               // 小程序所有页面定义
    "pages/mine/mine",                     // 第一个是首页
    "pages/findmore/findmore",
    "pages/otherpeers/otherpeers",
    "pages/peerscards/peerscards",
    "pages/addcards/addcards",
    "pages/mycards/mycards",
    "pages/ganerate/ganerate",
    "pages/company/company",
    "pages/quncards/quncards",
    "pages/inputSearch/inputSearch",
    "pages/fix/fix",
    "pages/teampeers/teampeers",
    "pages/industry/industry",
    "pages/findUs/findUs",
    "pages/searchInGroup/searchInGroup",
    "pages/cutImg/cutImg",
    "pages/webGezhi/webGezhi"
  ],
  "window": {                                  // 页面配置
    "backgroundTextStyle": "light",            // 下拉loading的样式（只支持dark / light）
    "navigationBarTitleText": "名片Live",      // 顶部栏文字（每个页面不单独设置的话默认是 名片Live）
    "navigationBarBackgroundColor": "#2C7FE7", // 顶部栏背景颜色
    "navigationBarTextStyle": "white"          // 顶部栏文字颜色（只支持 black/white）
  },
  "tabBar": {                                  // 底部导航栏
    "color": "#949494",                        // 底部导航栏默认颜色
    "selectedColor": "#2C7FE7",                // 底部导航栏选择时的颜色
    "backgroundColor": "#ffffff",              // 底部导航栏背景颜色
    "borderStyle": "#D8D8D8",                  // 底部导航栏上面的线
    "list": [                                  // 底部导航栏集合（只能2~5个）
      {
        "pagePath": "pages/findmore/findmore",  // 底部导航栏页面路径
        "text": "名片夹",                        // 底部导航栏名字
        "iconPath": "pages/images/menu_1.png",  // 没有选择时的图片
        "selectedIconPath": "pages/images/menu_1_active.png" // 选择时的图片
      },
      {
        "pagePath": "pages/quncards/quncards",
        "text": "群名片",
        "iconPath": "pages/images/menu_2.png",
        "selectedIconPath": "pages/images/menu_2_active.png"
      },
      {
        "pagePath": "pages/mine/mine",
        "text": "我的",
        "iconPath": "pages/images/menu_3.png",
        "selectedIconPath": "pages/images/menu_3_active.png"
      }
    ]
  }
}
```

# 小程序App.js配置

---

```
App({                               // 小程序实列
  globalData: {                     // 小程序全局变量集合
    log:[]          
  },
  onLaunch: function(ops) {         // 小程序加载时运行的函数 可以在ops里获取到一些参数（用户场景值，群参数等等）
    // 逻辑
  },
  onShow: function(ops) {           // 页面刷新函数（有一些函数是在 onlaunch 获取不到的可以在这里处理）
    // 逻辑
  }
})
```

# 小程序project.config.json配置

---

```
{
    "description": "项目配置文件。",
    "packOptions": {                                  // 打包项目配置项
        "ignore": []
    },
    "setting": {                                      // 项目配置
        "urlCheck": true,                             // 检查安全域名和 TLS 版本(打开的时候会验证服务器名是否可用，本地调试可以关)
        "es6": true,                                  // 启用es6 转 es5
        "postcss": true,                              // 上传代码时样式自动补全
        "minified": true,                             // 上传代码时自动压缩
        "newFeature": true
    },
    "compileType": "miniprogram",                     // 编译类型（小程序）
    "libVersion": "2.2.3",                            // 版本基础库（用户版本低于基础库 会提示更新微信）
    "appid": "",                                      
    "projectname": "%E5%90%8D%E7%89%87Live",          // 项目名称
    "isGameTourist": false,
    "condition": {
        "search": {
            "current": -1,
            "list": []
        },
        "conversation": {
            "current": -1,
            "list": []
        },
        "plugin": {
            "current": -1,
            "list": []
        },
        "game": {
            "currentL": -1,
            "list": []
        },
        "miniprogram": {
            "current": 0,
            "list": [                         // 自定义打开小程序页面（调试）
                {
                    "id": 0,
                    "name": "peerscards",
                    "pathName": "pages/company/company",
                    "query": "othercardid=76",
                    "scene": "1001"
                }
            ]
        }
    }
}
```

# 用到的API整理

---

* ### 获取用户信息wx.getUserInfo

##### 直接在小程序JS调用（只能获取已经授权过的用户信息，没有授过权就跳过）

```
wx.getUserInfo({
     success: function(res) {
         console.log(res)
     }
})
// 返回值res
 {errMsg: "getUserInfo:ok", rawData: "{"nickName":"😂😂😂😂😂😂😂😂","gender":1,"languag…fBvkVhEiapJSFiagpibXlr9dlnLCtGjbhv31BVMuRUg/132"}", userInfo: {…}, signature: "abeadd633f84ba29c8d461fe95ef67993820931f", encryptedData: "OGfWACsNLNFSAXrvD1wseEgEJFGnKP3WxvUzMrTde1n9v54hSr…QuLu5tyKBeaUHiRo1C0mRuq5yTKD7BcwCsYIH+XkA6H3fB8cr", …}
encryptedData:"OGfWACsNLNFSAXrvD1wseEgEJFGnKP3WxvUzMrTde1n9v54hSrChK3l8RrNpM7usGisTrmXkZD52f0Ga7hsHfU1BPP3/dCBMju8awSDyQFP4Dr8j8xC9WRVlGMKDt+EaA7Oar05DfH/frjej9JJKdwJrAr4jhnJmJONleJxLJWnJ7XdTSXT+Opu7eG6izorRMQdHKK1w70UtfZIDClUD9jXJMNm/CGEVxtMKgmGVxhdVt5QgKfdcuXXPTWhHAdP7+Gmz1KFGi9p9g1f3fpN1tUcHZanKbJLyipofyuJYJCMJU2pAqCcN3mvnObnGAYPd8hwef9KPRRu1M6feHcs39aM9VR43vKF+qYzXVeAnKRZGhorYdoXHuNsrJ4JyYdhdhalo7ArA2t+kS8chq2+ZIIQ5qgmzRB+WfCgg+oqG1pq2MzelrdAZDHRSDwSVFr758nq2Qr7zkLyQmWDQuLu5tyKBeaUHiRo1C0mRuq5yTKD7BcwCsYIH+XkA6H3fB8cr"
errMsg:"getUserInfo:ok"
iv:"3cdUvgDwzhm3JW8v/u2K8w=="
rawData:
"{"nickName":"😂😂😂😂😂😂😂😂","gender":1,"language":"zh_CN","city":"Fangshan","province":"Beijing","country":"China","avatarUrl":"https://wx.qlogo.cn/mmopen/vi_32/Q0j4TwGTfTL50AV50HChZskh80HxCDBNS0WiaBx3MibBFE19fBvkVhEiapJSFiagpibXlr9dlnLCtGjbhv31BVMuRUg/132"}"
signature:"abeadd633f84ba29c8d461fe95ef67993820931f"
userInfo:{nickName: "😂😂😂😂😂😂😂😂", gender: 1, language: "zh_CN", city: "Fangshan", province: "Beijing", …}
```

* ### 用户信息授权确认button组件

需要在wxml页面里写

```
<button class='btn' open-type="getUserInfo" bindgetuserinfo='addcards'>制作我的名片</button>
// open-type = "getUserInfo" bindgetuserinfo 只能用这个方法才有返回值 bindtap等等不能获取
这两个是必须的
```

JS里写上

```
addcards: function(e) {
    if (e.detail.userInfo) {
        // 用户点击确定按钮 以后的逻辑处理
    } else {
        // 用户点击取消按钮 以后的逻辑处理
    }
  }
```

* ### 页面跳转方法
* ##### wx.switchTab\({url: ""}\) 只能跳转到Tab页面（定义的TabBar页面）

跳转到 tabBar 页面，并关闭其他所有非 tabBar 页面

```
// app.json
{
  "tabBar": {
    "list": [{
      "pagePath": "index",
      "text": "首页"
    },{
      "pagePath": "other",
      "text": "其他"
    }]
  }
}
// 对应的JS文件
wx.switchTab({
  url: '/index'    // 必须是tabbar对应的页面（路径可以是相对路径，可以是绝对路径）
})
```

##### 2,wx.redirectTo\({url: ""}\)

关闭当前页面，跳转到应用内的某个页面，但是不允许跳转到 tabbar 页面。

```
wx.redirectTo({
  url: '/index'    // 必须是非tabbar对应的页面（路径可以是相对路径，可以是绝对路径）
})
```

##### 3,wx.reLaunch\({url: ""}\)

关闭所有页面，打开到应用内的某个页面

```
wx.reLaunch({
  url: '/index'    // 必须是非tabbar对应的页面（路径可以是相对路径，可以是绝对路径）
})
```

##### 4,wx.navigateTo\({url: ""}\)

保留当前页面，跳转到应用内的某个页面，但是不能跳到 tabbar 页面。使用[wx.navigateBack](https://developers.weixin.qq.com/miniprogram/dev/api/route/wx.navigateBack.html)可以返回到原页面。

```
wx.navigateTo({
  url: '/index'    // 必须是非tabbar对应的页面（路径可以是相对路径，可以是绝对路径）
})
```

##### 5,wx.navigateBack\({url: ""}\)

关闭当前页面，返回上一页面或多级页面。可通过[getCurrentPages\(\)](https://developers.weixin.qq.com/miniprogram/dev/framework/app-service/route.html#getcurrentpages)获取当前的页面栈，决定需要返回几层。

```
wx.navigateBack({
    delta: 2           // delta必须是整数 后退几个页面
})
```

* ### 分享小程序
* ##### 使用button组件（点击转发）

通过给`button`组件设置属性`open-type="share"`，可以在用户点击按钮后触发[`Page.onShareAppMessage`](https://developers.weixin.qq.com/miniprogram/dev/framework/app-service/page.html#onshareappmessageobject)事件，如果当前页面没有定义此事件，则点击后无效果。

```
// wxml 文件里写
<button class="footer-btn" open-type='share'>发送本张名片</button>


// 对应的JS文件里
onload(){
  wx.showShareMenu({                         // 这个可以不用写（写了这个，用户转发到群的时候会携带ShareTicket，开发者可以用来获取群ID）
      withShareTicket: true
  })
},
onShareAppMessage: function (a) {
    let that = this
    return {
      title: '我的名片信息',                                    // 转发的标题
      path: '/pages/peerscards/peerscards?othercardid=' + that.data.id, // 转发后点击进来的页面
      imageUrl: 'images/test.png',                          // 自定义转发图片（宽高比例是5:4）,不选择是默认选择当前页面的80%大小的截图
      success: function (res) {
        console.log(res)
      },
      fail: function (res) {
        console.log(res)
      }
    }
  }
```

##### 2. 右上角菜单的转发

```
// 对应的JS文件里
onload(){
  wx.showShareMenu({           // 这个可以不用写（写了这个，用户转发到群的时候会携带ShareTicket，开发者可以用来获取群ID）
      withShareTicket: true
  })
},
onShareAppMessage: function (a) {
    let that = this
    return {
      title: '我的名片信息',                                    // 转发的标题
      path: '/pages/peerscards/peerscards?othercardid=' + that.data.id, // 转发后点击进来的页面
      imageUrl: 'images/test.png',                          // 自定义转发图片（宽高比例是5:4）,不选择是默认选择当前页面的80%大小的截图
      success: function (res) {
        console.log(res)
      },
      fail: function (res) {
        console.log(res)
      }
      }
```

* ### 打开另一个小程序

```
// JS文件里
wx.navigateToMiniProgram({
    appId: "",                  // 目标小程序appid
    path: ""                    // 目标小程序页面路径，默认首页
})
```

或者

```
<navigator target="miniProgram" open-type="navigate" app-id="" path="" extra-data="" version="release">打开绑定的小程序</navigator>
```

* ### 小程序热更新

小程序的app.js的onShow里写

```
onShow (){
const updateManager = wx.getUpdateManager()
    updateManager.onCheckForUpdate(function(res) {
      // 请求完新版本信息的回调
      console.log(res.hasUpdate)
    })
    updateManager.onUpdateReady(function() {
      wx.showModal({
        title: '更新提示',
        content: '新版本已经准备好，是否重启应用？',
        success: function(res) {
          if (res.confirm) {
            // 新的版本已经下载好，调用 applyUpdate 应用新版本并重启
            updateManager.applyUpdate()
          }
        }
      })
    })
    updateManager.onUpdateFailed(function() {
      // 新的版本下载失败
      wx.showModal({
        title: '更新提示',
        content: '新版本下载失败',
        showCancel: false
      })
    })
}
```

* ### 跳转到h5

web-view 组件是一个可以用来承载网页的容器，会自动铺满整个小程序页面。个人类型与海外类型的小程序暂不支持使用。

```
<web-view src="https://mp.weixin.qq.com/"></web-view>
// src webview 指向网页的链接。可打开关联的公众号的文章,其它网页需登录小程序管理后台配置业务域名。
```



