---
title: Grunt 学习笔记
category: 工具
tag: Grunt
---

## 前端集成解决方案

解决前端工程的根本问题。一套包含框架和工具，便于开发者快速构建美丽实用的web应用程序的工作流，同时这套工作流必须是文件强壮的。

## 解决的前端问题

- 开发团队代码风格不统一，如何强制开发规范；
- 前期开发的组件库如何维护和使用；
- 如何模块化前端项目；
- 服务器部署前必须的压缩，检查流程如何简化，流程如何完善；

## 常见的前端集成解决方案

Yeoman --> Bower --> Grunt/Gulp 

mac平台: CodeKit

百度: FIS

腾讯Alloyteam: Spirit

## Build tool(编译一个程序的新版本时所使用的编译工具)

- ant(java)
- Yeoman、Grunt、Buildy(node.js)
- jasy(Python)
- Gmake(Ruby)
- Rake(Ruby,类Gmake)
- Sprockets(Rack)

## 学习基础

- html 
- css
- JavaScript基础知识
- 了解node.js

## 了解node.js

### 1. node环境安装

node.js官网： http://nodejs.org/

*安装node程序包时路径不要有空格*

### 2. npm(Node Package Manager)nodea包管理和分发工具

类似：
gem(ruby)

pypi / setuptools(python)

pear(php)

### 3. 命令行工具：

windows：cmd窗口不支持bash脚本，可安装Git，Git提供了git bash shell

mac: iTerm可替代原生的控制台

### 4. node项目的基本结构

~~~
~~~

## 安装Grunt

官网：`http://gruntjs.com/`

安装指令：`npm install -g grunt-cli`

验证方法：`grunt`

grunt：自动化，减少压缩、编译、单元测试，代码校验这种重复且无业务关联的工作。

## 安装Yeoman

官网：`http://yeoman.io/`

安装指令：`npm install -g yo`

验证方法：`yo -v`

Yeoman：现代web App的`脚手架`工具。 在web项目的立项阶段，使用Yeoman来生成项目的文件，代码结构。Yeoman自动将最佳实践和工具整合进来，大大加速和方便我们后续的开发。保留了代码校验、测试、压缩等基本工作流程。

安装好Yeoman还需要安装自己所需的Generator(生成器)

## 安装Bower

官网：`http://bower.io/`
安装指令： `npm install -g bower`
验证方法： `bower -v`

Bower： web的包管理器。
