# 项目简介 {#简介}

* 棱镜测试后台管理系统使用`vue`前端框架开发

* 开发过程使用vue-cli脚手架构建工具

* 对题目、答案、轮播图等信息的维护

* 避免开发人员直接操作数据库

## [Vue.js 是什么](https://cn.vuejs.org/v2/guide/#Vue-js-是什么) {#Vue-js-是什么}

---

Vue \(读音 /vjuː/，类似于**view**\) 是一套用于构建用户界面的**渐进式框架**。与其它大型框架不同的是，Vue 被设计为可以自底向上逐层应用。Vue 的核心库只关注视图层，不仅易于上手，还便于与第三方库或既有项目整合。另一方面，当与[现代化的工具链](https://cn.vuejs.org/v2/guide/single-file-components.html)以及各种[支持类库](https://github.com/vuejs/awesome-vue#libraries--plugins)结合使用时，Vue 也完全能够为复杂的单页应用提供驱动。

## [vue-cli](https://blog.csdn.net/qq_35574915/article/details/76060997)

---

`vue-cli` 是`vue.js`的脚手架，用于自动生成`vue.js+webpack`的项目模板，分为vue init webpack-simple 项目名 和vue init webpack 项目名 两种。

当然首先你的安装`vue`,`node`, `(webpack)`等一些必要的环境

# 生成项目

1. 需要安装node环境  
   node下载地址：推荐下载LTS\(长期支持版本\)版本  
   [https://nodejs.org/en/](https://nodejs.org/en/)  
   [https://nodejs.org/en/download/](https://nodejs.org/en/download/)  
   你可以根据不同平台系统选择你需要的Node.js安装包。

2. 安装vue-cli  
   如果不确定自己是否安装了node,可以在命令行工具内执行： `node -v`  \(检查版本\)  
   ![](/assets/import.png)  
   vue-cli 全局安装  
   请在终端命令行执行 `npm install -g vue-cli`    // 加-g是安装到全局

3. 初始化项目  
   执行命令：`vue init webpack demo`\(你新建的项目名称/文件名称\)  
   执行之后将会 自动初始化一个文件夹 ：`demo`

4. 启动项目  
   `cd demo`  
   `npm install`  
   `npm run dev`

5. 注意事项

   1. 以上步骤为创建新的vue-cli项目步骤，如果您手上有完整的**项目文件**或者您对vue-cli有一定了解，可忽略
   2. npm install 如安装失败 或者其他诡异



