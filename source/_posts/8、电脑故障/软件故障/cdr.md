title: cdr提示盗版解决方案
tags:
  - cdr
categories:
  - 8、电脑故障
  - 软件故障
date: 2019-10-11 11:48:00
---

---
>很多网友在使用 CorelDRAW 的时候，会弹出一个提示框，像下图这样(或者表现为卡在启动画面，无法进入软件主界面)，这可能是软件联网检测到了你是盗版用户，不给启动。今天教大家如何解决这个问题。

![](http://www.carrotchou.blog/wp-content/uploads/2019/05/72d3f-005zv1pegy1g1bu1dct0bj308f0egjrg.jpg)

# 解决方法

**第一步**，删除 `C:\\Users\\用户名\\AppData\\Roaming\\Corel` 文件夹里的所有内容，注意这个 AppData 文件夹是隐藏的，需要[显示隐藏文件夹](https://jingyan.baidu.com/article/da1091fbc6c7d2027849d628.html)，才能看到。本地判断是否是盗版的数据就保存在这个文件夹里，这个文件夹下的文件是 CorelDRAW 的缓存文件，删除了没有影响，下次打开 CorelDRAW 又会自动生成。

**第二步**，把 CorelDRAW 主程序添加到[防火墙出站规则](http://www.carrotchou.blog/176.html)里，屏蔽软件联网即可。
