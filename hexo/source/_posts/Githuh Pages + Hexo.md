---
title: Githuh Pages + Hexo 搭建个人博客
categories:
  - Hexo
tags:
  - Hexo 
# toc: true # 是否启用内容索引
---
# Githuh Pages + Hexo 搭建个人博客
## 本地git配置
### 配置本地git的用户信息

```c
git config --global user.name "Nate" 
git config --global user.email "287770626@qq.com" 
```
### 生成ssh密钥文件

```c
ssh-keygen -t rsa -C "287770626@qq.com"
```
期间会让你选择保存的目录，推荐使默认文件名，那么就会生成 id_rsa 和 id_rsa.pub 两个秘钥文件。
接着又会提示你输入两次密码（该密码是你push文件的时候要输入的密码，而不是github管理者的密码），当然，你也可以不输入密码，直接按回车。那么push的时候就不需要输入密码，直接提交到github上了。所以就是三个回车即可。

### 配置github的ssh

找到本地用户里面的id_rsa.pub，打开并且在Github Seting里面设置好ssh。

### 测试git与github关联情况

执行命令：ssh -T git@github.com

## 创建github pages 仓库

创建一个github page仓库，名字格式必须为

```
 username.github.io
```

## 克隆仓库到本地

```
git clone git@github.com:eagle230/nate.github.io.git
```

## 安装Hexo和Nodejs

### 安装Node.js

1、Node.js (Node.js 版本需不低于 10.13，建议使用 Node.js 12.0 及以上版本)
2、Git

### 安装Hexo

1.新建个blog目录，在此处执行cmd，

```
npm i hexo-cli -g 
```

开始安装hexo
2.输入npm install安装必备的组件
3.hexo g 生成静态
4.hexo s 开启服务
5.打开http://localhost:4000 
6.新建一篇博客，在cmd执行命令：

```
hexo new post “hello world”
```

7.在生成以及部署文章之前，需要安装一个扩展：

```
npm install hexo-deployer-git --save
```

8.编辑根目录下_config.yml文件

```
deploy:
  type: git
  repo: git@github.com:linton6/linton.github.io.git # 填写自己的仓库地址
  branch: master
```
9.加载博客样式文件 (搭建的时候遇到的坑)

需要修改_config.yml文件中的url地址和根目录

```  
url：是github Page给我们分配的网址
root：是搭建该博客的仓库名
```
10.更改主题
github下载好主题XXX后放在themes目录下，然后编辑站点的_config.yml中的theme: XXX
11.更改网页图标（更改完整路径，遇到的坑）

```
git clone git@github.com:cofess/hexo-theme-pure.git themes/pure
```
更改主题中

```
favicon: https://eagle230.github.io/nate.github.io/favicon.png
```

12.hexo g ，生成新的静态网页文件。
13.执行hexo d 上传到github上。
14.打开https://eagle230.github.io/nate.github.io/就看到了网页。

### 写博客

直接在port文件里面添加md格式的文件即可。

```
title: 文章标题
categories:
  - 文章分类
tags:
  - 文章标签
toc: true # 是否启用内容索引
```
参考链接：

[]: https://blog.csdn.net/linton1/article/details/90137367

