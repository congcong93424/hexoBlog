---
title: 原生js上拉加载
tags: js
date: 2019-02-19 17:20
categories: 前端
---
***
```
"远而望之，皎若太阳升朝霞;迫而察之，灼若芙蕖出渌波。"
```
#### 原生javascript的上拉加载操作
**1.注意js的onscroll方法，window.onscroll = function(){}检测在滚动条滚动的时候执行的操作**
**2.通过获取文档高度scrollHeight,视图高度clientHeight,滚动条滚动高度scrollTop，三个document属性**

**3.注意判断高度选取正确的值，如document.body.scrollTop,document.documentElement.scrollTop**

**4.在clientHeight跟scrollTop的高度总和等于scrollHeight时说明滑动到了底部，此时执行加载更多操作**

<!--more-->

代码如下
```
  // 上拉加载
  // 获取滚动条当前位置
  var pageNum = 1
window.onscroll = function(){
    // 1.先获取滚动条滚动的高度，用scrollTop,
    // 2.获取可视的高度，用clientHeight
    // 3.文档所有的高度 scrollHeight

    function getScrollTop(){
      var scrollTop = 0;
      if(document.documentElement && document.documentElement.scrollTop){
        scrollTop = document.documentElement.scrollTop
      }else if(document.body){
        scrollTop = document.body.scrollTop
      }
      return scrollTop
    }

    function getClientHeight(){
      var clientHeight = 0;
      if (document.body.clientHeight && document.documentElement.clientHeight) {
        clientHeight = Math.min(document.body.clientHeight, document.documentElement.clientHeight);
      } else {
        clientHeight = Math.max(document.body.clientHeight, document.documentElement.clientHeight);
      }
      return clientHeight;
    }

    function getScrollHeight() {
      return Math.max(document.body.scrollHeight, document.documentElement.scrollHeight);
    }
    if (getScrollHeight() - parseInt(getScrollTop() + getClientHeight()) == 1) {
      pageNum++
      for(let i = 20 * (pageNum - 1) + 1; i <= 20 * pageNum; i++){
        let li = document.createElement('li')
        li.innerText = `这是测试啊${i}`
        li.style.paddingTop = "20px"
        ul.appendChild(li)
      }
    }
  }
```