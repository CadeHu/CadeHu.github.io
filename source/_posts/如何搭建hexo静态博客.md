---
title: 如何搭建hexo静态博客
date: 2020-11-26 10:38:29
tags:
comment: true
categories: 
	- Nodejs
	- Hexo 
	- Git 
	- 静态博客
---

# <center><font color=red>Nodejs + Hexo + Git 搭建静态博客</font>    </center>

### 1. Nodejs和Git软件的安装

**Nodejs**：我这里版本是<a href="https://nodejs.org/en/" target="_blank">14.15.1</a>

**Git**：安装的是[Git-2.29.2.2](https://git-scm.com/download/win)

------

#### 1.1  **Nodejs**的环境配置：

这里主要是为了设置npm安装的全局模块路径和缓冲cache的配置，首先在**Nodejs**安装目录下创建【node_global】和【node_cache】

{% asset_img Nodejs.jpg  第一张本地照片 %}

在命令行【cmd】中设置**全局目录**和**缓冲目录**：

```bash
# 设置目录
npm config set prefix "D:\Nodejs\node_global"
# 设置缓冲区
npm config set cache "D:\Nodejs\node_cache"
```

------

#### 1.2  **设置环境变量**

用户变量中的**path**添加【D:\Nodejs\node_global】、系统变量里面增加变量【NODE_PATH】并设值【D:\Nodejs\node_modules】

------

#### **1.3  更换包管理工具—cnpm**

**Nodejs** 安装完了之后，又有自带的包管理工具**npm**下载速度慢，这里使用淘宝推出的一款包管理工具**cnpm**，在命令行下敲击如下代码：

用npm安装cnpm

```bash
npm install cnpm -g --registry=https://registry.npm.taobao.org
```

设置registry

```bash
npm config set registry https://registry.npm.taobao.org
```

读取registry

```bash
npm config get registry
```

下载需要的包

```bash
cnpm install [包名]
```

#### 1.4 Hexo框架的安装及使用

```bash
$ npm install hexo -g
	or
$ cnpm install -g hexo-cli
# 初始化hexo框架，生成基础文件
$ hexo init
# 清除缓存文件 db.json 和已生成的静态文件 public 
$ hexo clean 
# 创建新文件
$ hexo n <文件名>
# 生成静态文件
$ hexo g 
# 启动本地服务器，预览文章
$ hexo s
# 生成网站静态文件，并部署到设定的仓库
$ hexo d
```

至此，你已经完成了静态框架搭建

### 2. Git的操作

#### 2.1 Git 的基本概念

- **工作区：**就是你在电脑里能看到的目录。
- **暂存区：**英文叫 stage 或 index。一般存放在 **.git** 目录下的 index 文件（.git/index）中，所以我们把暂存区有时也叫作索引（index）。
- **版本库**: 工作区有一个隐藏目录 **.git** ，这个不算工作区，而是 Git 的版本库。

<center><img src="https://www.runoob.com/wp-content/uploads/2015/02/1352126739_7909.jpg" title="test"></center>

#### 2.2 Git  的操作命令

<center><img src="https://www.runoob.com/wp-content/uploads/2015/02/git-command.jpg" title="test"></center>



##### **常规操作**

```bash
1.初始化本地仓库
$ git init
2.将工作区的添加文件至缓冲区
$ git add <文件名>   
$ git add . # 将工作区所有文件添加缓冲区
3.提交文件至版本库
$ git commit -m "备注"
4.将本地库提交至远程库
$ git push origin master : master
6.指定默认主机(一般用于开始)
$ git push -u origin master
```

##### 创建ssh秘钥及连接远程仓库

```bash
# 创建SSH key
ssh-keygen -t rsa -C "1078316947@qq.com"
# github添加秘钥后，设置
git config --global user.name "yourname"
git config --global user.email "your_email@youremail.com"
#连接远程仓库
git remote add origin git@github.com:CadeHu/CadeHu.github.io.git 

# 连接之后将本地代码上传
git push -u origin <远程主机名> <本地分支名> : <远程分支名>

# 这里介绍一种特殊情况：
## 远程和本地仓库都有内容，需要将远程和本地合并
git pull origin master --allow-unrelated-histories
```

##### 删除远程库及强制操作

```bash
0. 删库
$ git push origin --delete <远程分支名>
$ git push origin -d <远程分支名>

1. git强制覆盖本地文件
$ git fetch --all && git reset --hard origin/master && git pull
2. git强制推送本地代码到远程仓库
$ git push -f origin master
```

##### **git branch**  和 **git checkout** 

```bash
$ git branch # 查看当前本地分支
$ git branch -r # 查看远程分支
$ git fetch origin # 手动远程更新仓库信息
$ git branch -a # 查看所有分支
$ git branch -d # 删除分支
$ git branch -m old_branch new_branch # 更改分支名
# 更改远程分支
git branch -m 旧分支名 新分支名

git push --delete origin 旧分支名

将新分支名推上去 
git push origin 新分支名

将新本地分支和远程相连 
git push --set-upstream origin 新分支名

# 切换分支
$ git checkout 分支名 # 切换到指定本地分支
$ git checkout -b 新分支名 # 创建并切换到新分支
例如：git checkout -b myRelease origin/Release
	作用是 checkout远程的Release分支，在本地起名为myRelease分支，并切换到本地的myRelase分支
```

##### **git push和git pull**的使用

```bash
$ git push <远程主机名> <本地分支名> : <远程分支名>
# 第一个master是本地分支名，第二个master是远程分支名
$ git push origin master:master

## 如果省略远程分支名，则会将本地分支上传至远程，并创建同名远程分支
$ git push origin master

## 如果省略本地分支名，则表示删除指定的远程分支
$ git push origin :master
## 等同于
$ git push origin -d master 


$ git pull <远程主机名> <远程分支名> : <本地分支名>
# 第一个master是远程分支名，第二个master是本地分支名
$ git pull origin master:master

## 如果省略本地分支名，则会将远程分支自动合并到当前所在分支
$ git pull origin master
```

##### 一些其他操作

```bash
$ git log # 查看git命令记录
$ git reset --hard <commit-id> # 强制回退到commit号的状态
$ git clone: url<https、ssh>  <本地目录>  # 下载资源包至指定的文件路径下
```

#### 2.3 问题解决

##### 出现本地仓库和远程仓库内容不一致

{% asset_img upload.jpg  第二张本地照片 %}

```bash
#    首先将本地文件添加本地库
git commit -m "last commit"
#    把本地仓库的变化连接到远程仓库主分支
git pull origin master
#    把本地仓库的文件推送到远程仓库
git push -u origin master 
```

##### 出现没有git开发工具问题

{% asset_img nogit.jpg  第三张本地照片 %}

```bash
git add .
git commit -m "备注"git
git push origin <远程分支名>
hexo clean && hexo g && hexo s
hexo d

其实就下面这行：
npm install --save hexo-deployer-git
如果安装cnpm：
cnpm install --save hexo-deployer-git
```

##### 博客中如何插入本地文件

```bash
## 安装插件
npm install https://github.com/CodeFalling/hexo-asset-image -- save
## 修改根目录下的配置文件_config.yml
post_asset_folder: true
## 在文章中插入
{% asset_img 文件名  第几张本地照片 %}
或者
![](文件名)
```

如果本地照片不显示，<a href="https://blog.csdn.net/xjm850552586/article/details/84101345" target="_blank">参考该文章</a>。

