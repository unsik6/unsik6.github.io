---
layout: post
title: Gitblog) jekyll bundler
subtitle: Setting Gitblog development environment
categories: GitBlog
tags: [GitBlog, Jekyll]
published: true
---
&nbsp;&nbsp;In this post, I introduce how to set Gitblog development enviroment using <i>Ruby</i> and <i>Jekyll bundler</i> in <u><i>Windows</i></u> OS. After setting, we can check the pages in `localhost:4000` befor publishing the pages.<br/>

## 1. Setting
<hr>

1. Install <i>Ruby+Dvkit</i> from <a href = "https://rubyinstaller.org/downloads/">RubyInstaller Downloads</a>. Select the recommended version that is emphasized.

    <img src = "https://user-images.githubusercontent.com/80208196/216691894-a2acebd1-5ee8-471a-b243-495f33c6fdfe.png"><br/>

2. Run the downloaded file. After install, Run the `ridk install`, and choose the options `MYSYS2 and MINGW development tool chain`.

    <img src = "https://user-images.githubusercontent.com/80208196/216692447-83d2887c-e264-404d-83cd-5018a414a843.png"><br/>

3. Run <i>Windows cmd</i>. And install jekyll bundler.

    <script src="https://gist.github.com/unsik6/ea72260b9f897e94c3515512f829ad58.js"></script>

## 2. Using
<hr>

1. Run <i>Windows cmd</i>. And go to the directory where your blog is.

    <script src="https://gist.github.com/unsik6/604a4269b4d08bad85d4075a1f92d92b.js"></script>

2. Input the command below. Then, you can watch your blog at `localhost:4000` using any browser.

    <script src="https://gist.github.com/unsik6/5a6da658b53da01a0af44639e57b2540.js"></script>

## Refers
<hr>
<a href = "https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/testing-your-github-pages-site-locally-with-jekyll">GitHub Docs</a><br/>
<a href = "https://zoomkoding.github.io/gitblog/2019/08/18/git-blog-2.html">줌코딩, "차근차근 Github 블로그 만들기(2) - Github 블로그 개발 환경 설정하기(Ruby, jekyll bundle 설치하기)"</a><br.>