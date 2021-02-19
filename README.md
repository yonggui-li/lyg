# msyql安装
https://blog.csdn.net/youarenotme/article/details/109291819
在自己的电脑上没有出现问题
---------


各位领导、专家好，我是安全实验室的李永贵，我的指导老师是张维。

今天我将从以下三个方面概述试用期的学习和工作，分别是学习内容，团队任务和未来规划。

## 一 学习内容



我的学习途径主要是公司培训、知识学习、工作任务三个方面。首先是公司培训，因为个人原因入职较晚，没赶上和大家一起系统的培训学习。只参加了一级培训并被评委优秀学员。然后是自主学习阶段，主要自学，学习渗透测试的基础知识，搭建靶场练习实操，尝试漏洞复现输出过程并分享交流，以及渗透工具的学习。最后工作也是一种学习，秉着任务驱动学习的观念，工作中查漏补缺，温故知新。

接下来按时间线简要叙述入职到现在的学习和工作内容。

9月......

10月.......

......

下面是几个月的学习输出，整理为几个大类，分别是web、主机、渗透工具、常见漏洞、docker容器，后续也会以这个框架为主干，继续丰富知识框架。

## 二 团队任务

接下来就是第二部分 团队任务。第一个独立测评任务是SMSF渗透测试。第一次渗透启发很大，同时也凸显出自己的不足。

首先概述一下SMSF项目的主要工作，分为以下五个，项目文档审计、...... 。

项目文档审计主要审计的点如下，从了解项目架构开始，到项目文档中所描述的具体实现方式，寻找不符合要求的实现或可能存在问题的点，作为后续渗透测试的侧重点。

主机渗透的主要工作是......，从中发现了漏洞和不安全实践。

很遗憾本次项目没有web端，只有一个管理页面也不归属与项目。所以有些无从下手。好在学了burp搭建隐形代理，分析几个网元之间的报文传输，也发现了一些问题，如数据传输协议内部使用http，使用工具扫描出一些问题，但是没提供给环境无法验证。

然后就是问题交流环节，......

最后输出报告。



下面来分享一个漏洞案例。

第一步信息收集：密文+密钥；如何利用，加密逻辑

学习了aes加密原理后了解到五种加密方式，但是加密的条件不止一个，需要组合不同的条件来找出加密逻辑。

获取加密逻辑后写解密函数，调试代码，只需将密文一个个输入，然后符合加密逻辑的密文就会解密输出，效率提升很多，并且成功获取密码进入sftp的主机。



写报告初稿时出现不少问题，......

通过队长耐心和我沟通交流，把一些不规范的问题去除，漏洞定级和分类，逐渐完善报告。



第一次渗透测试启发很多，不足也很多。......



第二个任务是RWCTF赛事跟踪和组织分享。

一开始完全是小白，自己也发出疑问：什么是CTF啊？

了解了CTF和题目类型后，通过Bugku靶场练习。完成一些题目，逐渐入门CTF

收获：



通过简单入门后开始赛事跟踪分析。

比赛和在线靶场又有不同，题目在docker环境下部署运行。几乎每一题的附件中都有dockerfile和docker-compose文件，学习了dockerfile制作容器镜像和docker-compose编排容器的基础语法。因为公司内网的原因，也无法ping通比赛的地址，所以没有尝试做题。

赛后进行了赛题解析并组织RWCTF分享会。

oldsystem这题让我受益匪浅。让我比较深刻的理解了反序列化漏洞的原理。和之前入门各个知识域的时候一样，我先从简单的反序列化漏洞开始，尝试在本地的两个虚拟机上复现了经典的Apache commons-collection漏洞。理解了java反序列化漏洞的核心：gadget chain和RCE是关键。gadget chain就是从反序列化实现类ObjectInputStream的readObject方法开始，执行的一系列操作的调用栈，最后执行到RCE注入的地方，即可利用漏洞。

这个题目唯一的一个实现类就执行了反序列化操作，显然可能存在反序列化漏洞。

但是题目的难点在于java版本很老，是1.4的。

已发现的gadget chain和RCE并不适用，只能自己挖掘新的利用链。

以ysoserial工具源码实现的思路作为参考，从readObject方法开始，以HashMap作为入口，到BeanComparator.compare方法，形成这样一条调用栈，从BeanComparator.compare方法到RCE也不同于已知的JNDI注入，也是需要分析一个个方法，挖掘新的调用栈，前后结合成一条完整的利用链，成功解题。

收获......



## 三 未来规划

首先是学习规划，我的宗旨是以任务驱动学习，学以致用：以工作任务驱动学习，不断扩大知识面，不断提高理解的深度；并且学到的知识能加以利用，更加巩固自身的能力。

我的学习规划主要分为这四个方面，渗透技能、代码审计、编程和知识拓展。其中渗透技能以web为主，着重发展；之后我们团队也会做白盒的工作，所以代码审计的能力也需要提升；另外的编程能力则是为了辅助黑白盒测试，比如我们现在渗透的二阶段，目标是深入项目业务挖掘src漏洞，以及之后白盒的代码审计，都必不可免地与代码打交道，学习编程语言会帮助我快速了解项目架构，也能更容易读懂关键函数和方法等；知识拓展主要......

最后是2021年的规划，左边是工作上的任务，包括已完成的、正在进行的和还在准备中的。......

右边是年初到现在已开始的学习和工作，......

最后我的寄语是......









