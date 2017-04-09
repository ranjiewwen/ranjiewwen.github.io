---
layout: post
title: blog基本搭建完成
date: 2017-04-09 
tag: 环境搭建
---

## 目录

* TOC 
{:toc}

## Hexo 初体验

- 刚开始了解Hexo,希望搭建一个主页，自己也把基本的demo做出来了，但是主要缺点就是多台电脑上使用不方便。后面才了解的jekyll。
- [Diwei Liu](http://www.csuldw.com/) 感觉这种风格也不错
- 后面不知道自己犯了什么错误，始终命令有错误，就不想弄了，然后就转jekyll
- hexo绑定github的方法和jekyll还是有点区别的，Hexo配置文件仓库地址；jekyll直接push到仓库即可

## Jekyll 初体验

- 认真的读了很多jekyll的文章
- [Jekyll个人博客构建之路](http://lilian.info/blog/2016/12/HowToCreateBlog.html)
- [Jekyll搭建个人博客](http://baixin.io/2016/10/jekyll_tutorials1/)
- 基本的demo比较好搭建

## jekyll遇到的坑

- 环境Ruby和Jekyll等版本需要一致，将模板直接用可能有些文件替换，导致版本各个不一致，命名行有错，下面的界面最后的正确显示
<center><img src="/images/posts/20170409/1.png" width = "70%"/></center>
<center><img src="/images/posts/20170409/2.png" width = "70%"/></center>

- 开始主页一直不显示，以为模板替换有问题，弄了一天，才发现只是主页不显示，其他页面是可以显示的。
- 然后就只找主页为什么不显示，就是根目录下有index.md，是原来的；替换模板有index.html;然后生成_site目录以index.md为准，就没有内容；删除即可！

## 总结

- 要善于发现问题