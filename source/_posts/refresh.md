---
title: 记录Window搭建hexo博客过程
tags: js
date: 2019-02-19 0:07
categories: js, 前端
---
***
```
"那少年，和当初被人们嘲笑时那样，不卑不亢。胜不骄，败不馁，如冰川一般纹丝不动。
```
**js原生下拉刷新**
#### 思路

1.主要在于js的touchstart,touchmove,touchend三个方法，通过dom上js的addEventListener监听这三个方法，touchstart的时候记录初始触摸位置，touchmove记录滑动位置并添加dom的css属性transition,transform。touchend的时候给transform重新设置，并且将位置恢复为0

2.如果显示下拉刷新，则在touchmove的时候通过css属性innerText添加文字。

3.解释transition属性：
```
transition 属性是一个简写属性，用于设置四个过渡属性：
    transition-property ： 规定设置过渡效果的 CSS 属性的名称
    transition-duration ： 规定完成过渡效果需要多少秒或毫秒。
    transition-timing-function ： 	规定速度效果的速度曲线(linear->匀速，ease->慢快慢，ease-in->慢速开始，ease-out->慢速结束)。
    transition-delay ：定义过渡效果何时开始。
```
<!--more-->
4.transform属性：
```
transform 属性向元素应用 2D 或 3D 转换。该属性允许我们对元素进行旋转、缩放、移动或倾斜。

transform: translateY(60px)   移动60像素的距离
transform: rotate(45deg)  旋转角度
```

5.代码如下
```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>下拉刷新</title>
  <style type="text/css">
    html,body,p{
      margin:0;
      padding:0;
    }
    .main{
      text-align:center;
      position: relative;
    }
    .refreshMain{
      width:100%;
      height:100vh;
      background: lightgray;
    }
    .refreshText{
      position: absolute;
      width: 100%;
      line-height: 50px;
      text-align: center;
      left: 0;
      top: 0;
    }
  </style>
</head>
<body>
  <div class="main">
    <p class="refreshText"></p>
    <div class="refreshMain">

    </div>
  </div>

</body>
</html>
<script type="text/javascript">
  var dom = document.getElementsByClassName('refreshMain')[0];
  var refreshText = document.getElementsByClassName('refreshText')[0];
  var startHeight;
  var moveHeight;
  var endHeight;
  <!-- 记录开始滑动的初始位置 -->
  dom.addEventListener('touchstart',function(e){
    startHeight = e.touches[0].pageY
    dom.style.position = "relative"
    dom.style.transition = "transform 0s"
    refreshText.innerText = ""
  })
  <!-- 滑动中 -->
  dom.addEventListener('touchmove',function(e){
    moveHeight = e.touches[0].pageY - startHeight
    dom.style.transform = `translateY(${moveHeight}px)`
    refreshText.innerText = "下拉刷新"
    if(moveHeight > 60){
      refreshText.innerText = "释放刷新"
    }
  })
  dom.addEventListener('touchend',function(e){
      dom.style.transition = "transform 0.5s ease 0.5s"
      dom.style.transform = "translateY(60px)"
      refreshText.innerText = "更新中..."
      setTimeout(function(){
        refreshText.innerText = "更新成功"
        dom.style.transform = "translateY(0px)"
      },3000)
  })
</script>

```