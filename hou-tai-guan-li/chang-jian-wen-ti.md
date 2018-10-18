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

