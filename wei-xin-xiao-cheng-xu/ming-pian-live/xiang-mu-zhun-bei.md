# 申请账号

点击[https://mp.weixin.qq.com/wxopen/waregister?action=step1](/ https://mp.weixin.qq.com/wxopen/waregister?action=step1)根据指引填写信息和提交相应的资料，就可以拥有自己的小程序帐号。![](/assets/1539823971%281%29.png)登录[https://mp.weixin.qq.com](https://mp.weixin.qq.com)，我们可以在菜单 “设置”-“开发设置” 看到小程序的**AppID和AppSecret**了 。

**AppSecret**生成以后要妥善保管，虽然可以重置，有时候后台需要**AppSecret**来解密，所以要是改了需要跟后台沟通。![](/assets/2018-10-18_0905161.png)

# **开发者工具下载**

打开[https://developers.weixin.qq.com/miniprogram/dev/devtools/download.html?t=18101520](https://developers.weixin.qq.com/miniprogram/dev/devtools/download.html?t=18101520)根据自己系统下载安装

# 安装开发工具

1, 新建一个空文件

2，打开开发者工具，选择刚建的空白文件

3，输入AppID

4，填写小程序名称

5，选择建立快速普通启动模板（注意：只有空白文件才有这选项）

![](/assets/2018-10-18_193150.png)

这样就建立了简单的第一个小程序

![](/assets/2018-10-18_195352.png)

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

[https://developers.weixin.qq.com/miniprogram/dev/api/network/download/wx.downloadFile.htm](https://developers.weixin.qq.com/miniprogram/dev/api/network/download/wx.downloadFile.html)

# 小程序启动

微信客户端在打开小程序之前，会把整个小程序的代码包下载到本地。

然后通过app.json的pages，加载第一个页面为首页

```
"pages": [                         // 这里pages/mine/mine 为首页
    "pages/mine/mine",    
    "pages/findmore/findmore",
    "pages/otherpeers/otherpeers"
  ],
```

## 相关文档 {#_5}

* [https://developers.weixin.qq.com/miniprogram/dev/component/](https://developers.weixin.qq.com/miniprogram/dev/component/)
* [https://developers.weixin.qq.com/miniprogram/dev/](https://developers.weixin.qq.com/miniprogram/dev/)



