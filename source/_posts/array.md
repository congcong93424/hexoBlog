---
title: 数组对象去重，对象的拷贝
tags: js
date: 2019-03-06 17:40
categories: 前端
---
***
```
"知命者不怨天，知己者不怨人。"
```
#### 1.js数组去重
** 方法一丶es5数组去重的思路: 1.遍历数组，新增空数组，判断新增数组IndexOf是否相等原数组，否则push **
```
var uniq = function(newArr) {
		var temArr = []
		for (var i = 0; i < newArr.length; i++){
			if(temArr.indexOf(newArr[i]) == -1){
				temArr.push(newArr[i])
			}
		}
		return temArr
	}
```
<!--more-->
** 方法二丶 通过双层遍历，判断第二个跟第三个的值是否相等,相等就通过splice删除原数组后一个元素 **
```
function unique(arr){            
        for(var i=0; i<arr.length; i++){
            for(var j=i+1; j<arr.length; j++){
                if(arr[i]==arr[j]){        
                    arr.splice(j,1);
                    j--;
                }
            }
        }
return arr;
}
```
** 方法三丶 运用es6的新特性，new Set 跟array from **
new Set():ES6 提供了新的数据结构 Set。它类似于数组，但是成员的值都是唯一的，没有重复的值。

Set本身是一个构造函数，用来生成 Set 数据结构。

Array.from()方法就是将一个类数组对象或者可遍历对象转换成一个真正的数组。
```
function unique (arr) {
  return Array.from(new Set(arr))
}
```


>1.浅拷贝： 将原对象或原数组的引用直接赋给新对象，新数组，新对象／数组只是原对象的一个引用
2.深拷贝： 创建一个新的对象和数组，将原对象的各项属性的“值”（数组的所有元素）拷贝过来，是“值”而不是“引用”

#### 2.对象浅拷贝
对象是 JavaScript 的基本块。对象是属性的集合，属性是键值对。JavaScript 中的几乎所有对象都是位于原型链顶部 Object 的实例。

浅拷贝对象
当拷贝源对象的顶级属性被复制而没有任何引用，并且拷贝源对象存在一个值为对象的属性，被复制为一个引用时，那么我说这个对象被浅拷贝。如果拷贝源对象的属性值是对象的引用，则只将该引用值复制到目标对象。

浅层复制将复制顶级属性，但是嵌套对象将在原始（源）对象和副本（目标）对象之间是共享。
**方法一丶循环遍历原始对象，然后一个一个地复制每个属性**
```
function copy(mainObj) {
  let objCopy = {}; // objCopy 将存储 mainObj 的副本
  let key;

  for (key in mainObj) {
    objCopy[key] = mainObj[key]; // 将每个属性复制到objCopy对象
  }
  return objCopy;
}
```

**方法二丶使用Object.assign()方法**
```
let obj = {
  a: 1,
  b: 2,
};
let objCopy = Object.assign({}, obj);
console.log(objCopy);
// Result - { a: 1, b: 2 }
```
> let obj = {
  a: 1,
  b: {
    c: 2,
  },
}
let newObj = Object.assign({}, obj);
console.log(newObj); // { a: 1, b: { c: 2} }
obj.a = 10;
console.log(obj); // { a: 10, b: { c: 2} }
console.log(newObj); // { a: 1, b: { c: 2} }
newObj.a = 20;
console.log(obj); // { a: 10, b: { c: 2} }
console.log(newObj); // { a: 20, b: { c: 2} }
newObj.b.c = 30;
console.log(obj); // { a: 10, b: { c: 30} }
console.log(newObj); // { a: 20, b: { c: 30} }
// 注意: newObj.b.c = 30; 为什么呢..

Object.assign的缺点，如果原对象的某个属性值是一个对象，那么拷贝的目标对象更改对象里那个对象的属性值时，原对象属性值为对象的那个也将被改变，这不是我们想要的。

这就是 Object.assign() 的陷阱。Object.assign 只是浅拷贝。 newObj.b 和 obj.b 都引用同一个对象，没有单独拷贝，而是复制了对该对象的引用。任何对对象属性的更改都适用于使用该对象的所有引用。
**方法三丶对象字面量的展开操作符能将源对象中的可枚举的属性复制到目标对象上。**
```
let obj = {
  one: 1,
  two: 2,
}

let newObj = { ...z };

// { one: 1, two: 2 }
```
注意：这将只对浅拷贝有效

注意：原型链上的属性和不可枚举的属性不能复制。 看这里：
```
let someObj = {
  a: 2,
}

let obj = Object.create(someObj, {
  b: {
    value: 2,  
  },
  c: {
    value: 3,
    enumerable: true,  
  },
});

let objCopy = Object.assign({}, obj);
console.log(objCopy); // { c: 3 }
```
someObj 是在 obj 的原型链，所以它不会被复制。
属性 b 是不可枚举属性。
属性 c 具有 可枚举(enumerable) 属性描述符，所以它可以枚举。 这就是为什么它会被复制。

#### 3.对象深拷贝
深度拷贝将拷贝遇到的每个对象。副本和原始对象不会共享任何东西，所以它将是原件的副本。以下是使用 Object.assign() 遇到问题的修复方案。

**方法一丶使用JSON.parse(JSON.stringfy())**
```
let obj = {
  a: 1,
  b: {
    c: 2,
  },
}

let newObj = JSON.parse(JSON.stringify(obj));

obj.b.c = 20;
console.log(obj); // { a: 1, b: { c: 20 } }
console.log(newObj); // { a: 1, b: { c: 2 } } (一个新的对象)
```
陷阱：不幸的是，此方法不能用于复制用户定义的对象方法

**解决方案：Object.assign可以复制对象里的方法**
```
let obj = {
  name: 'scotch.io',
  exec: function exec() {
    return true;
  },
}

let method1 = Object.assign({}, obj);
let method2 = JSON.parse(JSON.stringify(obj));

console.log(method1); //Object.assign({}, obj)
/* result
{
  exec: function exec() {
    return true;
  },
  name: "scotch.io"
}
*/

console.log(method2); // JSON.parse(JSON.stringify(obj))
/* result
{
  name: "scotch.io"
}
*/
```
结果表明，Object.assign() 可以用于复制对象的方法，而使用 JSON.parse(JSON.stringify(obj)) 则不行。
**方法二丶引入immutable**
```
const { Map } = require('immutable')
const map1 = Map({ a: 1, b: 2, c: 3 })
const map2 = map1.set('b', 50)
map1.get('b') // 2
map2.get('b') // 50
```
**方法三丶循环遍历**
```
let obj1 = {
  a: '1',
  b: '2',
  c: {
    d: '3'
  },
  d: function aa () {}
}
function deepCopy (obj) {
  let temp = obj.constructor === Array ? [] : {}
  for (let val in obj) {
    temp[val] = typeof obj[val] == 'object' ? deepCopy(obj[val]) : obj[val]
  }
  return temp
}
console.log(deepCopy(obj1)) //{ a: '1', b: '2', c: { d: '3' }, d: [Function: aa] }
```
