title: 解决chrome开发者模式弹窗
tags:
  - chrom
  - 开发者
categories:
  - 8、电脑故障
  - 软件故障
date: 2019-10-09 13:26:00
---
# 前言


作为一个前端程序员，难免会有一些专属自己的小扩展，没必要每一个都发到Chrome应用商店去，虽然可以勾选“开发者模式”来运行本地插件，但是每次启动都会有一个烦人的 **“请停用以开发者模式运行的扩展程序”** 提示，这个提示有多烦人，接触过的人都知道，启动的时候它不立即提示，等过了几秒钟等你打开某个网页开始执行某些操作时它突然弹出来干扰你的操作，真是苦不堪言！所以总想着如何把它给去掉。
作为一个前端程序员，难免会有一些专属自己的小扩展，没必要每一个都发到Chrome应用商店去，虽然可以勾选开发者模式来运行本地插件，但是每次启动都会有一个烦人的请停用以开发者模式运行的扩展程序提示，这个提示有多烦人，接触过的人都知道，启动的时候它不立即提示，等过了几秒钟等你打开某个网页开始执行某些操作时它突然弹出来干扰你的操作，真是苦不堪言！所以总想着如何把它给去掉。

![aW518xH258](http://image.haoji.me/201803/20180312_142912_913_8332.png)

# 解决方法

网上搜索了一圈，发现主要有3种方法——组策略法，运行批处理法，直接改dll文件法。第一种组策略的据说很早就失效了，我亲测了一下确实没用。另外一个批处理的方法据说也生效了，而且批处理权限太大没敢尝试运行，直接试了第三种方法，一次性成功！下面记录一下解决过程（ps原文说的不是特别清楚，有些误导人的地方，我这里全部重新截图描述一遍）


## 2.1. 修改dll文件法
---

打开Chrome安装目录，找到`chrome.dll`文件，用[x64dbg](http://www.jb51.net/softs/467705.html)打开，

![W521xH347](http://res.haoji.me/blog/images/transparent.gif)

双击`x96dbg.exe`，然后选择`x64dbg`（如果打不开，换`x32dbg`打开）：

![W594xH330](http://res.haoji.me/blog/images/transparent.gif)

然后连续多次点击`运行到用户代码`按钮，直至窗口标题处的模块变成`chrome.dll`：

![W771xH532](http://res.haoji.me/blog/images/transparent.gif)

然后在主面板右键依次选择`搜索` -> `当前模块` -> `字符串`：

![W580xH327](http://res.haoji.me/blog/images/transparent.gif)

然后会打开一个搜索界面，等待进度条加载完毕，搜索`ExtensionDeveloperModeWarning`：

![W645xH508](http://res.haoji.me/blog/images/transparent.gif)

会搜到2条结果，双击第一个，跳转到反汇编界面，往上翻一点，找到`cmp eax,2`（也有可能是`cmp eax,3`）：

![W786xH379](http://res.haoji.me/blog/images/transparent.gif)

双击打开编辑页面，修改成`cmp eax,9`，然后点击确定，注意只需要点击一次确定即可，点击确定后它还是会继续弹出其它行的编辑界面，此时直接关闭对话框即可。：

![W648xH166](http://res.haoji.me/blog/images/transparent.gif)

修改完之后`Ctrl+P`导出修改过的dll文件（点击修补文件按钮就是导出dll文件）：

![W529xH496](http://res.haoji.me/blog/images/transparent.gif)

你可以把dll文件导出到其它某个位置，然后把原始chrome.dll文件备份，再把这个修改过的替换，然后重启Chrome，可以发现该死的提示已经没有了。

以上步骤测试于`chrome@64.0.3282.140`。

## 2.2. 组策略法
---

经测试已失效：

https://jingyan.baidu.com/article/ce09321b7d581e2bff858f23.html

## 2.3. 批处理法
---

以下方法未亲测，但据说已失效：

http://blog.csdn.net/a493113713/article/details/54917592

# 参考


>本文引用[小茗同学](https://haoji.me/) 的文章，并做了一定缩减；

https://stackoverflow.com/questions/30287907/how-to-get-rid-of-disable-developer-mode-extensions-pop-up/30361260#30361260

https://www.52pojie.cn/forum.php?mod=viewthread&tid=695123&page=1&authorid=533705

个人网站： [https://haoji.me](https://haoji.me/)  
github： [https://github.com/sxei](https://github.com/sxei)  
博客园： [http://www.cnblogs.com/liuxianan](http://www.cnblogs.com/liuxianan)
