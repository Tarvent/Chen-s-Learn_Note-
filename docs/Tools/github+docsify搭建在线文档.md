# 一、docsify使用背景

一个好的开源软件必须要有一个完善的文档才容易被推广，那么我们在如何简单、高效、低成本的搭建一个文档网站呢？今天我们使用Github+docsify来零成本轻松打造一个在线文档系统！

不同于 GitBook、Hexo 的地方是它不会生成静态的 `.html` 文件，所有转换工作都是在运行时。只需要创建一个 `index.html` 就可以开始编写文档并直接[部署在 GitHub Pages](https://docsify.js.org/#/zh-cn/deploy)。

vue的官方文档也是使用docsify搭建的：[https://cn.vuejs.org](https://cn.vuejs.org/)

# 二、安装docsify

## 1、安装node和npm

这就不详细说了，网上一搜一大堆。这边给个链接。

https://www.cnblogs.com/xilifeng/p/5538711.html

## 2、全局安装docsify

```javascript
npm i docsify-cli -g
```

注：mac中需要使用root权限，需要加上sudo。

# 三、使用docsify创建文档网站

## 1、在github中新建一个项目

这个项目用来存放我们的文档内容，后面通过github来发布我们的文档网站。关于github上如何创建项目，如何clone到本地，这里就不详细说了。

将项目clone到本地:

```
git clone https://github.com/shelimingming/MJ_mall_doc.git
```

## 2、初始化项目

进入clone的项目中执行：

```javascript
docsify init ./docs
```

复制

![img](https://static001.geekbang.org/infoq/6b/6bfce77dbeb9a9620511e6b0b34e8b93.png)

会自动生成以下几个文件：

```javascript
index.html 入口文件
README.md 会做为主页内容渲染
.nojekyll 用于阻止 GitHub Pages 会忽略掉下划线开头的文件
```

复制

## 3、本地启动项目

```javascript
docsify serve docs
```

复制

本地访问http://localhost:3000即可看到文档：

# 四、通过github发布文档

### 1、将生成的代码提交到github中

```javascript
git add ./
git commit -m "初始化页面"
git push
```

复制

## 2、设置GitHub Pages

在Settings中的GitHub Pages中选择docs文件夹，点击保存，即可发布刚刚的文档网站。通过[https://shelimingming.github.io/MJ](https://shelimingming.github.io/MJmalldoc/)[*mall*](https://shelimingming.github.io/MJmalldoc/)[doc/](https://shelimingming.github.io/MJmalldoc/)地址即可访问！



至此，我们就零成本在公网上搭建了一个自己的文档网站了！！



# 五、docsify详细使用