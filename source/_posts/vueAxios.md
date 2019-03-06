---
title: axiso的使用
tags: vue
date: 2019-02-28 13:25
categories: vue
---
***
> "静下来的你才是真正的你，其余的一切都可以叫操劳。",

#### 1.axios
**Axios是一个基于promise的HTTP库，可以用在浏览器和Node.js中。**

* 从浏览器中创建 XMLHttpRequests
* 从 node.js 创建 http 请求
* 支持 Promise API
* 拦截请求和响应
* 转换请求数据和响应数据
* 取消请求
* 自动转换 JSON 数据
* 客户端支持防御 XSRF
<!--more-->
#### 2.安装
使用npm
> npm install axios

使用cdn
```
<script src="https://unpkg.com/axios/dist/axios.min.js"></script>
```
#### EXAMPLE
执行get请求
```
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
执行post请求
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

#### 统一封装axios请求
```
import axios from 'axios'

axios.defaults.headers.post['Content-Type'] = 'application/x-www-form-urlencoded'


axios.defaults.timeout = 5000;
// axios.defaults.baseURL ='http://www.liveu.xin';
// 请求拦截器
axios.interceptors.request.use(function(config){
    return config
}, function(error) {
    return Promise.reject(error)
})

// 响应拦截器
axios.interceptors.response.use(function(response){
    return response
},function(error){
    return Promise.reject(error)
})

export default {
    mockdata(url, params) {
        return new Promise((resolve, reject) => {
            axios.post(url, params).then(response => {
                resolve(response.data)
            }).catch((error) => {
                reject(error)
            })
        })
    }
}

export let reqMethodsPost = function(url,params) {
    return new Promise((resolve, reject) => {
        axios.post(url, params).then(response => {
            resolve(response.data)
        }).catch(error => {
            reject(error)
        })
    })
}
```
引用的时候就通过import axios from 'axios文件的位置'
或者 import { reqMethodsPost } from 'axios文件的位置'  来执行单个引入
