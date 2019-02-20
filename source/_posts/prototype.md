---
title: js原型与原型链
tags: js
date: 2019-02-21 0:11
categories: 前端
---
***
```
"我一定要幸福，哪怕幸福是场表演，我也会尽力演好每一场戏"
```
#### js原型与原型链
```
1.每一个构造函数都拥有一个prototype属性，这个属性指向一个对象，也就是原型对象。当使用这个构造函数创建实例的时候，prototype属性指向的原型对象就成为实例的原型对象。
2.原型对象默认拥有一个constructor属性，指向指向它的那个构造函数（也就是说构造函数和原型对象是互相指向的关系）。
3.每个对象都拥有一个隐藏的属性[[prototype]]，指向它的原型对象，这个属性可以通过
Object.getPrototypeOf(obj) 或 obj.__proto__ 来访问。
4.实际上，构造函数的prototype属性与它创建的实例对象的[[prototype]]属性指向的是同一个对象，即 对象.__proto__ === 函数.prototype 。
5.在JavaScript中，所有的对象都是由它的原型对象继承而来，反之，所有的对象都可以作为原型对象存在。
6.访问对象的属性时，JavaScript会首先在对象自身的属性内查找，若没有找到，则会跳转到该对象的原型对象中查找。
```
代码如下
```
<script>
	function User(name, level) {
		this.name = name;
		this.level = level;
	}
	User.prototype.showName = function(name) {
		alert(this.name)
	}
	User.prototype.showLevel = function(level) {
		alert(this.level)
	}

	var test = new User("XXX", "高级");

	test.showName()
	test.showLevel()


	// 继承
	function Vipuser(name,level,pass) {
		User.call(this,name,level);
		this.pass = pass;
	}

	Vipuser.prototype = new User()
	Vipuser.prototype.constructor = Vipuser;

	Vipuser.prototype.showPass = function(pass){
		alert(this.pass)
	}

	var jicheng = new Vipuser("XXX","高德","通过")

	jicheng.showName()
	jicheng.showPass()
	jicheng.showLevel()

</script>
```

### 确定原型和实例的关系
使用原型链后, 我们怎么去判断原型和实例的这种继承关系呢? 方法一般有两种.
```
第一种是使用 instanceof 操作符, 只要用这个操作符来测试实例(instance)与原型链中出现过的构造函数,结果就会返回true. 以下几行代码就说明了这点.
person instanceof father
```
```
第二种是使用 isPrototypeOf() 方法, 同样只要是原型链中出现过的原型,isPrototypeOf() 方法就会返回true, 如下所示.
Son.prototype.isPrototypeOf(father)
```

##### 想避免原型链查找, 建议使用 hasOwnProperty 方法. 因为 hasOwnProperty 是 JavaScript 中唯一一个处理属性但是不查找原型链的函数


##### 原型对象的constructor 属性指向创建的实例的构造函数.   实例的构造函数属性（constructor）指向构造函数
obj._proto_ === Object.prototype