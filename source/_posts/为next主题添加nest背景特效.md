---
title: 为next主题添加nest背景特效
date: 2017-03-25 11:32:03
tags: js
categories: hexo
---
背景的几何线条是采用的nest效果，一个基于html5 canvas绘制的网页背景效果，非常赞！来自github的开源项目canvas-nest

### 特性
* 不依赖任何框架或者内库，比如不依赖jQuery，使用原生的javascript。
* 非常小，只有1.66kb，如果开启gzip，可以更小。
* 非常容易实现，配置简单，即使你不是web开发者，也能简单搞定。

### 使用
* 使用非常简单，感觉都没有必要写这一节内容。

#### 修改_layout.swig
打开next/layout/_layout.swig
将下面的代码插入到 <body> 之前.
```
<script type="text/javascript" color="0,0,255" opacity='0.7' zIndex="-2" count="99" src="//cdn.bootcss.com/canvas-nest.js/1.0.0/canvas-nest.min.js"></script>
```
至此，大功告成，运行hexo clean 和 hexo g hexo s之后就可以看到效果了。

<!-- more -->
### 配置和配置项
* color : 线条颜色, 默认: '0,0,0' ；三个数字分别为(R,G,B)，注意用,分割
* opacity : 线条透明度（0~1）, 默认: 0.5
* count : 线条的总数量, 默认: 150
* zIndex : 背景的z-index属性，css属性用于控制所在层的位置, 默认: -1

### 不足
### CPU占用过高

可以看看你现在的Cpu使用率，占用挺高的。

优化方法是减少线条的总数量，但是效果会有点折扣，我使用的是默认的配置。