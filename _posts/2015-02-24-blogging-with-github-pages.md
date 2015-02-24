---
layout: post
category : blog
tags : [blog, github pages, jekyll, jekyll bootstrap]
title : "使用 GitHub Pages 搭建博客"
---
{% include JB/setup %}

GitHub Pages 是 github 为其用户提供的功能，它允许用户为自己的项目创建项目首页。用户通过 github repository 的形式上传、管理、发布你的博客，无需数据库，不需要关注服务器，只需要关注博客内容本身即可。

# 概述

## GitHub Pages 类型

GitHub Pages 有两种基本类型：用户/组织页面以及项目页面。这两者基本是一致的，它们之间只有一些关键的差异点。两者都使用的是 HTTP 协议而不是 HTTPS ，不能使用它们来处理一些敏感的信息；即便这个仓库是私有的，其发布后的页面也是公开的，所有人都能访问。

### User & Organization Pages

每个用户或组织都可以为自己创建唯一一个用户/组织页面，这个页面使用名称类似 *username.github.io* 的唯一仓库。注意：

* 你需要创建仓库 *username.github.io* ，其中 *username* 就是你的账号名称
* 必需使用 *master* 分支来创建和发布 GitHub Pages 页面。

当你的用户/组织页面创建后，用户就可以通过 *http(s)://\<username\>.github.io* 来访问你的页面了。

### Project Pages

项目页面与用户/组织页面不同，它和项目使用同一个 repository 。可以通过 *http(s)://\<username\>.github.io/\<projectname\>* （用户）或 *http(s)://\<orgname\>.github.io/\<projectname\>* （组织）来访问这个项目页面。创建项目页面对于用户和组织来说方法是一样的。

项目页面与用户/组织页面基本一致，除了少许差异：

* 项目页面使用 *gh-pages* 分支来创建、发布页面
* 如果没用使用自定义域名的话，项目页面只能通过用户页面站点的子路径来访问： *username.github.io/projectname*
* 在给用户/组织页面设置自定义域名后，账户下所有项目的页面都会使用同样的域名重定向
* 当访问的链接不存在时，会跳转到用户/组织页面的 404 page。如果想对某个项目指定单独的 404 page，则必需使用自定义域名。

# 创建 GitHub Pages

GitHub 提供了自动创建 GitHub Pages的工具，方便用户简单创建页面；用户也可以选择手动创建 GitHub Pages。

## [自动创建][2]

自动创建用户/组织页面和创建项目页面不同；创建用户/组织页面首先需要以账户名称创建仓库 *username.github.io* ，而创建项目页面不需要如此。后面的步骤二者类似：

1. 首先进入仓库的设置页面：
  ![](/images/2015-02-24-01-repo-actions-settings.png)
2. 在 Options -> GitHub Pages 下，点击 "Automatic page generator" 按钮：
  ![](/images/2015-02-24-02.png)
3. 在 Markdown 编辑器中编辑你的页面内容
4. 点击 "Continue To Layouts" 按钮
5. 在接下来的页面中选择 GitHub 提供的主题，预览页面展示效果：
  ![](/images/2015-02-24-03-page-generator-picker.png)
6. 选定主题后，点击 "Publis page" 按钮，将页面发布出去：
  ![](/images/2015-02-24-04-page-generator-publish.png)

这样你的 GitHub Pages 就创建好了。

## [手动创建][3]

手动创建即用户自己创建、编辑HTML、Markdown等文档，使用git命令或其它工具，上传到 GitHub Pages 对应的repository下；区别在于用户/组织页面提交到 *master* 分支，而项目页面提交到对应项目的 *gh-pages* 分支。下面以项目页面为例讲下手动创建过程：

###1. 首先创建 GitHub Pages 仓库的clone：

    $ git clone github.com/user/repository.git
    # clone 项目页面仓库
    正克隆到 'repository'...
    remote: Counting objects: 3, done.
    remote: Total 3 (delta 0), reused 0 (delta 0)
    Unpacking objects: 100% (3/3), done.
    检查连接... 完成。

###2. 创建 *gh-pages* 分支：

    $ cd repository

    $ git checkout --orphan gh-pages
    # 创建一个没有父分支的 gh-pages 分支
    切换到一个新分支 'gh-pages'

    $ git rm -rf .
    # 将旧分支的内容都删除掉
    rm 'README.md'

###3. 现在添加内容并 push 到 GitHub

    $ echo "My Test GitHub Page" > index.html
    $ git add index.html
    $ git commit -a -m "my first page commit"
    $ git push origin gh-pages

你现在可以在网上浏览你的 GitHub Pages http://*user*.github.com/*repository* 了。

# Jekyll

Jekyll 是 GitHub Pages 所使用的静态页面生成工具，具体介绍可以参看[维基百科条目][5]及 [Jekyll官网][6]。Jekyll 支持 Markdown (或 Textile) 配合 Liquid 编写的文档，将其解析为静态页面并发布到网站。具体使用可查阅[官方文档][7]，或者国人翻译的[中文文档][8]，里面介绍的很详细。我们要做的就是编写符合 Jekyll 规范的文档，将之上传到 GitHub Pages repository，GitHub 会自动将文档解析并发布出去。现在有很多好的博客模板，我们不需要再从零开始构建博客，可以复用现有模板。

# Jekyll Bootstrap

Jekyll Bootstrap 给用户创建 Jekyll 网站提供了模板，用户可以很轻松的快速搭建自己的 Jekyll 博客：

###1. 首先将 jekyll bootstrap 代码 clone 到本地：

    $ git clone https://github.com/plusjade/jekyll-bootstrap.git username.github.io

###2. 切换到我们自己的 GitHub Pages 代码仓库：

    $ cd username.github.io
    $ git remote set-url origin git@github.com:username/username.github.com.git

###3. 在部署博客到 GitHub Pages 上之前，可以先在本地安装jekyll，预览博客的显示效果：

    $ sudo gem install jekyll
    $ jekyll serve -w

jekyll 的安装可以参看[Using Jekyll with Pages][10]：

在浏览器打开url ： [http://localhost:4000](http://localhost:4000 localhost:4000)

###4. 创建 Post

可以通过 rake 命令来创建 post：

    $ rake post title="My first post"

rake 命令会自动创建符合 jekyll post 名称规范并具有 YAML Front Matter 的文件。

###5. 创建 Page

同样使用 rake：

    $ rake page name="about.md"
    # 创建 ./about.md 文件

也可以创建嵌套的页面：

    $ rake page name="pages/about.md"
    # 创建 ./pages/about.md 文件

或者创建有 "pretty" 路径的页面：

    $ rake page name="pages/about"
    # 创建 ./pages/about/index.html 文件

rake 会自动创建拥有符合 jekyll 命名规范且拥有 YAML Front Matter 的页面文件。

###6. 修改内容后，上传 GitHub

    $ git add .
    $ git commit -m "blog content"
    $ git push origin master

提交 GitHub 后， GitHub 会自动重新解析 GitHub Pages 仓库中的文档，重新部署静态页面。

[1]: https://help.github.com/articles/user-organization-and-project-pages/ "User organization and project pages"

[2]: https://help.github.com/articles/creating-pages-with-the-automatic-generator/ "Creating Pages with the automatic generator"

[3]: https://help.github.com/articles/creating-project-pages-manually/ "Creating Project Pages manually"

[4]: https://help.github.com/articles/custom-404-pages/ "Custom 404 pages"

[5]: http://en.wikipedia.org/wiki/Jekyll_(software) "Jekyll(Wikipedia)"

[6]: http://jekyllrb.com/ "Jekyll Simple, blog-aware, static sites"

[7]: http://jekyllrb.com/docs/home/ "Jekyll Document"

[8]: http://jekyllcn.com/docs/home/ "Jekyll 文档"

[9]: https://github.com/xcatliu/jekyllcn

[10]: https://help.github.com/articles/using-jekyll-with-pages/ "Using Jekyll with Pages"
