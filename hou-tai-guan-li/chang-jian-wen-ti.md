# 打包

打包后可能会发现css及js文件404 \(Not Found\)

config/index.js默认配置如下：

![](/assets/config-build.png)

build对象需改为：

```
assetsPublicPath: './'
```

# 语法检查

严格的语法检查可能会使你感到不适

当你少了一个空格、多了一个空行、没有严格对齐，引入变量没有使用

eslint将禁止你的程序继续运行除非你解决这些语法格式问题

可做如下配置，让eslint给你提出警告而不是终止程序

![](/assets/eslint.png)

#### 部分文件\(代码\)忽略语法检查

当你热衷于使用eslint的错误提示，可以不做以上设置

但是当引入外部打包后的js文件/插件，eslint此时仍然会让你的项目不能正常运行

此时需要在你需要忽略语法检查的文件或者代码的最上面加上此行代码

```
/* eslint-disable */
```



