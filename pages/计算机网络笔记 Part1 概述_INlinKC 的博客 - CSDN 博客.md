# 计算机网络笔记 Part1 概述_INlinKC 的博客 - CSDN 博客

Created: February 24, 2022 9:51 AM
Tags: 学习, 摘录, 计算机网络
URL: https://blog.csdn.net/weixin_45067603/article/details/106974036

> 概述1.速率相关性能指标速率定义：连接在计算机网络上的主机在数字信道上传送数据位数的速率单位:b/s,Kb/s,Mb/s,Tb/s，如果用字节表示，则是B/s,KB/s,MB/s,TB/s1Byte=8Bit带宽在计算机网络中，指的是网络设备所支持的最高速度，单位同速率，是理想条件下最高速率吞吐量指的是单位时间内通过某个网络的数据总量个人理解速率就是实际网速，带宽是理论网速（长城宽带警告），吞吐量是一个或多个设备的综合速率，比如说1000m宽带的路由器连着三部手机，每部手机都是10m
> 

# 本人计算机网络笔记总目录

[计算机网络笔记 Part1 概述](https://blog.csdn.net/weixin_45067603/article/details/106974036)

[计算机网络笔记 Part1 概述_INlinKC 的博客 - CSDN 博客](https://www.notion.so/Part1-_INlinKC-CSDN-e38bbbce3c29487f891d32fb0cfaab3e) 

[计算机网络笔记 Part2 物理层（Physical Layer）](https://blog.csdn.net/weixin_45067603/article/details/106974965) 

 [计算机网络笔记 Part2 物理层（Physical Layer）_INlinKC 的博客 - CSDN 博客](https://www.notion.so/Part2-Physical-Layer-_INlinKC-CSDN-f1e73c7085714a2ab74f8e4c27cd6196) 

[计算机网络笔记 Part3 数据链路层（Data Link Layer）](https://blog.csdn.net/weixin_45067603/article/details/106980441)

[计算机网络笔记 Part3 数据链路层（Data Link Layer）_INlinKC 的博客 - CSDN 博客](https://www.notion.so/Part3-Data-Link-Layer-_INlinKC-CSDN-b89fbe3ab8ed4f5b9ed0609fe5ceed30) 

[计算机网络笔记 Part4 网络层（Network Layer）](https://blog.csdn.net/weixin_45067603/article/details/106993253)

[计算机网络笔记 Part4 网络层（Network Layer）_INlinKC 的博客 - CSDN 博客](https://www.notion.so/Part4-Network-Layer-_INlinKC-CSDN-97190bf540fd4c1aa9640e38bdbd83fd) 

[计算机网络笔记 Part5 传输层（Transport Layer）](https://blog.csdn.net/weixin_45067603/article/details/107034202)

[计算机网络笔记 Part5 传输层（Transport Layer）_INlinKC 的博客 - CSDN 博客](https://www.notion.so/Part5-Transport-Layer-_INlinKC-CSDN-37254078573d43b5a37f3f8a7a602bca) 

[计算机网络笔记 Part6 应用层（Application Layer）](https://blog.csdn.net/weixin_45067603/article/details/107053479)

[计算机网络笔记 Part6 应用层（Application Layer）_INlinKC 的博客 - CSDN 博客](https://www.notion.so/Part6-Application-Layer-_INlinKC-CSDN-48a4cdae08db445da8d9db9d916bd5c0) 

# 1. 速率相关性能指标

## 1.1 速率

定义：连接在计算机网络上的主机在数字信道上传送数据位数的速率
单位: b/s,Kb/s,Mb/s,Tb/s，
如果用字节表示，则是 B/s,KB/s,MB/s,TB/s
1Byte=8Bit

## 1.2 带宽

在计算机网络中，指的是网络设备所支持的最高速度，单位同速率，是**理想条件下最高速率**

## 1.3 [吞吐量](https://so.csdn.net/so/search?q=%E5%90%9E%E5%90%90%E9%87%8F&spm=1001.2101.3001.7020)

指的是单位时间内通过某个网络的数据**总**量

## 个人理解

速率就是实际网速，带宽是理论网速（长城宽带警告），吞吐量是一个或多个设备的综合速率，比如说 1000m 宽带的路由器连着三部手机，每部手机都是 10mb/s 看片，那么速率就是 10mb/s，带宽是宽带的 1000m，路由器吞吐量是 30mb/s，即三者之和

# 2. 时延相关指标

## 2.1 时延

时延包括四大类

[Untitled](https://www.notion.so/3e3df284c0604843a6c4b2157c4bf93f)

使用高速链路 (提高网速)，只能减小发送时延，无法减少其他三个时延

## 2.2 时延带宽积

公式：时延带宽积 = 传播时延 x 带宽
意思是链路上有多少比特的数据

## 2.3 往返时延 RTT

发送端发送数据开始，到发送端收到来自接收端的确认（接收端收到数据后便立即发送确认），总共经历的时延
RTT= **传播时延** x2 + 处理时间 (有时可能直接忽略)

## 2.4 利用率

### 2.4.1 信道利用率

信道利用率 = 有数据通过**时间** / 有 + 无数据通过**时间**

### 2.4.2 网络利用率

网络利用率 = 所有信道利用率加权求平均值

### 2.4.3 时延和利用率的关系图

利用率越高，延迟越大

![https://img-blog.csdnimg.cn/20200626203643244.png](https://img-blog.csdnimg.cn/20200626203643244.png)

# 3. 分层结构

## 3.1 为什么要分层，分层要做什么

（1）发起通信的计算机必须将数据通信的通路进行激活。
（2）要告诉网络如何识别目的主机。
（3）发起通信的计算机要查明目的主机是否开机，并且与网络连接正常。
（4）发起通信的计算机要弄清楚，对方计算机中文件管理程序是否已经做好准备工作。
（5）确保差错和意外可以解决。

## 3.2 正式认识分层结构

![https://img-blog.csdnimg.cn/20200626204724293.png?shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTA2NzYwMw==,size_16,color_FFFFFF,t_70](https://img-blog.csdnimg.cn/20200626204724293.png?shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTA2NzYwMw==,size_16,color_FFFFFF,t_70)

# 4. 参考模型

[Untitled](https://www.notion.so/b34a886045fa4c3fb232a411ebfb0960)

## 4.1 OSI 流程简介

网络层及以上，每一层都要对上一层发送的数据进行处理（加个头部）

数据链路层不仅需要加头部，还需要加尾部

物理层什么都不加，只管发送数据（比特流）

![https://img-blog.csdnimg.cn/20200626205152756.png?xshadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTA2NzYwMw==,size_16,color_FFFFFF,t_70](https://img-blog.csdnimg.cn/20200626205152756.png?xshadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTA2NzYwMw==,size_16,color_FFFFFF,t_70)

## 4.2 TCP/IP 参考模型

![https://img-blog.csdnimg.cn/20200626205911885.png?shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTA2NzYwMw==,size_16,color_FFFFFF,t_70](https://img-blog.csdnimg.cn/20200626205911885.png?shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTA2NzYwMw==,size_16,color_FFFFFF,t_70)

## 4.3 五层参考模型及其传输过程简介

![https://img-blog.csdnimg.cn/20200626210125977.png?shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTA2NzYwMw==,size_16,color_FFFFFF,t_70](https://img-blog.csdnimg.cn/20200626210125977.png?shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTA2NzYwMw==,size_16,color_FFFFFF,t_70)

![https://img-blog.csdnimg.cn/20200626210211625.png?shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTA2NzYwMw==,size_16,color_FFFFFF,t_70](https://img-blog.csdnimg.cn/20200626210211625.png?shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTA2NzYwMw==,size_16,color_FFFFFF,t_70)

参考资料

[2019 王道考研 计算机网络](https://www.bilibili.com/video/BV19E411D78Q?p=1)

> 本文由简悦 SimpRead 转码