---
title: hexo+github搭建个人博客
date: 2019-09-02 12:33:08
categories:
    - hexo
tags:
    - 个人博客
    - tech
    - hexo
---

什么是hexo?
hexo是Node.js 编写的静态博客框架，基于hexo我们可以快速的搭建出我们的个人博客。如果要详细了解hexo,请看这里 [hexo官网](http://www.hexo.io/docs)
<!--more-->
------
## 一、安装Node.js
1. windows安装Node.js 
1).windows 安装Node.js非常简单，只需要到[Node.js官网](https://nodejs.org/en/download/)下载安装包，然后双击打开一路下一步即可安装完毕。
2).将node.js添加进环境变量
3).安装淘宝镜像<code> npm install -g cnpm --registry=https://registry.npm.taobao.org</code>
<br>
2. linux安装Node.js
1).打开终端进入/usr/local执行<code>wget https://npm.taobao.org/mirrors/node/v10.16.3/node-v10.16.3-linux-x64.tar.xz</code>命令

2).下载成功后执行<code>tar -xvf node-v10.16.3-linux-x64.tar.xz</code>解压缩
3).执行<code>mv node-v10.16.3-linux-x64 nodejs</code>
4).建立软连接
   <code>ln -s /usr/local/nodejs/node /usr/local/bin/node</code>
   <code>ln -s /usr/local/nodejs/npm /usr/local/bin/npm</code>
执行完上述几步之后node就安装好了。
5).安装淘宝镜<code> npm install -g cnpm --registry=https://registry.npm.taobao.org</code>
<br>
3. mac安装Node.js
1).打开终端执行命令<code>brew install node</code>
2).安装淘宝镜像<code> npm install -g cnpm --registry=https://registry.npm.taobao.org</code>

---
## 二、安装hexo，搭建hexo博客本地环境
1. 安装好node.js和淘宝镜像之后，执行<code> cnpm install -g hexo </code>
2. 新建一个文件夹blog,进入blog下，执行<code>hexo init</code>
3. 安装完依赖包之后，执行<code>hexo s</code>,此时hexo本地服务就会启动，用浏览器打开"http://localhost:4000",就会看到如下页面。
![](http://px6vw3ifw.bkt.clouddn.com/hexo.jpg)

---
## 三、安装git，关联github
1. git的安装过程请参照这里 [git官方文档](https://git-scm.com/book/zh/v2/%E8%B5%B7%E6%AD%A5-%E5%AE%89%E8%A3%85-Git)
2. 注册一个github账号，如果你还没有账号点这里[github官网](https://github.com)注册,如果有账号请忽略这一步
3. 添加SSH key
打开git,执行<code>git config --global user.username 你的github用户名</code>，接着执行<code>git config --global user.email 你注册github时的邮箱</code>，然后执行<code>ssh-genkey -t rsa -C 你的邮箱</code>，此时会在C:\user\用户\ 目录下生成一个.ssh的文件夹,打开里面的id_rsa.pub文件把里面的内容全部复制到到下图红框内。
![](http://px6vw3ifw.bkt.clouddn.com/addkey.jpg)
打开git 执行<code>ssh -T git@github.com</code>,如出现以下界面说明已经添加成功。

![](http://px6vw3ifw.bkt.clouddn.com/gittest.jpg)
4. 有了github账号之后，登陆上github网站，然后按照下图步骤执行。

![](http://px6vw3ifw.bkt.clouddn.com/repo.jpg)
按照上图创建好仓库之后我们新建一个名为hexo的分支,把hexo设为默认分支。打开git把创建好的仓库克隆到本地，并把我们的hexo项目复制到仓库根目录下(这一步是为了后面我们异地更新博客做准备，因为hexo环境是在本地，我们部署到github的时候不会把我们的项目文件部署上去，所以我们需要创建一个分支来管理我们的项目文件，当我们用其他电脑更新博客的时候只需要把仓库克隆下来，在我们的hexo分支上更新博客即可)，确保我们当前在hexo分支，执行<code>git add . && git commit -m "first submit project files</code>。
打开blog目录下的_config.yml文件找到deploy项配置如下图
![](http://px6vw3ifw.bkt.clouddn.com/config.jpg)
然后执行<code> git add . && git commit -m "提交信息"</code>，再执行<code>hexo g -d</code>,将项目部署到github上去。此时你打开浏览器并在地址栏输入你的仓库名称应该就可以看到一下界面了。
![](http://px6vw3ifw.bkt.clouddn.com/hexo.jpg)
