# 计算机网络笔记 Part2 物理层（Physical Layer）_INlinKC 的博客 - CSDN 博客

Created: February 24, 2022 1:13 PM
Tags: 学习, 摘录, 计算机网络
URL: https://blog.csdn.net/weixin_45067603/article/details/106974965

> 物理层1.基本概念2.数据通信基本知识一个数据通信例子相关术语三种通讯方式名称英文定义需要信道条数单工通信Simplex只能一个发一个收一条半双工通信half-duplex都可以发或者收，但是同一时间只能进行一个两条全双工通信duplex都可以同时收发数据两条两种数据传输方式传输方式特点串行传输速度慢，省钱，适合远距离并行传输速度快，耗钱，适合近距离码元（Symbol）定义：码元是指用一个
>
- # 本人计算机网络笔记总目录
  
  [计算机网络笔记 Part1 概述](https://blog.csdn.net/weixin_45067603/article/details/106974036)
  [[计算机网络笔记 Part1 概述_INlinKC 的博客 - CSDN 博客]]
  
  [计算机网络笔记 Part2 物理层（Physical Layer）](https://blog.csdn.net/weixin_45067603/article/details/106974965) 
   [[计算机网络笔记 Part2 物理层（Physical Layer）_INlinKC 的博客 - CSDN 博客]]
  
  [计算机网络笔记 Part3 数据链路层（Data Link Layer）](https://blog.csdn.net/weixin_45067603/article/details/106980441)
  [[计算机网络笔记 Part3 数据链路层（Data Link Layer）_INlinKC 的博客 - CSDN 博客]]
  
  [计算机网络笔记 Part4 网络层（Network Layer）](https://blog.csdn.net/weixin_45067603/article/details/106993253)
  [[计算机网络笔记 Part4 网络层（Network Layer）_INlinKC 的博客 - CSDN 博客]]
  
  [计算机网络笔记 Part5 传输层（Transport Layer）](https://blog.csdn.net/weixin_45067603/article/details/107034202)
  [[计算机网络笔记 Part5 传输层（Transport Layer）_INlinKC 的博客 - CSDN 博客]]
  
  [计算机网络笔记 Part6 应用层（Application Layer）](https://blog.csdn.net/weixin_45067603/article/details/107053479)
  [[计算机网络笔记 Part6 应用层（Application Layer）_INlinKC 的博客 - CSDN 博客]]
# 1. 基本概念

电脑要组网，第一件事要干什么？当然是先把电脑连起来，可以用光缆、电缆、双绞线、无线电波等方式。

这就叫做” 实体层”，逼格高一点的叫法就是物理层。它就是把电脑连接起来的物理手段。它主要规定了网络的一些电气特性，作用是负责传送 0 和 1 的电信号。

至于 0 和 1 的信号是什么，还轮不到物理层还决定。

![https://img-blog.csdnimg.cn/20200626212252286.png?shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTA2NzYwMw==,size_16,color_FFFFFF,t_70](https://img-blog.csdnimg.cn/20200626212252286.png?shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTA2NzYwMw==,size_16,color_FFFFFF,t_70)
# 2. [数据通信](https://so.csdn.net/so/search?q=%E6%95%B0%E6%8D%AE%E9%80%9A%E4%BF%A1&spm=1001.2101.3001.7020)基本知识
## 2.1 一个数据通信例子

![https://img-blog.csdnimg.cn/20200626212614182.png?shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTA2NzYwMw==,size_16,color_FFFFFF,t_70](https://img-blog.csdnimg.cn/20200626212614182.png?shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTA2NzYwMw==,size_16,color_FFFFFF,t_70)
## 2.2 相关术语

![https://img-blog.csdnimg.cn/20200626212816152.png?shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTA2NzYwMw==,size_16,color_FFFFFF,t_70](https://img-blog.csdnimg.cn/20200626212816152.png?shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTA2NzYwMw==,size_16,color_FFFFFF,t_70)
## 2.3 三种通讯方式

[Untitled](https://www.notion.so/0f9c2d50793a41289a314c2c64e0085d)
## 2.4 两种数据传输方式

[Untitled](https://www.notion.so/a2567ffa6f9b45c5bdac21ace74ebc76)

![https://img-blog.csdnimg.cn/20200626213810764.png?shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTA2NzYwMw==,size_16,color_FFFFFF,t_70](https://img-blog.csdnimg.cn/20200626213810764.png?shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTA2NzYwMw==,size_16,color_FFFFFF,t_70)
## 2.5 码元（[Symbol](https://so.csdn.net/so/search?q=Symbol&spm=1001.2101.3001.7020)）

定义：码元是指用一个固定时长的信号波形（数字脉冲），代表离散数值的基本波形。当有多个离散状态时，成为 M 进制码元
一个码元可以携带多个比特的信息
个人理解：码元就是在网线上传输的一个个信号段。码元的不同进制就是用来表示不同的数值的
## 2.6 波特（Baud）

用来指一秒可以传输多少个码元
## 2.7 速率

分为**码元传输速率**和**信息传输速率**
信息传输速率就是 b/s，就是我们平常说的**网速**
码元可以理解为几个比特的**集合**，所以信息传输速率（网速）= 码元传输速率 x 码元所带信息量（多少比特）
码元所带信息量（比特数）=log2（码元进制数）
## 2.8 带宽（Band Width）

用来表示最高数据速率
## 2.9 奈式准则（Nyquist）

是在

**理想状态下**

得出的结论

![https://img-blog.csdnimg.cn/20200626222053679.png?shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTA2NzYwMw==,size_16,color_FFFFFF,t_70](https://img-blog.csdnimg.cn/20200626222053679.png?shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTA2NzYwMw==,size_16,color_FFFFFF,t_70)
## 2.10 香农公式（Shannon）

是在

**有噪声的信道中**

得出的结论

![https://img-blog.csdnimg.cn/20200626225409541.png?shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTA2NzYwMw==,size_16,color_FFFFFF,t_70](https://img-blog.csdnimg.cn/20200626225409541.png?shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTA2NzYwMw==,size_16,color_FFFFFF,t_70)

![https://img-blog.csdnimg.cn/20200626225547833.png?shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTA2NzYwMw==,size_16,color_FFFFFF,t_70](https://img-blog.csdnimg.cn/20200626225547833.png?shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTA2NzYwMw==,size_16,color_FFFFFF,t_70)
## 2.11 基带信号和宽带 / 带通信号（Base band，pass band）

计算机网络中用的基带信号是

**数字信号**

![https://img-blog.csdnimg.cn/20200626225921565.png?shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTA2NzYwMw==,size_16,color_FFFFFF,t_70](https://img-blog.csdnimg.cn/20200626225921565.png?shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTA2NzYwMw==,size_16,color_FFFFFF,t_70)
## 2.12 编码

将数据转化为

**数字信号**

数字数据 (digtal data) 通过 数字发送器(digit emitter) 转化为 数字信号(digtal signal)

![https://img-blog.csdnimg.cn/20200626154459852.png](https://img-blog.csdnimg.cn/20200626154459852.png)

模拟数据 (analog data) 通过 PCM 编码器(PCM coder) 转化为 数字信号 (digtal signal)

![https://img-blog.csdnimg.cn/20200626154431937.png](https://img-blog.csdnimg.cn/20200626154431937.png)

> 单极性不归零编码：只使用一个电压值，高电平表示 1，低电平表示 0.
> 

> 双极性不归零编码：用幅值相等的正负电平表示二进制数 1 和 0.
> 

> 单极性归零编码：发送码 1 时高电平在整个码元期间只持续一段时间，其余时间返回零电平。
> 

> 双极性归零编码：正负零三个电平，信号本身携带同步信息。
> 

![https://img-blog.csdnimg.cn/20200626163610563.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTA2NzYwMw==,size_16,color_FFFFFF,t_70](https://img-blog.csdnimg.cn/20200626163610563.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTA2NzYwMw==,size_16,color_FFFFFF,t_70)

> 曼彻斯特编码：单极性编码的缺点是没有办法区分此时是没有信号，还是有信号，但是信号是 0.
这种编码方式是 bit 中间有信号，低 - 高跳转表示 0，高 - 低跳转表示 1，一个时钟周期只可以表示一个 bit，并且必须通过两次采样才能得到一个 bit。它能携带时钟信号，而且能区分此时是没有信号还是信号为 0.
> 

> 差分曼彻斯特编码：抗干扰能力比曼彻斯特编码更强。bit 与 bit 之间有信号跳变，表示下一个 bit 为 0，bit 与 bit 之间没有信号跳变，表示下一个 bit 为 1。
> 

![https://img-blog.csdnimg.cn/20200626165018277.png?shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTA2NzYwMw==,size_16,color_FFFFFF,t_70](https://img-blog.csdnimg.cn/20200626165018277.png?shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTA2NzYwMw==,size_16,color_FFFFFF,t_70)
## 2.13 调制：数据转化为模拟信号（了解）

常用的调制方法：调频 (AM)，调频 (FM)，调相 (PM)

![https://img-blog.csdnimg.cn/20200626165059865.png?shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTA2NzYwMw==,size_16,color_FFFFFF,t_70](https://img-blog.csdnimg.cn/20200626165059865.png?shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTA2NzYwMw==,size_16,color_FFFFFF,t_70)

模拟数据 (analog data) 通过 调制器(modulaotr) 转化为 模拟信号 (analog signal)

![https://img-blog.csdnimg.cn/20200626154409879.png](https://img-blog.csdnimg.cn/20200626154409879.png)

数字数据 (digtal data) 通过 调制器(modulaotr) 转化为 模拟信号 (analog signal)

![https://img-blog.csdnimg.cn/20200626154455793.png](https://img-blog.csdnimg.cn/20200626154455793.png)
# 3. 物理层传输介质

传输介质分为**导向性**传输介质和**非导向性**传输介质

[Untitled](https://www.notion.so/f724267296df4528a6d3c971f3da7236)
## 3.1 常见的导向性传输介质
### 3.1.1 双绞线

根据有无屏蔽层分为

**屏蔽双绞线（STP）**

和

**无屏蔽双绞线（UTP）**

![https://img-blog.csdnimg.cn/20200627110148375.png?shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTA2NzYwMw==,size_16,color_FFFFFF,t_70](https://img-blog.csdnimg.cn/20200627110148375.png?shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTA2NzYwMw==,size_16,color_FFFFFF,t_70)
### 3.1.2 同轴电缆（Coaxial Cable）

![https://img-blog.csdnimg.cn/20200627110353962.png?shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTA2NzYwMw==,size_16,color_FFFFFF,t_70](https://img-blog.csdnimg.cn/20200627110353962.png?shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTA2NzYwMw==,size_16,color_FFFFFF,t_70)
### 3.1.3 光纤（Optical fiber）

![https://img-blog.csdnimg.cn/20200627110509407.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTA2NzYwMw==,size_16,color_FFFFFF,t_70](https://img-blog.csdnimg.cn/20200627110509407.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTA2NzYwMw==,size_16,color_FFFFFF,t_70)

根据

**入射角**

不同，又分为单模光纤和多模光纤

![https://img-blog.csdnimg.cn/20200627110700437.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTA2NzYwMw==,size_16,color_FFFFFF,t_70](https://img-blog.csdnimg.cn/20200627110700437.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTA2NzYwMw==,size_16,color_FFFFFF,t_70)
## 3.2 常见的非导向性传输介质

包括

**无线电波**

，

**微波**

，

**红外线**

和

**激光**

等

![https://img-blog.csdnimg.cn/20200627110843264.png?shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTA2NzYwMw==,size_16,color_FFFFFF,t_70](https://img-blog.csdnimg.cn/20200627110843264.png?shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTA2NzYwMw==,size_16,color_FFFFFF,t_70)
# 4. 物理层设备
## 4.1 中继器（RP repeater）

注释：5-4-3 规则是为了限制中继器使用次数的，理由可见图

5 是指不能超过 5 个网段

4 是指在这些网段中的物理层网络设备（中继器，集线器）最多不超过 4 个

3 是指这些网段中最多只有三个网段挂有计算机

![https://img-blog.csdnimg.cn/20200627111139163.png?shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTA2NzYwMw==,size_16,color_FFFFFF,t_70](https://img-blog.csdnimg.cn/20200627111139163.png?shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTA2NzYwMw==,size_16,color_FFFFFF,t_70)
## 4.2 集线器（Hub）

集线器是个大的冲突域，同时

**只能有两个设备进行通讯**

，只会传输信号，没有智能。

![https://img-blog.csdnimg.cn/20200627111545392.png?shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTA2NzYwMw==,size_16,color_FFFFFF,t_70](https://img-blog.csdnimg.cn/20200627111545392.png?shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTA2NzYwMw==,size_16,color_FFFFFF,t_70)
# 5. 本章思维导图

![https://img-blog.csdnimg.cn/20200627112018411.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTA2NzYwMw==,size_16,color_FFFFFF,t_70](https://img-blog.csdnimg.cn/20200627112018411.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTA2NzYwMw==,size_16,color_FFFFFF,t_70)

参考资料

[2019 王道考研 计算机网络](https://www.bilibili.com/video/BV19E411D78Q?p=1)

[互联网 5 层模型入门–通俗易懂](https://blog.csdn.net/qq_20363225/article/details/79698084?)

> 本文由简悦 SimpRead 转码