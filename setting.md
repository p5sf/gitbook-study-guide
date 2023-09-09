# 项目配置

## 基本信息

创建配置文件并名为book.json，然后编译书籍

```json
{
    "author": "gitbook",		
    "title": " GitBook init",
    "description": "This is a book created by gitbook",
    "extension": null,
    "generator": "site",
    "links": {
        "sidebar": {
            "Gitbook Blog": "http://www.gitbook.cn"
        }
    },
      "styles": {
        "website": "styles/website.css",
        "ebook": "styles/ebook.css",
        "pdf": "styles/pdf.css",
        "mobi": "styles/mobi.css",
        "epub": "styles/epub.css"
    },
    "plugins": [],
  "pluginsConfig":{}
}
```

编译书籍

```shell
$ gitbook server
```

## 插件配置

> 通过 plugins 安装或删除(删除GitBook默认插件)，- 符号代表去除默认自带的插件，如下图

```js
"plugins": [
    "highlight",
    "-search",
    "back-to-top-button",
  	"tbfed-pagefooter",
  	"github",
]
```

Gitbook默认7个插件

- livereload 热加载插件
- highlight 语法高亮插件
- search 搜索插件
- lunr 搜索插件后台服务
- sharing 分享插件
- fontsettings 字体设置插件
- theme-default 主题

安装其他插件，方法一，直接在配置文件安装相应的插件，方法二：通过 npm 安装

```shell
gitbook install
npm install gitbook-plugin-xxx
```

插件配置

> [!Note]
>
> 安装一些插件之后，可能需要配置内容，例如配置页脚内容、Github

```json
"plugins": [
  	"tbfed-pagefooter",
  	"github",
]   
"pluginsConfig": {
        "tbfed-pagefooter": {
            "copyright":"Copyright &copy mine 2000-2020",
            "modify_label": "文件修订时间：",
            "modify_format": "YYYY-MM-DD HH:mm:ss"
        },
          "github": {
           	 "url": "https://github.com/zhangjikai"
       },
    }
```

修改配置文件后，需要重新安装插件

```shell
$ gitbook install
```

## 主题安装

添加[lou主题插件](https://www.npmjs.com/package/gitbook-plugin-theme-lou)，并重新安装

```js
{
  "plugins": ["theme-lou"],
  "pluginsConfig": {
    "theme-lou": {
      "color": "#FF4848", // 主题色
      "favicon": "static/favicon.ico", // favicon图标
      "logo": "static/logo.png", // 顶部左侧图标
      "appleTouchIconPrecomposed152": "static/apple.png", // apple图标
      "copyrightLogo": "assets/copyright.png",  // 底部水印LOGO
      "forbidCopy": true, // 页面是否禁止复制
      "search-placeholder": "Input Keywords to Search", // 搜索框默认文本
      "book-summary-title": "Article Directory", // 目录标题
      "book-anchor-title": "Search In the Article", // 本章目录标题
      "hide-elements": [".summary .gitbook-link", ".summary .divider"], // 需要隐藏的标签
      "copyright": {
        "author": "松露老师"  // 底部版权展示的作者名
      }
    }
  },
}
```

重新运行

```shell
$ gitbook serve
```

主题如下图

![img](https://camo.githubusercontent.com/d32438b40b77ad1a065297cbeaec8241f643ac48a0d6e81758bbcaaff54fd6ac/68747470733a2f2f747661312e73696e61696d672e636e2f6c617267652f3030386933736b4e677931677467333377626e62646a3631716d30753067716530322e6a7067)

## 插件大全

> [!Note]
>
> 记录一些常用的插件，每次安装插件都需要重新安装 gitbook install

参考如下：

- [Gitbook 插件使用教程](http://gitbook.zhangjikai.com/plugins.html)