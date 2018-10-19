# 小程序app.json 配置

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

### 获取用户信息wx.getUserInfo

##### 1,直接在小程序JS调用

```
wx.getUserInfo({
            success: function(res) {
              console.log(res)
            }
          })
```



