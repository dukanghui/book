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
    "list": [                                  // 底部导航栏集合（2~5个）
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



