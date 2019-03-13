---
title: react
tags: 前端
date: 2019-03-13 16:07
categories: react
---
***
```
 "黄色的树林里有两条岔开的路，可惜我不能在同一时间走两条路，我选择了少人行走的那条，这就造成了一切的差异。"
```
**选取自吕涯的react总结，感谢他的付出，放这里的原因是面试在即，方便查看，没有剽窃之心，再次感谢**

#React全家桶

# **第1章：React入门**

## 1.1. **React的基本认识**

DOM就是文档对象模型，在内存中是一颗树，DOM树（c++树）。我们在渲染页面的时候就会依据DOM树去渲染。

我们原生可以操作DOM，是与DOM进行交流。但比较麻烦。

而jQuery是比较方便我们去操作DOM，让我们操作DOM更加简单。但它运行速度比较慢。

而react，我们开发者就不再需要去直接跟DOM去打交道了，react就是一座桥梁，帮助我们与DOM之间的沟通，我们不需要直接去操作DOM，只需要编写你想要什么，react就会明白该怎么做，当数据变化时，那么就会UI相应的去改变，这就是react支持响应式UI理念，大大简化了UI的开发。另外一点，就是虚拟DOM，我们操作的就是虚拟DOM，这会大大提高性能。而不需要多次操作DOM。其实react用的技术就是文档碎片的形式去实现虚拟DOM技术。最后一个react的组件化开发，我们写一个页面，就像人一样，都是由每个组件组成的，头身体脚等等，我们直接去定义好组件，然后拼接起来就可以啦，组件中可能有公共的组件或更小的组件亦或功能逻辑比较复杂的组件，这就需要我们一层一层去定义好。这时，组件化的编程好处就出来了，当你改变了某个组件，那么所有使用此组件的地方都将自动更新，是不是很爽。
<!--more-->


### 1.1.1. **官网**

1) 英文官网:[ https://reactjs.org/](https://reactjs.org/)

2) 中文官网: <https://doc.react-china.org/>

### 1.1.2. **介绍描述**

1) 用于**构建用户界面**的 JavaScript 库(只关注于View层)

2) 由Facebook开源

记住：项目开启时，有无案例演示：要回答有。案例演示就是UI设计师的画的。

> ejs模板引擎：是有服务器端渲染的。像之前前后端无分离的，那么ejs模板就是数据在后端渲染（NODE）
>
> react：数据是由前端渲染的，后台只要给我数据，我改变状态去更新界面。（前后端分离）

### 1.1.3. **React的特点**

1) Declarative(声明式编码)

声明式编码（填充题）对应的是命令式编码（简答题，强调过程）。声明式编码的内部就是命令式编码。

2) Component-Based(组件化编码)-->基于组件化开发

3) Learn Once, Write Anywhere(支持客户端与服务器渲染)--->支持客户端和服务器端的渲染

4) 高效----->虚拟DOM

5) 单向数据流（Vue是双向数据流）

**注：**

1.父组件流向子组件。这就是单向数据流，通过props在标签属性来进行组件间的通信。

2.那么子组件要把数据流向父组件，其实也是有办法，那就是在父组件中声明一个函数，这个函数来改变状态，然后把这个函数传递给子组件，子组件调用这个函数间接去改变父组件的状态。

3.如果爷爷组件要传递给孙子组件，那么之间的通信会比较麻烦，那么这个时候也可以通过组件间的通信的第二种方式（订阅与发布机制来实现）

就是MVC架构（module就是数据层，View就是视图层，Control就是控制层）那么一般是M把数据传送到Control中，然后再去传送到View层。这就是单向数据流。

- 视图（View）：用户界面。
- 控制器（Controller）：业务逻辑
- 模型（Model）：数据保存

![](F:\截图软件图片保存\2018-07-15_155903.png)

![2018-07-15_155920](F:\截图软件图片保存\2018-07-15_155920.png)

![2018-07-15_155930](F:\截图软件图片保存\2018-07-15_155930.png)



### 1.1.4. **React高效的原因**

1) 虚拟(virtual)DOM, 不总是直接操作DOM-->**减少重绘重排的次数**，利用**文档碎片**来实现的。

2) DOM Diff算法, 最小化页面重绘（由这个可知，state从来不会替换，而是重新生成state）

## 1.2. **React的基本使用**

注意: 此时只是测试语法使用, 并不是真实项目开发使用

### 1.2.1. **效果**

![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\ksohtml\wps1B29.tmp.jpg)

### 1.2.2. **相关js库**

1) react.js: React的核心库（要最先引入）

2) react-dom.js: 提供操作DOM的react扩展库（依赖于react核心库）

3) babel.min.js: 解析JSX语法代码转为纯JS语法代码的库

### 1.2.3. **在页面中导入js**

```
<script type="text/javascript" src="../js/react.development.js"></script>
<script type="text/javascript" src="../js/react-dom.development.js"></script>
<script type="text/javascript" src="../js/babel.min.js"></script>
```

### 1.2.4. **编码**

```
<script type="text/babel"> //必须声明为babel
  // 创建虚拟DOM元素
  let virtualDom = <h1>hello react I and You </h1>; // 千万不要加引号
  // 渲染虚拟DOM到页面真实DOM容器中
  ReactDOM.render(virtualDom,document.getElementById('box'));
</script>
```

### 1.2.5. **使用React开发者工具调试**

![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\ksohtml\wps1B2A.tmp.png)



## 1.3. **React JSX**

### 1.3.1. **虚拟DOM**

1) React提供了一些API来创建一种 `特别` 的一般js对象

a. var element = React.createElement('h1', {id:'myTitle'},'hello')

b. 上面创建的就是一个简单的虚拟DOM对象。已经很少用了。

2) 虚拟DOM对象最终都会被React转换为真实的DOM

3) 我们编码时基本只需要操作react的虚拟DOM相关数据, react会转换为真实DOM变化而更新界面

### 1.3.2. **JSX**

1) 全称:  JavaScript XML

2) react定义的一种类似于XML的JS扩展语法: XML+JS

3) 作用: 用来创建react虚拟DOM(元素)对象

a. var ele = <h1>Hello JSX!</h1>

b. 注意1: <u>它不是字符串, 也不是HTML/XML标签</u>

c. 注意2: 它最终产生的就是一个**JS对象**

4) 标签名任意: HTML标签或其它标签

5) 标签属性任意: HTML标签属性或其它

6) 基本语法规则

a. 遇到 <开头的代码, 以标签的语法解析: html同名标签转换为html同名元素, 其它标签需要特别解析

b. 遇到以 { 开头的代码，以JS语法解析: 标签中的js代码必须用{ }包含.这就是和vue的区别。当在style中。其react应该是{{}}，外层表js代码，里层表对象。

7) babel.js的作用

a. **浏览器不能直接解析JSX代码, 需要babel转译为纯JS的代码才能运行**

b. 只要用了JSX，都要加上type="text/babel", 声明需要babel来处理



### 1.3.3. **渲染虚拟DOM(元素)**

1) 语法:  ReactDOM.render(virtualDOM, containerDOM)

2) 作用: 将虚拟DOM元素渲染到页面中的真实容器DOM中显示

3) 参数说明

a. 参数一: 纯js或jsx创建的虚拟dom对象（两种方式创建虚拟DOM对象）

b. 参数二: 用来包含虚拟DOM元素的真实dom元素对象(一般是一个div)



### 1.3.4. **建虚拟DOM的2种方式**

1) 纯JS(一般不用)

*React.createElement('h1',*  *{id:'myTitle'},*  *title)*

2) JSX:

*<h1 id='myTitle'>{title}</h1>*

```
//两种方式创建虚拟DOM对象

//用纯js语法创建虚拟DOM语法
  let t = React.createElement('H1', {class: 'box1'}, '我是放文本内容的，hello react');
  //渲染
  ReactDOM.render(t,document.getElementById('test1'));


  //创建第二种方法
  let virtualDom = <h1>我是文本，里面放内容。第二种创建虚拟DOM的方法。</h1>;
  ReactDOM.render(virtualDom,document.getElementById('test2'));
```



### 1.3.5. **JSX练习**

需求: 动态展示列表数据

![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\ksohtml\wps1B3B.tmp.jpg)

```
<script type="text/babel">
  let arr = ['我','是','傻','X']
  ReactDOM.render((
      <ul>
        {arr.map((item,index)=>  <li key={index}>{item}</li>)}
      </ul>
  ),document.getElementById('test'));
</script>
```



## 1.4. **模块与组件和模块化与组件化的理解**

### 1.4.1. **模块**

1) 理解: 向外提供特定功能的js程序, 一般就是一个js文件

2) 为什么:  js代码更多更复杂

3) 作用: 复用js, 简化js的编写, 提高js运行效率（耦合度高。污染全局gloab，不易复用，不易维护）

### 1.4.2. **组件**

1) 理解: 用来实现特定(局部)功能效果的代码集合**(html/css/js)** 注意两个词：功能对应js，效果对应HTML、CSS

2) 为什么: 一个界面的功能更复杂

3) 作用: 复用编码, 简化项目编码, 提高运行效率

就像一个京东，列表选框上，他有很多的是功能一样的，那么就把他当做组件去写。**复用性强。**

> 组件的两个作用：
>
> 1.复用性（将重复的界面单独抽取出来成为一个组件）
>
> 2.简化（有些组件的某一部分的功能比较复杂，需要单独抽取出来做，可以简化代码。比如，NavFooter可以单独抽取出来做，本身是放在main中的，但因为本身的逻辑可能比较复杂，要过滤掉某一个路由，去自动匹配响应的路由组件。或者user-list的逻辑比较复杂。）

### 1.4.3. **模块化**

当应用的js都以模块来编写的, 这个应用就是一个模块化的应用

### 1.4.4. **组件化**

当应用是以多组件的方式实现, 这个应用就是一个组件化的应用

![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\ksohtml\wps1B3C.tmp.png)



当既有模块化又有组件化的一个项目，那么就是一个工程化的。（应用react脚手架搭建的项目就是工程化。能够自动打包编译，检查语法，并且自动运行在浏览器就是一个工程化的项目）

# **第2章：React面向组件编程**

## **2.1. 基本理解和使用**

### **2.1.1. 效果**

![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\ksohtml\wps1B3D.tmp.jpg)

```
/*工厂函数创建组件*/
function MyComponentOne() {
  return <h1>我是工厂函数创建组件的方式，这种方式不会创建新的实例对象，只是调用函数</h1>
}
ReactDOM.render(< MyComponentOne />,document.getElementById('test1'));

/*通过ES6-class的类的方式创建组件*/
class MyComponentTwo extends React.Component {
  constructor (props){
    super(props);
    /*只有在调用super之前，才能去用this。this的指向就靠super来的*/
    console.log('我是construction的方法的输出···', this,this.props);
  }
  render() {
    return <h1>我是通过ES6中的class来创建组件的，先new创建实例，然后调用render方法。</h1>
  }
}

ReactDOM.render(< MyComponentTwo />, document.getElementById('test2'))
```



### **2.1.2. 自定义组件(Component) :**

1) 定义组件(3种方式)

```
/*方式1: 工厂函数组件(简单组件)*/
function MyComponent () {
  return <h2>工厂函数组件(简单组件)</h2>
}
//工厂函数组件会进行一些简单的操作，他会自动去调用。而不会创建新的实例。

/*方式2:  ES6类组件(复杂组件)*/
class MyComponent2 extends React.Component {
  render () {
    console.log(this) // MyComponent2的实例对象
    return <h2>ES6类组件(复杂组件)</h2>
  }
}
//这里可以显示出声明式编程的想法。render里面有会做很多的事情，我不关心，我不关心其具体的过程是如何实现。这就是声明式编程的概念，类似于填空题。与之对应的是一个命令式编程的概念，他是关系过程，类似于简答题。
/*另外一种不讲几乎不用*/
```

2) 渲染组件标签

```
ReactDOM.render(<MyComponent />, document.getElementById('example1'))
```



### **2.1.3. 注意**

1) 组件名必须首字母大写

2) 虚拟DOM元素只能有一个**根元素**

3) 虚拟DOM元素必须有结束标签

4) style标签要用{{}}

5)不能用class关键字，要用className

6)有些单标签要加上自结束标签

### **2.1.4. render()渲染组件标签的基本流程**

## **2.2. 组件三大属性1: state**

### **2.2.1. 效果**

![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\ksohtml\wps1B4D.tmp.png)

```
class Love extends React.Component {
    constructor (props){
      super(props);
      this.state = {
        isLove : true
      }
      //改变changeLove的this指向，本身undefined
      this.switchLove = this.switchLove.bind(this);
    }

    switchLove () {
      //获取到最新的state
      let isLove = !this.state.isLove;
      //去设置更新状态
      this.setState({isLove});
    }

    render() {

      let text = this.state.isLove ? '你是9，我是3' : '我除了你，还是你' ;
      return <h1 onClick={this.switchLove}> {text} </h1>
    }

  }

  ReactDOM.render(< Love/>,document.getElementById('test'))
```



### **2.2.2. 理解**

1) state是组件对象最重要的属性, 值是对象(可以包含多个数据)

2) 组件被称为"状态机", 通过更新组件的state来更新对应的页面显示(重新渲染组件)。**组件是虚拟DOM的集合**。创建组件并渲染组件。

### **2.2.3. 编码操作**

1) 初始化状态:（一般把他写在constructor里面）

  *constructor (props) {*

​    *super(props)*

​    *this.state = {*

​      *stateProp1 : value1,*

​      *stateProp2 : value2*

​    *}*

  *}*

2) 读取某个状态值

  *this.state.statePropertyName*

3) 更新状态---->组件界面更新（注意，在调用了setState中后，就会react内部会去调用render。这就是观察者模式：render，render去监听一切的变化，只要有变化，那就重新调用render，渲染组件。）

  *this.setState({*

​    *stateProp1 : value1,*

​    *stateProp2 : value2*

  *})*

## **2.3. 组件三大属性2: props**

### **2.3.1. 效果**

需求: *自定义用来显示一个人员信息的组件*  *1).* *姓名必须指定*  *2).* 如果性别没有指定,默认为男3). 如果年龄没有指定, 默认为18

![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\ksohtml\wps1B4E.tmp.jpg)

```
class Person extends React.Component {

    render() {
      //获取到外面定义的props
      let {name,age,gender} = this.props;
      return (
        <ul>
          <li>Name : {name}</li>
          <li>Age : {age}</li>
          <li>Gender : {gender}</li>
        </ul>
      )
    }
  }

  //定义props的一些属性及其限制
  Person.propTypes = {
    //没有提供时，会打印警告信息
    name:PropTypes.string.isRequired,
    age :PropTypes.number,
    gender :PropTypes.oneOf(['Male','Female'])
  };
  //给一些props一些默认属性值
  Person.defaultProps = {
    age : 18,
    gender : 'Male'
  };
  //在外面传值
  let person1 = {name:'lyuya' , age : 16 , gender : 'Male'};
  //渲染-->扩展属性: 将对象的所有属性通过props传递
  ReactDOM.render(< Person {...person1}/>, document.getElementById('test1'));

  let person2 = {name:'react'};
  ReactDOM.render(< Person {...person2}/>, document.getElementById('test2'));
```

### **2.3.2. 理解**

1) 每个组件对象都会有props(properties的简写)属性

2) 组件标签的所有属性都保存在props中

### **2.3.3. 作用**

1) 通过**标签属性**从组件外向组件内传递变化的数据2) 注意: 组件内部不要修改props数据

### **2.3.4. 编码操作**

1) 内部读取某个属性值

*this.props.propertyName*

2) 对props中的属性值进行类型限制和必要性限制（一般是放在组件的外面定义）

*Person.propTypes = {*

​    name:PropTypes.string.isRequired,
    age :PropTypes.number,
    gender :PropTypes.oneOf(['Male','Female'])

*}*

但在后面我们发现：引入一个库（prop-types中有一个PropTypes）

static PropTypes = {

 item:PropTypes.object.isRequired,  

 index:PropTypes.number.isRequired,

 del:PropTypes.func.isRequired,

};

3) 扩展属性: 将对象的所有属性通过props传递

通过标签属性（键值对）来传递props

本身是<Person name={person.name}  age={person.age} />

还可以用三点运算符（这里详细补充一下，为什么对象可以用三点运算符，可知react框架对对象进行了可迭代的优化，添加了Symbol(symbol.iterator) 属性。迭代的本质就是其或其原型上有Symbol(symbol.iterator)属性）

*<Person {...person}/>*

4) 默认属性值

*Person.defaultProps = {*

*name: 'Mary'*

*}*

5) 组件类的构造函数

这里要传prop进去，是因为constructor里面要用props。如果不用的话可以不传。

*constructor (props) {*

*super(props)*

*console.log(props) // 查看所有属性*

*}*



### **2.3.5. 面试题**

问题: 请区别一下组件的props和state属性

```
- state是定义在组件内部的私有数据
- props是定义在组件外部的公有数据
- 提前就能定义好的数据通常用state
- 如果需要发送请求或者传递数据，就是用props

双向通信的问题：
父----->子  
通过props去传递就可以做到
子------>父
在父中定义一个函数，然后将这个函数用props去传递给子，然后子来调用，这样就可以更新子的数据。从子的数据更新到父中的数据。
```

1) state: 组件自身内部可变化的数据

2) props: 从组件外部向组件内部传递数据, 组件内部**只读不修改**

## **2.4. 组件三大属性3: refs与事件处理**

### **2.4.1. 效果**

需求: 自定义组件,功能说明如下: 2.点击按钮,*提示第一个输入框中的值*  *3.* *当第**2**个输入框失去焦点时,*提示这个输入框中的值



![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\ksohtml\wps1B4F.tmp.png)

```
 class App extends React.Component {
      constructor (prop){
        super(prop);
        //修改this指向
        this.handleData = this.handleData.bind(this);
        this.handleData1 = this.handleData1.bind(this);

      }
      //处理的一些alert逻辑
      handleData () {
        let {value} = this.inputDom;
        if(value.trim()){
          alert(value);
          this.inputDom.value = '';
        }
      }
      handleData1 () {
        let {value} = this.refs.xxx;
        if(value.trim()){
          alert(value);
          this.refs.xxx.value = '';
        }
      }
      handleBlur (event){
        let {value} = event.target;
        if(value.trim()){
          alert(value);
          event.target.value = '';
        }
      }

    render() {
     return (
       <div>
       //this表示是实例对象
           <input type="text" ref={input=>this.inputDom=input}/>
           <button onClick = {this.handleData}>提示输入数据</button>
           <input type="text" ref='xxx'/>
           <button onClick = {this.handleData1}>提示输入数据1</button>
           <input type="text" placeholder="失去焦点提示数据" onBlur={this.handleBlur}/>
       </div>
     )
    }
    }
    //渲染
    ReactDOM.render(<App />, document.getElementById('test'))
```



### **2.4.2. 组件的3大属性之三: refs属性**

1) 组件内的标签都可以定义ref属性来标识自己

```
 <input type="text" ref={input => this.xxxx = input}/>
```

b. 回调函数在组件初始化渲染完或卸载时自动调用

2) 在组件中可以通过this.xxxx来得到对应的真实DOM元素

3) 作用: 通过ref获取组件内容特定标签对象, 进行读取其相关数据

### **2.4.3. 事件处理**

1) **通过onXxx属性指定组件的事件处理函数(注意大小写)**

a. React使用的是自定义(合成)事件, 而不是使用的原生DOM事件（！！！）

b. React中的事件是通过事件委托方式处理的(委托给组件最外层的元素)

2) **通过event.target得到发生事件的DOM元素对象**

*<input onFocus={this.handleClick}/>*

*handleFocus(event) {*

*event.target  //返回input对象*

*}*

绑定事件监听需要哪些？第一就是事件名，第二就是回调函数，第三就是参数（Event,传递给回调函数，event本身是一个数据容器，里面包括了target，type，clientX等一些数据的信息）

绑定事件监听和触发事件是不同的概念。绑定了之后不一定触发。触发DOM事件，就是浏览器去做的。

### **2.4.4. 强烈注意**

1) **组件内置的方法中的this为组件对象**

2) 在组件类中自定义的方法中this为undefined

a. 强制绑定this: 通过函数对象的bind()

b. 箭头函数(ES6模块化编码时才能使用通常开发中都这么用)

## **2.5. 组件的组合**

### **2.5.1. 效果**

功能: 组件化实现此功能

  1. 显示所有todo列表
  2. 输入文本, 点击按钮显示到列表的首位, 并清除输入的文本

![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\ksohtml\wps1B60.tmp.png)

```
 //定义主组件 App
  class App extends React.Component {
    //state要在construction里面定义
    constructor(props) {
      super(props);
      this.state = {
        todoList: ['我是9', '你是3', '我除了你', '还是你']
      }
      //修正this的指向
      this.add = this.add.bind(this);
    }
    //定义一个方法,去操作app中的数据
    add(newTodo){
     //获取这个数组
      let {todoList} = this.state;
      //插入传过来的值到数组中
      todoList.unshift(newTodo);
      //更新state数据
      this.setState({todoList});
    }

    render() {
      //获取到state
      let {todoList} = this.state;
      return (
        <div>
          <h2>Simple TODO List</h2>
          <AddTodo add={this.add} length={this.state.todoList.length}/>
          <TodoList todoList={todoList}/>
        </div>
      )
    }
  }

  //定义一个AddTodo组件
  class AddTodo extends React.Component {

    constructor(props) {
      super(props);
      //修正add的this指向
      this.add = this.add.bind(this);
    }

    //绑定一个增加的事件
    add() {
      console.log(this.props);
      //获取到input的值-value
      // console.log(this.refs.xxx.value);
      let value = this.refs.xxx.value.trim();
      if (value) {
        //要增加上去
        this.props.add(value);
        //清空
        this.refs.xxx.value = '';
      }
    }

    render() {
      return (
        <div>
          <input type="text" ref="xxx"/>
          <button onClick={this.add}>Add #{this.props.length}</button>
        </div>
      )
    }
  }

  //定义一个TodoList组件
  class TodoList extends React.Component {
    render() {
      //todoList此时是一个数组
      let {todoList} = this.props;
      console.log(todoList);
      return (
        <ul>
          {todoList.map((item, index) => <li key={index}>{item}</li>)}
        </ul>
      )
    }
  }

  //渲染
  ReactDOM.render(<App/>, document.getElementById('test'))

```



### **2.5.2. 功能界面的组件化编码流程(无比重要)**

1) 拆分组件: 拆分界面,抽取组件

2) 实现静态组件: 使用组件实现静态页面效果

3) 实现动态组件

a. 动态显示初始化数据（看看初始化的数据用state定义还是用props去传递）

b. 交互功能(从绑定事件监听开始)

## **2.6. 收集表单数据**

### **2.6.1. 效果**

需求: 自定义包含表单的组件
  1. 输入用户名密码后, 点击登陆提示输入信息
  3. 不提交表单


![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\ksohtml\wps1B61.tmp.png)

```

class App extends React.Component {
  constructor(props){
    super(props);
    //初始化
    this.state = {
      msg : 'hello lyuya'
    };
    this.handleChange = this.handleChange.bind(this)
  }
  handleChange(event){
    this.setState({
      msg:event.target.value
    })
  }
  render() {
    let {msg} = this.state;
    return (
      <div>
          <input type="text" value={msg} onChange={this.handleChange}/>
          <p>{msg}</p>
      </div>
    )
  }
  }
  ReactDOM.render(<App />, document.getElementById('test'))
```



### **2.6.2. 理解**

1) 问题: 在react应用中, 如何收集表单输入数据

2) 包含表单的组件分类

a. 受控组件: 表单项输入数据能自动收集成状态(通过在表单上添加onchange函数，然后将表单的数据准确的显示在状态里，重新设置状态即可)

b. 非受控组件: 需要时才手动读取表单输入框中的数据

```
<script type="text/babel">
  /*
  受控组件
  1. React是一个单向数据流
  2. 但可以自定义双向数据流组件(受控组件)
  */
  /*
  功能: 自定义组件, 功能如下
    1. 界面如页面所示
    2. 初始数据显示为atguigu
    3. 输入数据时, 下面的数据同步变化
  */

class App extends React.Component {
  constructor(props){
    super(props);
    //初始化
    this.state = {
      msg : 'hello lyuya'
    };
    this.handleChange = this.handleChange.bind(this)
  }
  handleChange(event){
    this.setState({
      msg:event.target.value
    })
  }
  render() {
    let {msg} = this.state;
    return (
      <div>
          <input type="text" value={msg} onChange={this.handleChange}/>
          <p>{msg}</p>
      </div>
    )
  }
  }
  ReactDOM.render(<App />, document.getElementById('test'))
</script>
```



## **2.7. 组件生命周期**

### **2.7.1. 效果**

需求: 自定义组件
  1. 让指定的文本做显示/隐藏的渐变动画
  2. 切换持续时间为2S
  3. 点击按钮从界面中移除组件界面

![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\ksohtml\wps1B62.tmp.png)

```
 class LifeCycle extends React.Component {
    constructor(props){
      console.log('constructor()')
      super(props);
      this.state = {
        opacity : 1
      }
    }
    //组件将被挂载
    componentWillMount (){
      console.log('componentWillMount()组件将被挂载')
    }
    //组件已经挂载完毕
    componentDidMount () {
      console.log('componentDidMount()组件已经挂载完毕')
      let opacity = this.state.opacity;
      //处理透明度
      this.timer = setInterval(()=>{
        opacity -= 0.1;
        if(opacity <= 0){
          opacity = 1;
        }
        this.setState({opacity});
      },200);
    }

    //组件应该被更新（this.setState）
    shouldComponentUpdate (){
    console.log('shoudComponentUpdate()组件应该被更新')
      return true
    }
    //组件将要被更新
    componentWillUpdate (){
    console.log('componentWillUpdate()组件将要被更新')
    }
    //组件已经更新完毕
    componentDidUpdate (){
    console.log('componentDidUpdate()组件已经更新完毕')
    }
    //组件将要被卸载-当触发unmountComponentAtNode
    componentWillUnmount() {
      clearInterval(this.timer);
    }


    render() {
      let {opacity} = this.state;
      return (
        <div>
          <h1 style={{opacity}}>我现在京SOLO的天台上</h1>
          <button onClick={()=>ReactDOM.unmountComponentAtNode(document.getElementById('test'))}>人生无味须尽欢</button>
        </div>
      );
    }

    }

    ReactDOM.render(< LifeCycle/>, document.getElementById('test'))
```



### **2.7.2. 理解**

1) 组件对象从创建到死亡它会经历特定的生命周期阶段

2) React组件对象包含一系列的勾子函数(生命周期回调函数), 在生命周期特定时刻回调

3) 我们在定义组件时, 可以重写特定的生命周期回调函数, 做特定的工作

### **2.7.3. 生命周期流程图**

![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\ksohtml\wps1B73.tmp.jpg)

### **2.7.4. 生命周期详述**

1) 组件的三个生命周期状态:

​    * Mount：插入真实 DOM  （挂载）

​    * Update：被重新渲染

​    * Unmount：被移出真实 DOM

2) React 为每个状态都提供了勾子(hook)函数

​    * componentWillMount()

​    * componentDidMount()

​    * componentWillUpdate()

​    * componentDidUpdate()

​    * componentWillUnmount()

3) 生命周期流程:

a. 第一次初始化渲染显示: ReactDOM.render()

​      * constructor(): 创建对象初始化state

​      * componentWillMount() : 组件将要挂载（插入）回调 (虚拟DOM将要被插入到真实DOM里头)

​      * render() : 用于插入虚拟DOM回调

​      * componentDidMount() : 已经插入回调

b. 每次更新state: this.setSate()

​      * componentWillUpdate() : 将要更新回调

​      * render() : 更新(重新渲染)

​      * componentDidUpdate() : 已经更新回调

c. 移除组件: ReactDOM.unmountComponentAtNode(containerDom)

​      * componentWillUnmount() : 组件将要被移除回调

### **2.7.5. 重要的勾子**

1) render(): 初始化渲染或更新渲染调用（观察者模式，自动监测）

2) componentDidMount(): 开启监听, 发送ajax请求（一些异步任务都可以在这里处理）

3) componentWillUnmount(): 组件将被卸载，移除。做一些收尾工作, 如: 清理定时器

4) componentWillReceiveProps(): 后面需要时讲(在获取GitHub的用户名的用户输入的搜索名在这个状态发送ajax，这个时候，发送ajax请求是最快的。)



## **2.8. 虚拟DOM与DOM Diff算法**

### **2.8.1. 效果**

![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\ksohtml\wps1B74.tmp.png)



```
  class HelloReact extends React.Component {
    constructor(props){
      super(props);
      this.state = {
        date:new Date()
      }

    }
    componentDidMount (){
      setInterval(()=>{
        this.setState({
          date:new Date()
        })
      },1000)
    }
    render(){
      return (
        <p>
          Hello, <input type="text" placeholder="Your name here"/>!
          It is {this.state.date.toTimeString()}
        </p>
      )
    }
  }
ReactDOM.render(<HelloReact/>, document.getElementById('test'))

 //从这个例子可以知道，当我在input中输入一些数据，这个时候并不会input也重新渲染，可知，他是部分different渲染的

```



### **2.8.2. 基本原理图**

![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\ksohtml\wps1B75.tmp.jpg)



# **第3章：react应用(基于react脚手架)**

## **3.1. 使用create-react-app创建react应用**

### **3.1.1. react脚手架**

1) xxx脚手架: 用来帮助程序员快速创建一个基于xxx库的模板项目

a. 包含了所有需要的配置

b. 指定好了所有的依赖

c. 可以直接安装/编译/运行一个简单效果

2) react提供了一个用于创建react项目的脚手架库: **create-react-app**

3) 项目的整体技术架构为:  react + webpack + es6 + eslint

4) 使用脚手架开发的项目的特点: 模块化, 组件化, 工程化

### **3.1.2. 创建项目并启动**

npm install -g create-react-app

create-react-app hello-react

cd hello-react

npm start

### **3.1.3. react脚手架项目结构**

ReactNews

​	|--node_modules---第三方依赖模块文件夹

​	|--public

​		*|--* *index.html**-----------------主页面*

​	|--scripts

​		*|--* *build.js**-------------------bui**ld**打包引用配置*

​	*|--* *start.js**-------------------**start**运行引用配置*

​	|--src------------源码文件夹

​		*|--components--**----**-----------react组件*

​		*|--**index.js**-----**----**----------应用入口js*

​	|--.gitignore------git版本管制忽略的配置

​	|--package.json----应用包配置文件

​	|--README.md-------应用描述说明的readme文件



## **3.2. demo: 评论管理**

### **3.2.1. 效果**

![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\ksohtml\wps1B85.tmp.png)

### **3.2.2. 拆分组件**

应用组件: App

\* state: comments/array

添加评论组件: CommentAdd

\* state: username/string, content/string

\* props: add/func

评论列表组件: CommentList

\* props: comment/object, delete/func, index/number

评论项组件: CommentItem

\* props: comments/array, delete/func

### **3.2.3. 实现静态组件**



### **3.2.4. 实现动态组件**

动态展示初始化数据

\* 初始化状态数据

​	* 传递属性数据

响应用户操作, 更新组件界面

​	* 绑定事件监听, 并处理

​	* 更新state



# React服务器端渲染入门

- 理解

  - 当服务器端接收到请求时, 在服务器端基于React动态渲染页面, 并返回给浏览器显示（也就是说，我渲染的流程放在服务器端实现了）
  - 相对于浏览器端渲染的好处?
    - 服务器端和客户端可以共享某些代码，避免重复定义。
    - 首次加载页面的速度加快
    - 便于SEO优化。服务器端渲染可以让搜索引擎更容易读取页面的meta信息以及其他SEO相关信息（就像Alt和title Alt就是为搜索引擎来保护的，而title是可有可无的）
  - 相对于浏览器端渲染的不好?
    - 对服务器的压力增大
    - 要求服务器使用基于node搭建，不能用Java和PHP去搭建。

- 简单编码实现服务器端渲染

  - 应用文件结构

    ```
    react-node
      |-- src
          |-- App.js-----------------主组件js
          |-- server.js--------------启动服务器监听, 处理请求的js
      |-- index.js---------入口js
      |-- .babelrc---------babel配置文件
      |-- package.json-----应用包信息文件
    ```

  - 编码

    - package.json

      ```
      {
        "name": "react-node",
        "version": "1.0.0",
        "scripts": {
          "start": "node index"
        },
        "devDependencies": {
          "babel-preset-es2015": "^6.6.0",
          "babel-preset-react": "^6.5.0",
          "babel-register": "^6.8.0"
        },
        "dependencies": {
          "react": "^15.3.1",
          "react-dom": "^15.3.1"
        }
      }
      ```

    - .babelrc

      ```
      {
        "presets": ["react", "es2015"]
      }
      ```

    - App.js

      ```
      import React, {Component} from 'react'
      class App extends Component {

        render() {
          return (
            <div>测试React服务器</div>
          )
        }
      }
      export default App
      ```

    - server.js

      ```
      import React from 'react';
      import { renderToString } from 'react-dom/server';
      var http = require('http');
      import App from './App';

      //创建服务器对象, 并启动监听
      http.createServer(function (request, response) {
        //向浏览器端写头信息
        response.writeHead(200, {'Content-Type': 'text/html'});
        //渲染组件成标签结构字符串
        const appHTML = renderToString(<App />);
        //向浏览器返回结果
        response.end(appHTML);
      }).listen(8888);
      // 终端打印提示信息
      console.log('Server running at http://127.0.0.1:8888/');
      ```

    - index.js

      ```
      require('babel-register');
      require('./src/server.js');
      ```

  - 启动服务器运行:

    - 命令: npm start
    - 访问: http://127.0.0.1:8888



# 第4章：react ajax

## **4.1. 理解**

### **4.1.1. 前置说明**

1) React本身只关注于界面, 并不包含发送ajax请求的代码

2) 前端应用需要通过ajax请求与后台进行交互(json数据)

3) react应用中需要集成第三方ajax库(或自己封装)

### **4.1.2. 常用的ajax请求库**

1) jQuery: 比较重, 如果需要另外引入不建议使用

2) axios: 轻量级, 建议使用

a. 封装XmlHttpRequest对象的ajax

b.  promise风格（返回一个promise）

c. 可以用在浏览器端和node服务器端

3) fetch: 原生函数, 但老版本浏览器不支持（兼容性没有axios好）（中间要先处理一下，res.json()）

a. 不再使用XmlHttpRequest对象提交ajax请求

b. 为了兼容低版本的浏览器, 可以引入兼容库fetch.js

### **4.1.3. 效果**

需求:
  1. 界面效果如下
  2. 根据指定的关键字在github上搜索匹配的最受关注的库
  3. 显示库名, 点击链接查看库
  4. 测试接口: https://api.github.com/search/repositories?q=r&sort=stars

		![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\ksohtml\wps1B86.tmp.png)

## **4.2. axios**

### **4.2.1. 文档**

<https://github.com/axios/axios>

### **4.2.2. 相关API**

1) GET请求

```
axios.get('/user?ID=12345')
  .then(function (response) {
    console.log(response);
  })
  .catch(function (error) {
    console.log(error);
  });

axios.get('/user', {
    params: {
      ID: 12345
    }
  })
  .then(function (response) {
    console.log(response);
  })
  .catch(function (error) {
    console.log(error);
  });
```

2) POST请求

```
axios.post('/user', {
    firstName: 'Fred',
    lastName: 'Flintstone'
})
.then(function (response) {
  console.log(response);
})
.catch(function (error) {
  console.log(error);
});
```



## **4.3. Fetch**

### **4.3.1. 文档**

1) <https://github.github.io/fetch/>

2) <https://segmentfault.com/a/1190000003810652>

### **4.3.2. 相关API**

1) GET请求

```
fetch(url).then(function(response) {
  return response.json()
}).then(function(data) {
  console.log(data)
}).catch(function(e) {
  console.log(e)
});
```

2) POST请求

```
fetch(url, {
  method: "POST",
  body: JSON.stringify(data),
}).then(function(data) {
  console.log(data)
}).catch(function(e) {
  console.log(e)
})
```



## **4.4. demo: github users**

### **4.4.1. 效果**

![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\ksohtml\wps1B97.tmp.png)

### **4.4.2. 拆分组件**

App

​		* state: searchName/string

​    Search

​      	* props: setSearchName/func

​    List

​      	* props: searchName/string

​      	* state: firstView/bool, loading/bool, users/array, errMsg/string

### **4.4.3. 编写静态组件**

### **4.4.4. 编写动态组件**

**componentWillReceiveProps(nextProps): 监视接收到新的props, 发送ajax**

**	使用axios库发送ajax请求**



# **第5章：几个重要技术总结**

## **5.1. 组件间通信**

### **5.1.1. 方式一: 通过props传递**（重要~）

1) 共同的数据放在父组件上, 特有的数据放在自己组件内部(state)

2) 通过props可以传递一般数据和函数数据, 只能一层一层传递

3) 一般数据-->父组件传递数据给子组件-->子组件读取数据

4) 函数数据-->子组件传递数据给父组件-->子组件调用函数（在父组件中定义函数，把这个函数用props的方式传给子组件）

### **5.1.2. 方式二: 使用消息订阅(subscribe)-发布(publish)机制**

1) 工具库: PubSubJS

2) 下载: npm install pubsub-js --save

3) 使用:

​	  import PubSub from 'pubsub-js' //引入

​	  **PubSub.subscribe('delete', function(msg,data){ }); //先订阅**

​	  **PubSub.publish('delete', data) //后发布消息**

### **5.1.3. 方式三: redux**

后面专门讲解

redux           mobx(是redux的替换方案)   ：统一状态管理

## **5.2. 事件监听理解**

### **5.2.1. 原生DOM事件**

1) 绑定事件监听

a. 事件名(类型): 只有有限的几个, 不能随便写

b. 回调函数

2) 	触发事件

a. 用户操作界面

b. 事件名(类型)

c. 数据()

### **5.2.2. 自定义事件(消息机制重要)**

1) 绑定事件监听

a. 事件名(类型): 任意

b. 回调函数: 通过形参接收数据, 在函数体处理事件

2) 触发事件(编码)

a. 事件名(类型): 与绑定的事件监听的事件名一致

b. 数据: 会自动传递给回调函数

**这样的思想在订阅发布（组件间的通信法2）和socketIO是同样的思想。**

## **5.3. ES6常用新语法**

1) 定义常量/变量:  const/let

2) 解构赋值: let {a, b} = this.props   import {aa} from 'xxx'

3) 对象的简洁表达: {a, b}

4) 箭头函数:

a. 常用场景

\* 组件的自定义方法: xxx = () => {}

\* 参数匿名函数

b. 优点:

​		* 简洁

​		* 没有自己的this,使用引用this查找的是外部this

5) 扩展(三点)运算符: 拆解对象(const MyProps = {}, <Xxx {...MyProps}>)

思考为啥能拆？我们ES6只能拆数组，因为数组有迭代器，但是对象是没有的。但是react一定将对象可迭代化了

6) 类:  class/extends/constructor/super

7) ES6模块化:  export default | import





# **第6章：react-router4**

## **6.1. 相关理解**

### **6.1.1. react-router的理解**

1)     react的一个插件库

2) 	专门用来实现一个**SPA**(单页应用)应用

3) 	基于react的项目基本都会用到此库

### **6.1.2. SPA的理解**

1)     单页Web应用（single page web application，SPA）

2) 	整个应用只有一个完整的页面

3) 	**点击页面中的链接不会刷新页面, 本身也不会向服务器发请求**（优点）

4) 	当点击路由链接时, 只会做页面的局部更新

5) 	数据都需要通过ajax请求获取, 并在前端异步展现

### **6.1.3. 路由的理解**

1) 什么是路由?

a. **一个路由就是一个映射关系(key:value)**

b. **key为路由路径, value可能是function-->后台路由/component-->前台路由**

2) 路由分类

a. 后台路由: node服务器端路由, value是function, 用来处理客户端提交的请求并返回一个响应数据

b. 前台路由: 浏览器端路由, value是component, 当请求的是路由path时, 浏览器端前没有发送http请求, 但界面会更新显示对应的组件

3) 后台路由

a. 注册路由: router.get(path, function(req, res))

b. 当node接收到一个请求时, 根据请求路径找到匹配的路由, 调用路由中的函数来处理请求, 返回响应数据

后端路由的主要作用就是发送请求，接受请求，返回响应。那么他有三个组成，请求方式，路径URI，句柄回调函数。

4) 	前端路由

a. 注册路由: <Route path="/about" component={About}>

b. 当浏览器的hash变为#about时, 当前路由组件就会变为About组件

优点：刷新页面不发送请求，但**会改变历史记录。**

> 从路由的组成概念中引出前端路由与后台路由的分类
>
>

### **6.1.4. 前端路由的实现**

1) history库

a. 网址: <https://github.com/ReactTraining/history>

b. 管理浏览器会话历史(history)的工具库

c. 包装的是原生BOM中window.history和window.location.hash

2) history API

a. History.createBrowserHistory(): 得到封装window.history的管理对象--用的比较多

b. History.createHashHistory(): 得到封装window.location.hash的管理对象

c. history.push(路径): 添加一个新的历史记录

d. history.replace(路径): 用一个新的历史记录替换**当前的记录**

e. history.goBack(): 回退到上一个历史记录

f. history.goForword(): 前进到下一个历史记录

g. history.listen(function(location){}): 监视历史记录的变化

3) 测试

![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\ksohtml\wps1B98.tmp.png)   ![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\ksohtml\wps1B99.tmp.png)



```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>history test</title>
</head>
<body>
  <p><input type="text"></p>
  <a href="/test1" onclick="return push('/test1')">test1</a><br><br>
  <button onClick="push('/test2')">push test2</button><br><br>
  <button onClick="back()">回退</button><br><br>
  <button onClick="forword()">前进</button><br><br>
  <button onClick="replace('/test3')">replace test3</button><br><br>

  <script type="text/javascript" src="https://cdn.bootcss.com/history/4.7.2/history.js"></script>
  <script type="text/javascript">
    let history = History.createBrowserHistory() // 方式一
    // history = History.createHashHistory() // 方式二
    // console.log(history)

    function push (to) {
      history.push(to)
      return false
    }

    function back() {
      history.goBack()
    }

    function forword() {
      history.goForward()
    }

    function replace (to) {
      history.replace(to)
    }

    history.listen((location) => {
      console.log('请求路由路径变化了', location)
    })
  </script>
</body>
</html>
```



## **6.2. react-router相关API**

### **6.2.1. 组件**（记住这些一下都是组件---->路由组件）

1) <BrowserRouter>  路由器组件：分类管理路由

2) <HashRouter> 路由器带hash（#     改变#不触发网页重载。改变#会改变浏览器的访问历史）

3) <Route> 路由组件  注册路由

4) <Redirect>  重定向：重定向到组件

5) <Link>  相当于a标签（不会自动添加一个类）

6) <NavLink> 相当于a标签（他有自动添加一个类，可以通过这个类来设置CSS样式。activeClassName='你设置的类名'）

7) <Switch> 切换  （当提示不允许多个组件显示的时候用它）



### **6.2.2. 其它**

1) history对象

2) match对象

3) withRouter函数

**export default** **withRouter**(NavFooter) *//* *让非路由组件（一般组件）可以访问到路由组件的**API*

## **6.3. 基本路由使用**

### **6.3.1. 效果**

![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\ksohtml\wps1BA9.tmp.png)

### **6.3.2. 准备**

1) 下载react-router: npm install --save react-router@4

2) 引入bootstrap.css: <link rel="stylesheet" href="/css/bootstrap.css">

### **6.3.3. 路由组件: views/about.jsx**



```
import React,{Component} from 'react';

class About extends Component {
  render(){
    return (
      <h1>我是About组件的内容</h1>
    )
  }
}

export default About;
```

### **6.3.4. 路由组件: views/home.jsx**

```
import React,{Component} from 'react';
import {
  NavLink,
  Route,
  Redirect,
  Switch
} from 'react-router-dom'

import News from '../news/News';
import Message from '../message/Message';
class Home extends Component {
  render(){
    return (
      <div>
        <h2>Home组件内容</h2>
        <div>
          <ul className="nav nav-tabs">
            <li><NavLink to='/home/news' activeClassName='lvActive'>News</NavLink></li>
            <li><NavLink to='/home/message' activeClassName='lvActive'>Message</NavLink></li>
          </ul>
          <div>
            <Switch>
            <Route path='/home/news' component={News}/>
            <Route path='/home/message' component={Message}/>
             <Redirect to='/home/news' />
            </Switch>
          </div>
        </div>
      </div>
    );
  }
}
export default Home;

```



### **6.3.5. 包装NavLink组件: components/my-nav-link.jsx**



### **6.3.6. 应用组件: components/app.jsx**



```
import React, {Component} from 'react';
import {
  NavLink,
  Link,
  Route,
  Redirect,
  Switch
}from 'react-router-dom';
import About from '../../views/about/About';
import Home from  '../../views/home/Home';
import './lvActive.css';

//定义组件
class App extends Component {

  render () {
    return (
      <div>
        <div className="row">
          <div className="col-xs-offset-2 col-xs-8">
            <div className="page-header">
              <h2>React Router Demo</h2>
            </div>
          </div>
        </div>
        <div className="row">
          <div className="col-xs-2 col-xs-offset-2">
            <div className="list-group">
              <NavLink className="list-group-item" activeClassName="lvActive" to="/about">About</NavLink>
              <NavLink className="list-group-item" activeClassName="lvActive" to="/home">Home</NavLink>
            </div>
          </div>
          <div className="col-xs-6">
            <div className="panel">
              <div className="panel-body">
                <Switch>
                  <Route path="/about" component={About}/>
                  <Route path="/home" component={Home}/>
                  <Redirect to="/about"/>
                </Switch>
              </div>
            </div>
          </div>
        </div>
      </div>
    )
  }

}

//暴露出去
export default App;

```



### **6.3.7. 自定义样式: index.css**



```
.lvActive{
  background-color: #2e6da4!important;
  font-weight: bolder!important;
  color: white!important;
}
```



### **6.3.8. 入口JS: index.js**

```
import React from 'react';
import {render} from 'react-dom';
import {BrowserRouter as Router} from 'react-router-dom';
import App from './components/app/App';

//渲染组件
render(
  <Router>
  <App />
  </Router>, document.getElementById('app'));
```



## **6.4. 嵌套路由使用**

### **6.4.1. 效果**

![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\ksohtml\wps1BAA.tmp.png)

### **6.4.2. 二级路由组件: views/news.jsx**



```
import React,{Component} from 'react';

class News extends Component {

  state = {
    data:['ChinaNews','USANews','UANews']
  };

  render(){
    let {data} = this.state;
    return (
      <ul>
        {data.map((item,index)=>{
          return <li key={index}>{item}</li>
        })}
      </ul>
    )
  }
}

export default News;
```



### **6.4.3. 二级路由组件: views/message.jsx**



```
import React,{Component} from 'react';
import MsgDetail from '../msgdetail/MsgDetail';
import {
  Route,
  NavLink
} from 'react-router-dom';



class Message extends Component {
  state = {
    data:[]
  };
  //模拟ajax请求
  componentDidMount(){
    setTimeout(()=>{
      this.setState({
        data:[{id:1,message:'Message001'},
              {id:3,message:'Message003'},
              {id:9,message:'Message009'},
             ]
      })
    },2000)
  }

  render(){
   let {history} = this.props;
   let {data} = this.state;
    return (
      <div>
        <ul>
          {data.map((item,index)=>{
            return (
              <li key={index}>
                 <NavLink to={'/home/message/'+item.id}>{item.message}</NavLink>&nbsp;&nbsp;
                <button onClick={()=> history.push('/home/message/'+item.id)}>push</button>&nbsp;
                <button onClick={()=> history.replace('/home/message/'+item.id)}>replace</button>
              </li>
            )
          })}
        </ul>
     <button onClick={()=>history.goForward()}>前进</button>
     <button onClick={()=>history.goBack()}>后退</button>
     <Route path='/home/message/:id' component={MsgDetail}/>
      </div>
    )
  }
}

export default Message;
```



### **6.4.4. 一级路由组件: views/home.jsx**



## **6.5. 向路由组件传递参数数据**

### **6.5.1. 效果**

![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\ksohtml\wps1BBB.tmp.png)

### **6.5.2. 三级路由组件: views/message-detail.jsx**



```
import React,{Component} from 'react';

const data = [{id:1,title:'你说我的心在左边还是右边？',Content:'在你那边'},
  {id:3,title:'你说我的缺点是什么？',Content:'是缺点你'},
  {id:9,title:'我是9，你是3',Content:'除了你，还是你'}];

class MsgDetail extends Component {
  render(){
    let {id} = this.props.match.params;
    let result = data.find((result)=>result.id===id*1);
    return (
     <ul>
       <li>ID: {id}</li>
       <li>Title: {result.title}</li>
       <li>Content: {result.Content}</li>
     </ul>
    )
  }
}

export default MsgDetail;
```



### **6.5.3. 二级路由组件: views/message.jsx**





## **6.6. 多种路由跳转方式**

### **6.6.1. 效果**

![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\ksohtml\wps1BBC.tmp.png)

### **6.6.2. 二级路由: views/message.jsx**







# **第7章：react-ui**

## **7.1. 最流行的开源React UI组件库**

### **7.1.1. material-ui(国外)**

1) 	官网: [http://www.material-ui.com/#/](#/)

2) 	github: <https://github.com/callemall/material-ui>

### **7.1.2. ant-design(国内蚂蚁金服)**

1) 	PC官网: <https://ant.design/index-cn>

2) 移动官网: <https://mobile.ant.design/index-cn>

3) 	Github: <https://github.com/ant-design/ant-design/>

4) Github: <https://github.com/ant-design/ant-design-mobile/>

## **7.2. ant-design-mobile使用入门**

### **7.2.1. 效果**

![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\ksohtml\wps1BCD.tmp.png)

### **7.2.2. 使用create-react-app创建react应用脚手架**

​	npm install create-react-app -g

​	create-react-app antm-demo

​	cd antm-demo

​	npm start

### **7.2.3. 搭建antd-mobile的基本开发环境**

1) 	下载

npm install antd-mobile --save

2) src/App.jsx

```
import React, {Component} from 'react'
// 分别引入需要使用的组件
import Button from 'antd-mobile/lib/button'
import Toast from 'antd-mobile/lib/toast'

export default class App extends Component {
  handleClick = () => {
    Toast.info('提交成功', 2)
  }

  render() {
    return (
      <div>
        <Button type="primary" onClick={this.handleClick}>提交</Button>
      </div>
    )
  }
}
```

3) 	src/index.js

```
import React from 'react';
import ReactDOM from 'react-dom'
import App from "./App"
// 引入整体css
import 'antd-mobile/dist/antd-mobile.css'


ReactDOM.render(<App />, document.getElementById('root'))
```

4) 	index.html

```
<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, minimum-scale=1, user-scalable=no" />

<script src="https://as.alipayobjects.com/g/component/fastclick/1.0.6/fastclick.js"></script>
<script>
  if ('addEventListener' in document) {
    document.addEventListener('DOMContentLoaded', function() {
      FastClick.attach(document.body);
    }, false);
  }
  if(!window.Promise) {
    document.writeln('<script src="https://as.alipayobjects.com/g/component/es6-promise/3.2.2/es6-promise.min.js"'+'>'+'<'+'/'+'script>');
  }
</script>

```



### **7.2.4. 实现按需打包(组件js/css)**

1) 下载依赖包

yarn add react-app-rewired --dev

yarn add babel-plugin-import --dev

2) 修改默认配置:  

l package.json

```
"scripts": {
  "start": "react-app-rewired start",
  "build": "react-app-rewired build",
  "test": "react-app-rewired test --env=jsdom"
}
```

l config-overrides.js

```
const {injectBabelPlugin} = require('react-app-rewired');
module.exports = function override(config, env) {
  config = injectBabelPlugin(['import', {libraryName: 'antd-mobile', style: 'css'}], config);
  return config;
};
```

3) 编码

```
// import 'antd-mobile/dist/antd-mobile.css'

// import Button from 'antd-mobile/lib/button'
// import Toast from 'antd-mobile/lib/toast'
import {Button, Toast} from 'antd-mobile'
```



# **第8章：redux**

## **8.1. redux理解**

### **8.1.1. 学习文档**

1) 英文文档: <https://redux.js.org/>

2) 中文文档: <http://www.redux.org.cn/>

3) Github: <https://github.com/reactjs/redux>

### **8.1.2. redux是什么?**

1) redux是一个独立专门用于做状态管理的JS库(**不是react插件库**)

2) 它可以用在react, angular, vue等项目中, 但基本与react配合使用

3) 作用: **集中式管理react应用中多个组件共享的状态**

集中式管理：管理就是两种，一种是读取状态（从store）一种是更新状态（去触发dispatch，然后调用reducers函数，处理状态的函数）

状态放在哪里？看是一个组件需要这些状态还是一些组件需要使用这些状态。

如果只是一个组件需要，那么就直接放在这个组件上面，直接在本组件去管理state即可。

如果一些组件需要，那么就把这些状态统一放在父组件上。如果运用了redux那么就放在redux管理。两种情况的状态需要放在redux里管理：一，就是多个组件需要共享的状态（共享）；二，后台异步任务获取到的响应数据（后台）

更新状态的函数放哪？状态放哪，函数就放哪。

### **8.1.3. redux工作流程**

![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\ksohtml\wps1BDD.tmp.jpg)

![](C:\Users\Administrator\Desktop\小熊node\day19感冒真几把难受，讲了小熊说很难的redux。也还好就是比较绕，注意手动画图搞清楚各个模块的连接\redux的工作原理.png)

![](F:\截图软件图片保存\2018-07-16_095543.png)



### **8.1.4. 什么情况下需要使用redux**

1) 总体原则: 能不用就不用, 如果不用比较吃力才考虑使用

2) 	某个组件的状态，需要共享

3) 	某个状态需要在任何地方都可以拿到

4) 	一个组件需要改变全局状态

5) 	一个组件需要改变另一个组件的状态

## **8.2. redux的核心API**

### **8.2.1. createStore()**

1) 作用:

创建包含指定reducer的store对象

2) 编码:

import {createStore} from 'redux'

import counter from './reducers/counter'

const store = createStore(counter)

### **8.2.2. store对象**

1) 作用:

redux库最核心的管理对象

2) 它内部维护着:

​		state

​		reducer

3) 核心方法:

​		getState()

​		dispatch(action)

​		subscribe(listener)

4) 编码:

​		store.getState()

​		store.dispatch({type:'INCREMENT', number})

​		store.subscribe(render)

```
https://mp.weixin.qq.com/s/_u_gqFe3t8lAAxiN724gpg   getState的方法是异步的还是同步的。
```

```
class App extends React.Component {
  state = { val: 0 }

  componentDidMount() {
    this.setState({ val: this.state.val + 1 })
    console.log(this.state.val)

    this.setState({ val: this.state.val + 1 })
    console.log(this.state.val)

    setTimeout(_ => {
      this.setState({ val: this.state.val + 1 })
      console.log(this.state.val);

      this.setState({ val: this.state.val + 1 })
      console.log(this.state.val)
    }, 0)
  }

  render() {
    return <div>{this.state.val}</div>
  }
}

//结合上面分析的，钩子函数中的 setState 无法立马拿到更新后的值，所以前两次都是输出0，当执行到 setTimeout 里的时候，前面两个state的值已经被更新，由于 setState 批量更新的策略， this.state.val 只对最后一次的生效，为1，而在 setTimmout 中 setState 是可以同步拿到更新结果，所以 setTimeout 中的两次输出2，3，最终结果就为 0, 0, 2, 3 。
```

```
react中setState是同步的还是异步？？？？？？？？
1.setState 只在合成（自定义）事件和钩子函数中是“异步”的，在原生事件和 setTimeout 中都是同步的。
2.setState的“异步”并不是说内部由异步代码实现，其实本身执行的过程和代码都是同步的，只是合成事件和钩子函数的调用顺序在更新之前，导致在合成事件和钩子函数中没法立马拿到更新后的值，形式了所谓的“异步”，当然可以通过第二个参数 setState(partialState, callback) 中的callback拿到更新后的结果。
3.如果对同一个值进行多次 setState ， setState 的批量更新策略会对其进行覆盖，相同的key会被覆盖，只会对最后一次的 setState 进行更新，取最后一次的执行，如果是同时 setState 多个不同的值，在更新时会对其进行合并批量更新。
```



### **8.2.3. applyMiddleware()**

1) 作用:

应用上基于redux的中间件(插件库)

2) 编码:

import {createStore, applyMiddleware} from 'redux'

import thunk from 'redux-thunk'  // **redux异步中间件**

const store = createStore(

  counter,

  applyMiddleware(thunk) // **应用上异步中间件**

)

### **8.2.4. combineReducers()**

1) 作用:

合并多个reducer函数

2) 编码:

export default combineReducers({

  user,

  chatUser,

  chat

})

## **8.3. redux的三个核心概念**

### **8.3.1. action**

1) 标识要执行行为的对象

2) 包含2个方面的属性

a. type: 标识属性, 值为字符串, 唯一, 必要属性

b. xxx: 数据属性, 值类型任意, 可选属性

3) 例子:

​		const action = {

​			type: 'INCREMENT',

​			data: 2

​		}

4) **Action Creator(创建Action的工厂函数)**使用分别暴露

​		const increment = (number) => ({type: 'INCREMENT', data: number})

### **8.3.2. reducer**

1) 根据老的state和action, 产生新的state的**纯函数**

2) 样例

​		export default function counter(state = 0, action) {

​		  switch (action.type) {

​		    case 'INCREMENT':

​		      return state + action.data

​		    case 'DECREMENT':

​		      return state - action.data

​		    default:

​		      return state

​		  }

​		}

3) 注意

a. 返回一个**新的状态**

b. **不要修改原来的状态**

### **8.3.3. store**

1) 将state,action与reducer联系在一起的对象

2) 如何得到此对象?

​		import {createStore} from 'redux'

​		import reducer from './reducers'

​		const store = createStore(reducer)

3) 此对象的功能?

​		getState(): 得到state

​		dispatch(action): 分发action, 触发reducer调用, 产生新的state

​		subscribe(listener): 注册监听, 当产生了新的state时, 自动调用

## **8.4. 使用redux编写应用**

### **8.4.1. 效果**

![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\ksohtml\wps1BDE.tmp.png)

### **8.4.2. 下载依赖包**

npm install --save redux

### **8.4.3. redux/action-types.js**

```
/*
action对象的type常量名称模块
 */
export const INCREMENT = 'increment'
export const DECREMENT = 'decrement'
```



### **8.4.4. redux/actions.js**



```
/*
action creator模块
 */
import {INCREMENT, DECREMENT} from './action-types'

export const increment = number => ({type: INCREMENT, number})
export const decrement = number => ({type: DECREMENT, number})
```



### **8.4.5. redux/reducers.js**



```
/*
根据老的state和指定action, 处理返回一个新的state
 */
import {INCREMENT, DECREMENT} from '../constants/ActionTypes'

import {INCREMENT, DECREMENT} from './action-types'

export function counter(state = 0, action) {
  console.log('counter', state, action)
  switch (action.type) {
    case INCREMENT:
      return state + action.number
    case DECREMENT:
      return state - action.number
    default:
      return state
  }
}
```



### **8.4.6. components/app.jsx**



```
/*
应用组件
 */
import React, {Component} from 'react'
import PropTypes from 'prop-types'
import * as actions from '../redux/actions'

export default class App extends Component {

  static propTypes = {
    store: PropTypes.object.isRequired,
  }

  increment = () => {
    const number = this.refs.numSelect.value * 1
    this.props.store.dispatch(actions.increment(number))
  }

  decrement = () => {
    const number = this.refs.numSelect.value * 1
    this.props.store.dispatch(actions.decrement(number))
  }

  incrementIfOdd = () => {
    const number = this.refs.numSelect.value * 1

    let count = this.props.store.getState()
    if (count % 2 === 1) {
      this.props.store.dispatch(actions.increment(number))
    }
  }

  incrementAsync = () => {
    const number = this.refs.numSelect.value * 1
    setTimeout(() => {
      this.props.store.dispatch(actions.increment(number))
    }, 1000)
  }

  render() {
    return (
      <div>
        <p>
          click {this.props.store.getState()} times {' '}
        </p>
        <select ref="numSelect">
          <option value="1">1</option>
          <option value="2">2</option>
          <option value="3">3</option>
        </select>{' '}
        <button onClick={this.increment}>+</button>
        {' '}
        <button onClick={this.decrement}>-</button>
        {' '}
        <button onClick={this.incrementIfOdd}>increment if odd</button>
        {' '}
        <button onClick={this.incrementAsync}>increment async</button>
      </div>
    )
  }
}

```



### **8.4.7. index.js**



```
import React from 'react'
import ReactDOM from 'react-dom'
import {createStore} from 'redux'

import App from './components/app'
import {counter} from './redux/reducers'

// 根据counter函数创建store对象
const store = createStore(counter)

// 定义渲染根组件标签的函数
const render = () => {
  ReactDOM.render(
    <App store={store}/>,
    document.getElementById('root')
  )
}
// 初始化渲染
render()

// 注册(订阅)监听, 一旦状态发生改变, 自动重新渲染
store.subscribe(render)
```



### **8.4.8. 问题**

1) redux与react组件的代码耦合度太高

2) 编码不够简洁

所以用react-redux中的Provider和connect

## **8.5. react-redux**

先有redux这个库，然后再有react-redux这个库。使得使用redux更好的管理更简化的使用redux。

### 8.5.1. 理解

1) 一个react插件库

2) 专门用来简化react应用中使用redux

### **8.5.2. React-Redux将所有组件分成两大类**

1) UI组件

a. 只负责 UI 的呈现，不带有任何业务逻辑

b. 通过props接收数据(一般数据和函数)

c. **不使用任何 Redux 的 API**

d. 一般保存在components文件夹下

2) 容器组件

a. 负责管理数据和业务逻辑，不负责UI的呈现

b. **使用 Redux 的 API**

c. 一般保存在containers文件夹下

**容器组件：有使用connect的就是容器组件。**

### **8.5.3. 相关API**

1) Provider

**让所有组件都可以得到state数据**

<Provider store={store}>
    <App />
  </Provider>

2) connect()

**用于包装 UI 组件生成容器组件---->这个容器组件可以传递属性值（state，一些action的函数）给UI组件**

import { connect } from 'react-redux'
  connect(
    mapStateToprops,
    mapDispatchToProps
  )(Counter)

3) mapStateToprops()

将外部的数据（即state对象）转换为UI组件的标签属性
  const mapStateToprops = function (state) {
   return {
     value: state
   }
  }

4) mapDispatchToProps()

将分发action的函数转换为UI组件的标签属性

简洁语法可以直接指定为actions对象或包含多个action方法的对象

### **8.5.4. 使用react-redux**

1) 下载依赖包

npm install --save react-redux

2) redux/action-types.js

不变

3) redux/actions.js

不变

4) redux/reducers.js

不变

5) components/counter.jsx

```
/*
UI组件: 不包含任何redux API
 */
import React from 'react'
import PropTypes from 'prop-types'

export default class Counter extends React.Component {

  static propTypes = {
    count: PropTypes.number.isRequired,
    increment: PropTypes.func.isRequired,
    decrement: PropTypes.func.isRequired
  }

  increment = () => {
    const number = this.refs.numSelect.value * 1
    this.props.increment(number)
  }

  decrement = () => {
    const number = this.refs.numSelect.value * 1
    this.props.decrement(number)
  }

  incrementIfOdd = () => {
    const number = this.refs.numSelect.value * 1
    let count = this.props.count
    if (count % 2 === 1) {
      this.props.increment(number)
    }
  }

  incrementAsync = () => {
    const number = this.refs.numSelect.value * 1
    setTimeout(() => {
      this.props.increment(number)
    }, 1000)
  }

  render() {
    return (
      <div>
        <p>
          click {this.props.count} times {' '}
        </p>
        <select ref="numSelect">
          <option value="1">1</option>
          <option value="2">2</option>
          <option value="3">3</option>
        </select>{' '}
        <button onClick={this.increment}>+</button>
        {' '}
        <button onClick={this.decrement}>-</button>
        {' '}
        <button onClick={this.incrementIfOdd}>increment if odd</button>
        {' '}
        <button onClick={this.incrementAsync}>increment async</button>
      </div>
    )
  }
}
```

6) containters/app.jsx

```
/*
包含Counter组件的容器组件
 */
import React from 'react'
// 引入连接函数
import {connect} from 'react-redux'
// 引入action函数
import {increment, decrement} from '../redux/actions'

import Counter from '../components/counter'

// 向外暴露连接App组件的包装组件
export default connect(
  state => ({count: state}),
  {increment, decrement}
)(Counter)
```

7) index.js

```
import React from 'react'
import ReactDOM from 'react-dom'
import {createStore} from 'redux'
import {Provider} from 'react-redux'

import App from './containers/app'
import {counter} from './redux/reducers'

// 根据counter函数创建store对象
const store = createStore(counter)

// 定义渲染根组件标签的函数
ReactDOM.render(
  (
    <Provider store={store}>
      <App />
    </Provider>
  ),
  document.getElementById('root')

```



### **8.5.5. 问题**

1) **redux默认是不能进行异步处理的,**

2) 应用中又需要在redux中执行异步任务(ajax, 定时器)



## **8.6. redux异步编程**

因为redux本身是没有操作异步的，故要引入redux-thunk插件来帮助我们异步的操作。

在未使用redux应用之前，我们是用react直接写的。而react本身是可以异步操作的。

action：

分为同步的action和异步的action

怎么区别：看有无回调函数。

同步的action：返回的一个对象

异步的action：返回的是一个dispatch回调函数，并且要主动分发同步的action。就像之前写的dispatch(get(commentsList))s

### 8.6.1. 下载redux插件(异步中间件)

npm install --save redux-thunk

### **8.6.2. index.js**（重要）



```
import {createStore, applyMiddleware} from 'redux'
import thunk from 'redux-thunk'
// 根据counter函数创建store对象
const store = createStore(
  counter,
  applyMiddleware(thunk) // 应用上异步中间件
)

```



### **8.6.3. redux/actions.js**（重要）



```
// 异步action creator(返回一个函数)
export const incrementAsync = number => {
  return dispatch => {
    setTimeout(() => {
      dispatch(increment(number))
    }, 1000)
  }
}
```



### **8.6.4. components/counter.jsx**



```
incrementAsync = () => {
  const number = this.refs.numSelect.value*1
  this.props.incrementAsync(number)
}
```



### **8.6.5. containers/app.jsx**



```
import {increment, decrement, incrementAsync} from '../redux/actions'
// 向外暴露连接App组件的包装组件
export default connect(
  state => ({count: state}),
  {increment, decrement, incrementAsync}
)(Counter)
```



## **8.7. 使用上redux调试工具**

### **8.7.1. 安装chrome浏览器插件**

![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\ksohtml\wps1BEF.tmp.png)

### **8.7.2. 下载工具依赖包**

npm install --save-dev redux-devtools-extension

### **8.7.3. 编码**



```
import { composeWithDevTools } from 'redux-devtools-extension'

const store = createStore(
  counter,
  composeWithDevTools(applyMiddleware(thunk))
)
```



## **8.8. 相关重要知识: 纯函数和高阶函数**

### **8.8.1. 纯函数**

1) 一类特别的函数: **只要是同样的输入，必定得到同样的输出**

2) 必须遵守以下一些约束  

a. 不得改写参数

b. 不能调用系统 I/O 的API

c. 能调用Date.now()或者Math.random()等不纯的方法  

3) **reducer函数必须是一个纯函数**

### **8.8.2. 高阶函数**

4) 理解: 一类特别的函数

a. 情况1: 参数是函数

b. 情况2: 返回是函数

5) 	常见的高阶函数:

a. 定时器设置函数

b. 数组的map()/filter()/reduce()/find()/bind()

c. react-redux中的connect函数

6) 	作用:

a. 能实现更加动态, 更加可扩展的功能
