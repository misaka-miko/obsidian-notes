---
tags:
  - knowledge
  - physics
  - example
---
# 怎么计算第一宇宙速度
## 问题描述
给定地球半径$R$，质量$M$，卫星质量为$m$。要使卫星在距离地面高度$h$的高度围绕地球做匀速圆周运动，求解其发射速度。

## 解答
我们需要列出功能原理的表达式
假设发射速度是$v_{1}$，绕行速度为$v$，我们将当前系统看作是**机械能守恒**的，那么我们有：
$$
\frac{1}{2}mv_{1}^{2}- G \frac{Mm}{R} = \frac{1}{2}mv^{2}-G \frac{Mm}{R+h}
$$
同时在运动过程中，万有引力作为**向心力**
$$
G \frac{Mm}{(R+h)^{2}} = m \frac{v^{2}}{R+h}
$$
联立两式，可得
$$
v_{1}=\sqrt{ \frac{2GM}{R} - \frac{GM}{R+h} } \Rightarrow v_{1}=\sqrt{ gR\left( 2-\frac{R}{R+h} \right) }
$$
值得注意的是我们有$h \ll R$，上式可以近似为
$$
v_{1}=\sqrt{ gR }
$$


# Idea 

**NOTE**: 别忘记用机械能守恒，列出来了也别高兴的太早，需要观察其他可能存在的等式**联立**求解


# Reference‘s
- [[energy]]
- [[learning]]
