---
title: 记录Window搭建hexo博客过程
tags: hexo
categories: 博客 
---
**缘起老大要我搭建一个博客用于分享文章，遂有了下面的故事。。。**

#### <font color=red># 背景</font>

本次过程使用hexo的Next主题和github仓库管理代码，并关联github的单页功能，最后实现自动push仓库后自动更新到github单页里。这里安装git和node的过程就不再提了，不会的自行百度。

#### <font color=red># 安装hexo</font>
**1.安装hexo**
``` 
$ npm install hexo-cli -g  全局安装hexo
$ hexo init blog  初始化博客
$ cd blog  切换到blog目录
$ npm install 安装所需的依赖
$ hexo server  本地运行hexo项目 可用hexo s --debug带调试的简写模式，方便看到错误信息
```
<!--more-->
新建完成后，指定文件夹的目录如下：
```
├── _config.yml
├── package.json
├── scaffolds
├── source
|   └── _posts
└── themes
    └── landscape
```
运行hexo server后再浏览器地址栏输入localhost:4000即可看到默认的博客样式。

**2.更换hext主题**
在hero的根目录下打开git bash 输入如下命令后在themes文件夹下多出一个next文件夹，此为主题文件
```
git clone https://github.com/iissnan/hexo-theme-next themes/next themes/next
```
** 【注意：在hexo-blog和themes/next都有一个_config.yml的文件，为了区分。我们使用一下称呼】 **
** –根目录下/_config.yml:站点配置文件 **
** –themes/next/_config.yml:主题配置文件 **

打开站点配置文件 找到themes: 修改为 themes: next
打开主题配置文件 找到Schemes: 选择不同的样式主题。

3.新建分类
在项目根目录下输入如下命令新建分类文件
```
hexo new page catgegories
```
打开根目录下source/categotries/index.md输入如下内容
```
---
title: categories
date: 2019-01-03 15:29:26
type: "categories"
---
```

在主题配置文件找到 menu 如下所示
```
menu:
  home: / || home
  archives: /archives/ || archive
  categories: /categories/ || th
```

在站点配置文件找到输入language: zh-Hans
```
language: zh-Hans
```

接着在source/_posts/first.md新建first.md最顶部输入
```
---
title: 记录Window搭建hexo博客过程
tags: hexo
categories: 博客   //注释，这个代表此文章属于哪个分类下
---
```
保存md文件

#### <font color=red># github建立仓库</font>
新建github仓库后，在本地配置ssh key与github关联。进入项目文件目录
```
$ git init
$ git add .
$ git commit -m "你提交的说明"
$ git remote add origin 你新建的仓库地址
$ git push -u origin master
```
至此你已经把本地代码与github仓库关联。

#### <font color=red># 建立github单页项目</font>
在github主页新建仓库，name命名格式为你的GitHub的name.github.io  如 congcong.github.io


#### <font color=red># 本地hero一键部署功能</font>
npm安装hexo-deployer-git
```
$ npm install hexo-deployer-git --save
```
打开站点配置文件修改配置如下
```
deploy:
  type: git
  repo: <repository url> #git@github.com:congcong93424/congcong93424.github.io.git
  branch: master
```

输入如下命令即可将生成后的静态网页部署到github page
```
hexo clean   清除缓存文件 (db.json) 和已生成的静态文件 (public)。
在某些情况（尤其是更换主题后），如果发现您对站点的更改无论如何也不生效，您可能需要运行该命令。
hexo generate  部署之前生成静态文件
hexo deploy   部署网站。
```
最后等待一两分钟，在浏览器地址输https://congcong93424.github.io即可看到你自己的博客啦。

#### <font color=red># 自动化部署到github Pages</font>
*此功能与上者本地一键部署功能选一即可*
**Travis CI是一个持续集成的工具，它绑定Github上面的项目，只要有新的代码就会自动抓取。然后提供一个运行环境，执行测试，完成构建，还能部署到服务器**
*持续集成指的是只要代码有变更，就自动运行构建和测试，反馈运行结果。确保符合预期以后，再将新代码"集成"到主干。*  
*持续集成的好处在于，每次代码的小幅变更，就能看到运行结果，从而不断累积小的变更，而不是在开发周期结束时，一下子合并一大块代码。*

**1.登录 GitHub: Settings--> Developer settings--> Personal access tokens--> Generate new token --> 勾选第一项**
**2.进入travis ci官网https://travis-ci.org  github账号授权登陆**
**3.登陆后可以看到当前账号的所有公共代码仓库，开启需要自动化的项目**
**4.进入travis ci项目设置，在Environment Variables 中添加刚刚在github中生成得github_token.**
**5.在本地项目跟目录下新建.travis.yml文件，内容如下：**
```
language: node_js
node_js: stable

install:
  - npm install
script:
  - hexo g
after_script:
  - cd ./public
  - git init
  - git config user.name "congcong93424"
  - git config user.email "congcong@liveu.xin"
  - git add .
  - git commit -m "add/edit"
  - git push --force --quiet "https://${guthub_token}@${GH_REF}" master:master
branches:
  only:
    - master

cache:
  directories:
    - node_modules

env:
global:
  GH_REF: github.com/congcong93424/congcong93424.github.io
```
**6.完成上述配置后，hexo和trabvis环境就搭建好了，更新博客后Push到github仓库后，travis就已经开始为我们同步代码了**
**【小贴士，hexo有很多的插件可以用，上网查找试着装扮你的博客吧。】**
<!-- <img src="/images/1.png" width="400px" /> -->
 <!-- 9dc6efe819a86f80a52588a7a9729f20c6344c0d  -->
![图片](/images/1.png)
