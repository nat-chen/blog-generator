---
title: 使用 Hexo + GitHub 搭博客
date: 2018-04-03 21:45:16
tags: Hexo
---

## 搭建环境 + 创建第一篇博客

* 进入安全的目录，别再根目录下 (/) 瞎搞，只有 ~ 里面的目录才是可以碰的。
* 在 GitHub 中创建一个空 repo，名称为 ‘你的用户名.github.io’。
* `npm install -g hexo-cli` 安装 Hexo
* `hexo init myBlog`
* `cd myBlog`
* `npm i`
* `hexo new 开博大吉`，生成一个 md 文件的路径
* 编辑此 md 文件
* 编辑网站配置：
  - 将 title 改成自己的想起的名
  - 将 author 改成自己的名字
  - 将最后一行的 type 改成 `type:git`
  - 在最后一行后面新增一行，左边也 type 平齐，加上一行 `repo: 仓库地址`。
* `npm install hexo-deployer-git --save`, 安装 git 部署插件。
* `hexo deploy`
* 进入 ‘你的用户名.github.io’ 对应的 repo，打开 GitHub Pages 功能，大功告成！

## 第二篇博客
* `hexo new 第二篇博客`
* 复制显示路径，编辑它
* `hexo generate`
* `hexo deploy`

## 换主题
* 选择喜欢的主题： https://github.com/hexojs/hexo/wiki/Themes
* 进入主题的 GitHub 首页，复制它的 SSH 地址
* `cd themes`
* `git clone git@github.com:iissnan/hexo-theme-next.git`
* `cd ..`
* _config.yml 修改 `theme: hexo-theme-next`
* `hexo generate`
* `hexo deploy`

## 上传源代码
留意 ‘你的用户名.github.io’ 上保存只是你的博客，并没有保存生成博客的程序代码。因此创建一个名为 blog-generator 的空仓库，以便保存 myBlog 里面生成博客的程序代码
* GitHub 创建 blog-generator 空仓库
* 根据 GitHub 向导完成后续指示
* 每次 `hexo deploy` 博客会更新，但要 add/commit/push 下 blog-generator


