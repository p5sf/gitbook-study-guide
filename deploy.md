## 项目发布

> [!Tip]
>
> 上述只能在本地运行，需要发布到[Github pages](https://pages.github.com/)用来托管静态网页

**文档打包**

命令结束后，，在项目下生成`_book`文件夹，这就是最终项目。
在此文件夹里有`index.html`文件，这个就是网页入口，把`_book`文件夹复制到服务器，即可完成文档网站的部署

```shell
$ gitbook build
```

项目提交

> [!NOTE]
>
> 由于gitbook生成的项目，文档和源码是两个部分，所以可以把文档放在master分支上，部署的网页放在gh-pages分支上

创建Github项目： `gitbook-study-guide`

上传项目文档

```shell
$ git add *
$ git commit -m "Ignore some files"
$ git branch -M master
$ git remote add origin git@github.com:p5sf/gitbook-study-guide.git
$ git push -u origin master
```

上传项目的源代码:将_book下的编译代码绑定到 gh-pages 上，自动推送

```shell
git subtree push --prefix=_book origin gh-pages
git subtree split --prefix=public -b gh-pages
```







## 自动发布

> [!tip]
>
> 每次都需要手动推送，非常麻烦，为了简单化可以写个脚本命令，自动化发布网页

先通过安装`gh-pages` 插件

```shell
$ npm i -D gh-pages
```

修改脚本文件

```shell
"scripts": {
  "deploy": "gh-pages -d build"
},
```

添加脚本文件 `deploy.sh`、并执行文件，如果看到`gh-pages`分支上有`index.html`文件，说明部署成功

```shell
#!/usr/bin/env sh
echo '开启自动化'
echo '执行命令：gitbook build .'
gitbook build .
echo "进入编译：cd ./_book\n"
cd ./_book
echo "初始化仓库\n"
git init
echo "添加所有文件\n"
git add -A
echo "项目提交\n"
git commit -m 'deploy'
echo "项目发布"
git push -f https://github.com/yulilong/book.git master:gh-pages
echo "回到上次工作目录"
cd -
```

