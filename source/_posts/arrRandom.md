---
title: 数组排序，检测字符串取最多的字符
tags: js
date: 2019-03-11 17:56
categories: 前端
---
***
```
"过去的事之所以美好就在于它已成为过去，往事我们就让它如烟飘散。"
```
**记录面试遇到的两个问题，注意思路很重要，对象属性的唯一性，随机数，这里讲述两个问题，第一如何将数组随机排列，第二，检测字符串出现最多的那个字符跟相应的次数**

#### 问题1：ajajajdffdfsfaa这样一个字符产检测出现最多次数的字符跟次数，打印出来
<!--more-->
```
  // 思路： 将字符串的每一个值写进对象的属性里面去
	//  2.通过字符chatAt取出值
  var str = 'ajajajdffdfsfaa'
	var obj = {}
	for(var i = 0 ;i < str.length; i++){
		if(!obj[str.charAt(i)]){
			obj[str.charAt(i)]  = 1
		}else{
			obj[str.charAt(i)] = obj[str.charAt(i)] + 1
		}
	}

	var maxNum = 0;
	var maxStr = ''

	for(var j in obj){
		if(obj[j] >= maxNum){
			maxNum = obj[j]
			maxStr += j
		}
	}

	console.log(`出现最多次数的字符是${maxStr},一共出现了${maxNum}`)

  <!-- 出现最多次数的字符是a,一共出现了5 -->
```

#### 问题2：将数组重新随机排序
```
/*
	** 思路： 首先数组是有长度的，根据总长度，想到math.random()的方式获取随机数，获取后将数组内容交换即可
	 */
	function arrRandom(arr){
		for(var i=0; i<arr.length-1;i++){
			var randomNum = parseInt(Math.random() * arr.length)
			var temNum = arr[randomNum]
			arr[randomNum] = arr[i]
			arr[i] = temNum
		}
		console.log(arr)
	}
	arrRandom([1,2,4,5,6])
```
