# hexoBlog
###### 1.拉取代码
```
$ git clone git@github.com:congcong93424/hexoBlog.git
$ cd hexo-blog
$ npm install
```

###### 2.安装hexo

```
$ npm install hexo-cli -g  全局安装hexo
```

###### 3.本地启动hexo
```
$ hexo server  可简写 hexo s
```
###### 4.新增文章
可在source/_posts/下新建md文件，也可用如下命令
```
$ hexo new xxx.md  //新建文章
```
###### 5.发布
```
$ hexo clean    清除缓存文件 (db.json) 和已生成的静态文件 (public)。在某些情况（尤其是更换主题后），如果发现您对站点的更改无论如何也不生效，您可能需要运行该命令。
$ hexo generate 或 hexo g 部署之前生成静态文件
$ hexo deploy   或 hexo d  部署网站。
```

> 当执行hexo deploy时，Hexo会创建或更新另外一个用于部署的分支，这个分支就是_config.yml配置文件中指定的分支。Hexo会将生成的站点文件推送至该分支下，并且完全覆盖该分支下的已有内容。因此，部署分支应当不同于写作分支。
