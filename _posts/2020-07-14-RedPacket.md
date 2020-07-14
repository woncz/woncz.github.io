---
layout:     post
title:      "Red Packet Algorithm"
subtitle:   "algos"
date:       2020-07-14
author:     "Woncz"
header-img: "img/post-bg-redpacket.jpg"
catalog: true
tags:
  - ALGOS
---

#### 微信红包

微信红包，依托其强大的社交基因，短时间内占据个人支付的广阔市场，撕开支付宝苦心经营多年的领地，本文试图从技术的角度剖析随机红包算法的实现方案


#### 约束条件

- 全局约束: 每个人的红包金额取值范围[1, 20000]， 单位分，发红包时，需要对红包金额、红包个数校验，不满足约束则创建红包失败（生成失败或者无法提交）

- 红包约束: 针对具体单个红包，当前用户的红包金额取值，收到双重约束：全局约束，红包整体金额；当前用户的红包最小值为：当前剩余红包金额 - 剩余红包个数（不含本次） * 全局最大值   和  全局最小值，这两者的较大者，记LOWER，当前用户的红包最大值为：当前剩余红包金额 - 剩余红包个数（不含本次） * 全局最小值  和 全局最大值，这两者的较小者，记UPPER


#### 技术方案

- 线段法：提前根据约束条件预生成红包分配方案，根据用户请求次序，分配不同金额

- 二倍均值法：根据均匀分布，完全随机获取[1, 2倍均值]，如果约束条件的红包约束对取值范围进行重约束，则取值范围改为[Max(1, LOWER), Min(20000, UPPER)]

- 截尾正态分布法：由于取值范围的上界和下届，到均值的的距离不等，出现不对称的情况


- 概率密度函数
$$
\begin{align}
f(x) = \frac{1}{\sqrt{2\pi}\sigma} exp(- \frac{(x - \mu)^2}{2 \sigma^2})
\end{align}
$$

---

![截尾正态分布](https://pic4.zhimg.com/b1080067aa9356cd8ee4b5a16e903f4c_r.jpg?source=1940ef5c "截尾正态分布")

- [截尾正态分布的期望与方差](!https://blog.csdn.net/lanchunhui/article/details/61623189)



#### reference

- http://www.phppan.com/2015/04/weixin-hongbao/
- https://blog.csdn.net/bjweimengshu/article/details/80045958
- https://www.zhihu.com/question/22625187
- https://www.zybuluo.com/yulin718/note/93148
- https://juejin.im/entry/56bd3dd16be3ffc0224a4f30
- https://blog.csdn.net/renwudao24/article/details/44463489
- https://blog.csdn.net/lanchunhui/article/details/61623189
