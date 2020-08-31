title: npm_apm_pip工具修改国内源.md
tags:
  - npm
  - apm
  - pip
categories:
  - 5、编程相关
  - 编程技巧
date: 2020-08-31 14:26:00
---
大家都用过npm、apm、pip之类的包下载安装工具，但是受限于默认源国内访问过慢的问题导致使用体验极差，这里总结了各个工具修改源为国内源的方法，详细参见下方：
# npm篇
NPM是随同NodeJS一起安装的包管理工具，能解决NodeJS代码部署上的很多问题，常见的使用场景有以下几种：
*   允许用户从NPM服务器下载别人编写的第三方包到本地使用。
*   允许用户从NPM服务器下载并安装别人编写的命令行程序到本地使用。
*   允许用户将自己编写的包或命令行程序上传到NPM服务器供别人使用。
## npm修改国内源
永久修改，参见下代码：
```
npm config set registry https://registry.npm.taobao.org
```
查看下是否修改成功：
```
npm config get registry
```
临时修改
```
npm --registry https://registry.npm.taobao.org install express
```
## npm国内源清单
淘宝npm镜像
*   搜索地址：http://npm.taobao.org/
registry地址：http://registry.npm.taobao.org/
cnpmjs镜像
*   搜索地址：http://cnpmjs.org/
*   registry地址：http://r.cnpmjs.org/

# pip篇
pip 是 Python 包管理工具，该工具提供了对Python 包的查找、下载、安装、卸载的功能。
## pip修改国内源
永久修改参见下代码：
```
pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple
```
临时修改：
```
pip install scrapy -i https://pypi.tuna.tsinghua.edu.cn/simple
```
## pip国内源清单
*   阿里云 http://mirrors.aliyun.com/pypi/simple/
*   中国科技大学 https://pypi.mirrors.ustc.edu.cn/simple/
*   豆瓣(douban) http://pypi.douban.com/simple/
*   清华大学 https://pypi.tuna.tsinghua.edu.cn/simple/
*   中国科学技术大学 http://pypi.mirrors.ustc.edu.cn/simple/

# apm篇
Atom的插件更新功能由apm提供。apm内部封装了一个npm。
## apm修改国内源
永久修改：
```
apm config set registry http://registry.npm.taobao.org
```
## apm国内源清单
淘宝npm镜像
*   搜索地址：http://npm.taobao.org/
registry地址：http://registry.npm.taobao.org/
cnpmjs镜像
*   搜索地址：http://cnpmjs.org/
*   registry地址：http://r.cnpmjs.org/
---
