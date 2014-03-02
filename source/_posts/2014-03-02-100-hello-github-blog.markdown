---
layout: post
title: "GitHub搭建博客"
date: 2014-03-02 16:14:29 +0800
comments: true
categories: [github,blog]
---
github博客搭建方法及常用命令
<!-- more -->
###博客搭建教程:
1. [搭建](http://beyondvincent.com/blog/2013/07/27/107-hello-page-of-github/)
2. [配置](http://biaobiaoqi.me/blog/2013/07/10/decorate-octopress/)  [另外一个配置](http://www.yanjiuyanjiu.com/blog/20130402/)
3. [octopress官网](http://octopress.org/docs/)
4. [在多台电脑上写Octopress博客](http://www.heqingbao.com/blog/2014/01/18/zai-duo-tai-dian-nao-shang-xie-octopressbo-ke/)
5. [博客主题github](https://github.com/imathis/octopress/wiki/3rd-Party-Octopress-Themes)
6. [理想的写作环境：Git+Github+Markdown+Jekyll](http://www.yangzhiping.com/tech/writing-space.html)
7. [语法高亮](http://octopress.org/docs/blogging/code/)

``` plain 博客常用命令
rake new_post["New Post"] 
rake generate
git add .
git commit -am "Some comment here." 
git push origin source
git preview
rake deploy
```



