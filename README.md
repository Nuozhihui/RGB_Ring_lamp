#  RGB_语音小灯_RGB
 RGB_语音小灯_RGB

 

**程序整理后开源！！可以去我的Github上看看！！点个关注再去（圈粉）🦢**

**如果你有啥问题可以通过两个途径联系到我们**

**QQ交流群:864884014**

**个人博客:https://hinuohui.com/**

Github仓库:

#  版本

V0.9文档编写

# 简介

RGB灯环，使用WS2812B和ESP-C3模组和VC-02语音模组

# 项目



## 效果

TODO

![120ce0d4fe4276ce431a684934416ba.jpg](//image.lceda.cn/pullimage/2gIZetLrnOf59CterIL1sPwCwcmBwBWrc5JRIAZd.jpeg)

![image-20230112224404407](https://image.lceda.cn/pullimage/0TE7KIe4LvQbc3wffCwkdFF5BLSxN3qhqDAdr4RN.jpeg)



<video src="https://oshwhub.com/attachments/2023/1/IfDyWO7dAQnEC5UFrooVmcl3fQot67o3DkIi3188.mp4"></video>

基础介绍

## 环境

-  TODO

## 实现功能

1.RGB照明效果

2.远程手机控制

3.语音唤醒

4.时钟模式

5.等....

## 模式

TODO

#  项目目录

- [x] 硬件 
- [ ] 固件
- [ ] 软件
- [x] 工具

# VC-02使用

VC系列模组Windows平台串口驱动下载：[ 链接](https://docs.ai-thinker.com/_media/tools/serial_driver_windos.7z)

VC系列模组开发指导手册下载：[点我下载](https://docs.ai-thinker.com/_media/vc-0102_manual.zip)

VC系列模组出厂指令列表：[中文](https://docs.ai-thinker.com/_media/出厂指令列表及功能.pdf) [EN](https://docs.ai-thinker.com/_media/vc_factorycommandtable.pdf)

## VC-02应用开发

安信可语音开放平台使用教程：[【离线语音专题②】安信可语音开放平台的使用——VC系列SDK的获取](https://blog.csdn.net/Boantong_/article/details/124689101)

VC系列开发环境搭建教程：[【离线语音专题③】安信可VC系列离线语音SDK开发环境搭建——基于Linux系统](https://blog.csdn.net/Boantong_/article/details/123889070?spm=1001.2014.3001.5501)

VC控制LED灯：[【离线语音专题④】安信可VC离线语音开发板二次开发语音控制LED灯](https://aithinker.blog.csdn.net/article/details/124098329)

# 安信可语音开放平台使用

安信可语音开放平台：

[http://voice.ai-thinker.com/#](http://voice.ai-thinker.com/#)

**一、RGB品类产品生成**

在【灯具】品类选择【RGB灯】，【选择场景】里选择纯离线方案，【选择模组】可以根据自己实际的硬件选择，我这里选择VC-02。【填写产品信息】中的产品名称按需填写，语言选择中文即可。下拉到最底部，点击【保存】。

![动图](https://pic4.zhimg.com/v2-9f6dcac618443b74045a30efb93e187f_b.webp)



**1.产品功能定义**

在语音SDK选项中，前端信号处理、Pin脚配置保持默认

![img](https://pic2.zhimg.com/80/v2-cd2ef50ffd7a334340ab4212498a5059_720w.webp)

**2.定义控制LED的唤醒词及回复语**

![img](https://pic1.zhimg.com/80/v2-29bb9f9aa3b26544419186033351dbc0_720w.webp)

**3.定义命令词及回复语**

在基础信息中

- 行为：即action，用于代码内部识别，必填
- 命令词：即语音命令词，需要给模组写入的指令，多个命令用 “ | ”隔开，必填
- 回复语：即命令词对应的回复语，多个回复语用 “ | ”隔开，`必填`

![img](https://pic2.zhimg.com/80/v2-9889a42eb46b1b215e25dec505cfc365_720w.webp)

**4. 添加控制**

在控制详情中添加命令词对应做的控制：

![img](https://pic3.zhimg.com/80/v2-98916759217964257602ea9add2131f6_720w.webp)

在开发板中，默认引出了三个LED灯，对应的GPIO分别是：

![img](https://pic3.zhimg.com/80/v2-bfb5373553baf706caa64c26f6384742_720w.webp)

可以添加唤醒状态灯，例如：蓝色灯为唤醒状态灯、暖光灯为被命令词控制灯。

![img](https://pic2.zhimg.com/80/v2-b85797b29a3a637e54b13aa1170aef91_720w.webp)

**5.完整的制作过程(包含SDK生成)**

[https://aithinker.blog.csdn.net/article/details/124098329](https://link.zhihu.com/?target=https%3A//aithinker.blog.csdn.net/article/details/124098329)

或点击阅读原文查看

**二、SDK下载和固件下载**

![img](https://pic2.zhimg.com/80/v2-dfb89e202a85db04b0f231a74769183d_720w.webp)

**SDK的生成需要时间，不用着急。**

如果不需要再外加功能，可以直接选择固件下载，可生成和定制功能一致的固件，之后烧录即可。
如需外加别的功能，比如退出唤醒关闭蓝色灯。就下载SDK，修改源码实现功能。

**1.固件下载**

固件下载是通过远程服务器编译当前SDK后生成的固件，一般有四个固件，它们分别是：

- uni_app_debug.bin： 调试版固件，有调试信息输出，需要用专门的调试器进行烧录
- uni_app_debug_update.bin： 调试版的串口升级固件，可以使用UART进行烧录
- uni_app_release.bin： 正式版固件，需要用专门的调试器进行烧录
- uni_app_release_update.bin：正式版的串口升级固件，可以使用UART进行烧录

![img](https://pic4.zhimg.com/80/v2-31c4e65304d573943124865f39885c63_720w.webp)

**2.SDK下载**

SDK下载的文件是压缩格式，推荐使用Linux系统进行解压，解压指令：

```text
tar -xzvf uni_hb_m_solution-xxxxx-xxxxxxxx.tar.gz
```

![img](https://pic1.zhimg.com/80/v2-173266fa49c08679587dbc15f6590680_720w.webp)

