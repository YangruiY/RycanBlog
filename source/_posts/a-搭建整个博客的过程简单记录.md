---
title: a-搭建整个博客的过程简单记录
tags: hexo
abbrlink: 19656
description: 演示搭建环境
date: 2023-06-21 03:19:51
sticky: 1
top_img: './img/6.jpg'
cover: './img/《白蛇2青蛇劫起》小青4k壁纸3840x2160_彼岸图网.jpg'
---
<meta name="referrer" content="no-referrer" />
# 基础

## 简单搭建

- [官网][http://nodejs.cn/]安装`nodejs`
- 安装 `git`    `brew install git`

- 查看nodejs版本     `npm -version`

- 安装cnpm 依赖于淘宝源：`npm install -g cnpm --registry=https://registry.npm.taobao.org`
- 查看cnpm 版本  `cnpm -v`
- 我使用` cnpm install -g hexo-cli`   出现了问题   但是  使用` npm install -g hexo-cli`可以
- 查看 `hexo -v`
- `mkdir RyCanBlog`
- `cd /Users/yangrui/RycanBlog`
- ` hexo init `      适当连接手机热点         
  - 安装成功： `INFO  Start blogging with Hexo!`
-  `  hexo s`  启动服务   `http://localhost:4000/`   平时写博客的时候可以进行`预览`
- `cd source/_posts`
- ` hexo n "搭建整个博客的过程简单记录"`  创建文章
- `vim 搭建整个博客的过程简单记录`
- ` cd /Users/yangrui/Z_RycanBlog`

- `hexo clean`
- `hexo g`
- `hexo s`  浏览

## 部署

- `Github ` 登录新建一个仓库，必须要和自己的用户名一样  ： 命名规则`XXX.github.io`
- `/Users/yangrui/Z_RycanBlog` 下安装插件`npm install --save hexo-deployer-git`

- 设置`vim _config.yml `     必须要是 ssh才能获取成功

  ```yml
  -- 最后の位置
  deploy:
    type: git
    repo: git@github.com:YangruiY/YangruiY.github.io.git 
    branch: main
  ```

- `hexo clean`
- `hexo g`
- `hexo d`

- 浏览器直接访问自己的`XXX.github.io` 即可

## 更换主题

`cd /Users/yangrui/Z_RycanBlog`

- 下载主题 `git clone https://github.com/litten/hexo-theme-yilia.git themes/yilia`
- 修改hexo根目录下的 `_config.yml` ： `theme: yilia`

- `vim _config.yml `

  ```yml
  ## Themes: https://hexo.io/themes/
  theme: yilia
  ```

- `hexo clean & hexo g &hexo s`

![成功效果](https://gitee.com/Ryang1118/typora/raw/master/images/202306210117794.png)

## 提升

- DIY定制化主题   `butteryfly`
- `npm install hexo-renderer-pug hexo-renderer-stylus --save`安装pug 以及 stylus 的渲染器

- `npm install hexo-abbrlink --save`   给每一篇文章来上一个属于自己的链接所需要的插件

- `vim _config.yml`

  ```yml
  #permalink: :year/:month/:day/:title/
  permalink: post/:abbrlink.html
  abbrlink:
  alg: crc32
  rep: hex
  ```

- 新建文章

  ```sh
  npm i hexo-deployer-git
  hexo new post "草稿"
  hexo cl && hexo g  && hexo d  && hexo s
  ```

  

```
menu:
  首页: https://haiyong.site/ || fas fas fa-home
  资源合集|| fas fa-tags: 
    免费资源: https://code.haiyong.site/ziyuan/free/ || fas fa-tools
    网站模板: https://code.haiyong.site/moban/ || fas fa-gamepad
    游戏源码: https://code.haiyong.site/ziyuan/game/ || fas fa-anchor
    编程资料: https://code.haiyong.site/program/ || fas fa-tools
    ppt模板: https://code.haiyong.site/ziyuan/ppt/ || fas fa-gamepad
    PC软件: https://code.haiyong.site/ziyuan/pc/ || fas fa-anchor
  导航||fas fa-list:
    源码资源库: https://code.haiyong.site/ || fas fa-tags
    学习资料: https://haiyong.site/doc/ || fas fa-folder-open
    时间线: /archives/ || fas fa-archive
    标签: /tags/ || fas fa-tags
  摸鱼||fas fa-fish:
    游戏: /moyu/ || fas fa-gamepad
    工具: /tools/ || fas fa-tools
    动画: /demo/ || fas fa-anchor
  摸鱼大军: /chat/ || fas fa-place-of-worship
  友人帐: /link/ || fas fa-link
  关于我: /about/ || fas fa-heart
```
