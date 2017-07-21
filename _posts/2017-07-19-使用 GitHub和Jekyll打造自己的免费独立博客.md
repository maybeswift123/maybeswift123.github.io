---
layout: post
title: 使用GitHub和Jekyll打造自己的免费独立博客
categories: [tech]
tags: [github,jekyll]
---

[GitHub](https://github.com/)是一个代码托管网站，现在很多开源项目都放在GitHub上。 利用GitHub，可以让全球各地的程序员们一起协作开发。GitHub 提供了一种功能，叫 [GitHub Pages](https://pages.github.com/), 利用这个功能，我们可以为项目建立网站，当然，这也意味着我们可以通过 GitHub Pages 建立自己的网站。

[Jekyll](http://jekyll.com.cn/)是一个简单的，针对博客设计的静态网站生成器。使用 GitHub 和 Jekyll，我们可以打造自己的独立博客，你可以自由地定制网站的风格，并且这一切都是免费的。

这是我在GitHub上个人博客的[源代码](https://github.com/maybeswift123/maybeswift123.github.io)。

# 入门指引

[GitHub Pages](https://pages.github.com/)的主页提供了一个简单的入门指引，阅读并操作一下，会有一个直观简单的认识。

阮一峰老师的文章《[搭建一个免费的，无限流量的Blog----github Pages和Jekyll入门](http://www.ruanyifeng.com/blog/2012/08/blogging_with_jekyll.html)》是使用 GitHub 和 Jekyll 搭建独立博客非常好的入门文章，强烈建议先阅读并操作一遍。
 # 建立自己的博客
在学习完阮一峰老师的文章后，你就已经有能力搭建自己的独立博客了，但是这个博客 只有最基本的功能，并且也不好看。这时候，你面临几个选择:

 1. 完全自己定制博客
 2. 找一份框架，修改后使用
 3. 从GitHub上fork别人的博客代码，在其中添加自己的文章
<!-- more -->
如果选择 2, 那么 jekyll-bootstrap是一个选择。 

如果选择 3, 那么自己Google一下 github.io 博客 能找到不少博客,去fork,然后修改一下就好。 最近有一个 jekyll-now，在 GitHub 上已经获取了 1000+ 的fork，可以关注一下。这个项目的特点是，所有操作都是通过网站进行的，不需要懂命令行。

如果选择 1, 那么可以好好看下后文的内容。
# GitHub + Jekyll 工作机制
### 机制一 
  简单地说，你在 GitHub 上有一个账号，名为username(任意)， 有一个项目，名为 username.github.io(固定格式，username与账号名一致)， 项目分支名为 master(固定)，这个分支有着类似下面的 目录结构:
<div class="message">
├── index.html  <br />
├── _config.yml  <br />
├── assets  <br />
│   ├── blog-images  <br />
│   ├── css  <br />
│   ├── fonts  <br />
│   ├── images  <br />
│   └── javascripts  <br />
├── _includes  <br />
├── _layouts  <br />
├── _plugins  <br />
├── _posts  <br />
└── _site  <br />
</div>
这样，当你访问 [http://username.github.io/] 时，GitHub 会使用 Jekyll 解析 用户 username名下的username.github.io项目中，分支为master 的源代码，为你构建一个静态网站，并将生成的 index.html 展示给你。

关于这个目录更多的内容，我们还不需要关心，如果你好奇心比较重，可以先看后文源代码一节。

看完上面的解释，你可能会有一些疑问，因为按照上面的说法，一个用户只能有一个 网站，那我有很多项目，每个项目都需要一个项目网站，该怎么办呢？另外，在阮一峰老师的文章中，特别提到，分支名应该为 gh-pages，这又是怎么回事呢？

原来，GitHub认为，一个GitHub账号对应一个用户或者一个组织，GitHub会 给这个用户分配一个域名：username.github.io，当用户访问这个域名时， GitHub会去解析username用户下，username.github.io项目的master分支， 这与我们之前的描述一致。

另外，GitHub还为每个项目提供了域名，例如，你有一个项目名为blog， GitHub为这个项目提供的域名为[username.github.io/blog] ， 当你访问这个域名时，GitHub会去解析username用户下，blog项目的gh-pages 分支。

所以，要搭建自己的博客，你可以选择建立名为 username.github.io的项目， 在master分支下存放网站源代码，也可以选择建立名为 blog 的项目，在 gh-pages分支下存放网站源代码。

GitHub 的 Help 文档中的[User, Organization and Project Pages](https://help.github.com/articles/user-organization-and-project-pages/)对此有 详细的描述。
### 机制二
Jekyll 提供了插件功能，在网站源代码目录下，有一个名为 <em>_plugins</em>的目录， 你可以将一些插件放进去，这样，Jekyll在解析网站源代码时，就会运行你的插件， 这样插件是 Ruby 写成的。可以为Jekyll添加功能，例如，Jekyll默认是不提供分类 页面的，你可以写一个插件，根据文章内容生成分类页面。如果没有插件，你只能每次写文章，添加分类时，为每个分类手动写 HTML 页面。

在本地运行 Jekyll 时，这些插件会自动被调用，但是GitHub在解析网站源代码时， 出于安全考虑，会开启安全模式，禁用这些插件。我们既想用这些插件，又想用 GitHub，怎么办呢？

GitHub还为我们提供了更一种解析网站的方式，那就是直接上传最终的静态网页， 这样，我们可以在本地使用 Jeklly 把网站解析出来，然后再上传到 GitHub上， 这就使得我们既使用了插件，又使用了 GitHub。在上文的目录结构中，有一个 名为<em> _site</em> 的目录，这个就是Jeklly在本地解析时最终生成的静态网站，我们 把其中的内容上传到 GitHub 的项目中就可以了。例如，我在GitHub上的网站， 既解析后的<em> _site</em> 目录，大概是这样的:
<div class="message">
├── index.html  <br />
├── 2016  <br />
├── 2017  <br />
├── assets  <br />
├── categories  <br />
├── page2  <br />
</div>
其中的 categories，2016, 2017 目录就是分类插件和归档插件帮助我生成的， 我只要把这个目录下的内容上传到 GitHub 相应的项目分支中就可以了。这样，你 访问 username.github.io时，GitHub就不解析了，直接把index.html返回给你了。

本文内容摘取自[on_1y](http://blog.csdn.net/on_1y/article/details/19259435) 的blog
