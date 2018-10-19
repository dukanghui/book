# 小程序代码构成

1. `.json`后缀的`JSON`配置文件
2. `.wxml`后缀的`WXML`模板文件
3. `.wxss`后缀的`WXSS`样式文件
4. `.js`后缀的`JS`脚本逻辑文件

### JSON文件

json文件分为三个

##### 1，项目根目录下的app.json

`app.json`是当前小程序的全局配置，包括了小程序的所有页面路径、界面表现、网络超时时间、底部 tab 等。

刚建的小程序的app.json 如下：

```
{
  "pages":[                              //所有创建的小程序页面都会在里，新建的时候只需在这里按照格式写一下再运行，小程序会自动创建需要的目录
    "pages/index/index",
    "pages/logs/logs"
  ],
  "window":{                            // 定义小程序所有页面的顶部背景颜色，文字颜色定义等。
    "backgroundTextStyle":"light",
    "navigationBarBackgroundColor": "#fff",
    "navigationBarTitleText": "WeChat",
    "navigationBarTextStyle":"black"
  }
}
```

其他配置可以查看[https://developers.weixin.qq.com/miniprogram/dev/framework/config.html](https://developers.weixin.qq.com/miniprogram/dev/framework/config.html)

##### 2，项目根目录下的project.config.json

小程序开发者工具在每个项目的根目录都会生成一个`project.config.json`，你在工具上做的任何配置都会写入到这个文件，当你重新安装工具或者换电脑工作时，你只要载入同一个项目的代码包，开发者工具就自动会帮你恢复到当时你开发项目时的个性化配置，其中会包括编辑器的颜色、代码上传时自动压缩等等一系列选项。

其他配置可以查看[https://developers.weixin.qq.com/miniprogram/dev/devtools/projectconfig.html](https://developers.weixin.qq.com/miniprogram/dev/devtools/projectconfig.html)

##### 3，页面目录下的 .json

开发者可以独立定义每个页面的一些属性，例如刚刚说的顶部颜色、是否允许下拉刷新等等。

其他配置项细节可以参考文档

[https://developers.weixin.qq.com/miniprogram/dev/framework/config.html\#%E9%A1%B5%E9%9D%A2%E9%85%8D%E7%BD%AE](https://developers.weixin.qq.com/miniprogram/dev/framework/config.html#页面配置)

### wxml文件

`WXML`由标签、属性等等构成，是显示页面，作用与html相似。

参考文档：

[https://developers.weixin.qq.com/miniprogram/dev/framework/view/wxml/index.html](https://developers.weixin.qq.com/miniprogram/dev/framework/view/wxml/index.html)



### wxss文件

`WXSS`具有`CSS`大部分的特性，小程序在`WXSS`也做了一些扩充和修改，额外增加了rpx单位，比起px，是自动根据用户设备来变换的，不需要开发者根据不同的屏幕尺寸做计算。

参考文档：

[https://developers.weixin.qq.com/miniprogram/dev/framework/view/wxss.html](https://developers.weixin.qq.com/miniprogram/dev/framework/view/wxss.html)



### JS文件

js文件主要用来实现交互逻辑。数据可以用this.setData\({test: "helle word!"}\)，this代表当前页面实列，微信也提供了丰富的API

,可以在js里边引用。

参考文档：

[https://developers.weixin.qq.com/miniprogram/dev/framework/view/wxml/event.html](https://developers.weixin.qq.com/miniprogram/dev/framework/view/wxml/event.html)

[https://developers.weixin.qq.com/miniprogram/dev/api/network/download/wx.downloadFile.html](https://developers.weixin.qq.com/miniprogram/dev/api/network/download/wx.downloadFile.html)



