---
title: hello
date: 2017-03-24 17:45:49
tags:
---

## Reactnews头条新闻，兼容pc端和移动端

### 项目技术架构
* React
* React-router
* React-responsive
* ant-design
* fetch
* webpack

### 安装预览

* 安装相关依赖包
  ```
  npm install
  ```

  
* 启动服务

  ```
  webpack-dev-server --contentbase src --inline --hot
  ```

* 目录结构
***
<pre>
├── node_modules         // 项目相关依赖包
├── index.html           // 项目入口文件
├── package.json         // 项目配置文件
├── src                  // 生产目录
│  ├── images            // 图片资源
│  ├── css               // 公共的css 资源
│  ├── js                // 公共的js 资源
│     ├── components     // 各种组件
      ├── root.js        //主界面
│  └── bundle.js         // Webpack 预编译入口
</pre>


### 实现的功能
* 注册/登陆
* 新闻详情页
* 个人中心
* 收藏列表
* 评论中心