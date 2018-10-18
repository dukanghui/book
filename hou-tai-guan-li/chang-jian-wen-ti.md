# 打包

打包后可能会发现css及js文件404 \(Not Found\)

config/index.js默认配置如下：

![](/assets/config-build.png)

build对象需改为：

```
assetsPublicPath: './'
```

# 语法检查



