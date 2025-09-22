# 怎么描述运动
- 时空中*坐标*的连续变化: $(\vec{r}, t)$: 坐标原点的选取：**参考系**
- 运动的描述：坐标作为时间的**函数** $\vec{x} = f(t)$, 高维空间，矢量：$\vec{r} = \vec{f}(t)$
- 力学性质衍生量：**速度**, **加速度**
# 一维世界
时空中坐标：$(x, t)$
原点：$(0, t)$
## 参考系
用来描述物体运动而选的参考的物体
- 运动的相对性决定描述物体运动必须选取参考系
- 参考系可以任选，**方便**为主
- 不同参考系对物体运动的描述**不同**
- 参考系可以运动

## 平均速度
$$
v_{av-x} = \frac{x_{2} - x_{1}}{t_{2} - t_{1}} = \frac{\Delta x}{\Delta t}
$$
## 瞬时速度
$$
v_{x} = \lim_{ \Delta t \to 0 } \frac{\Delta x}{\Delta t} = \frac{dx}{dt}
$$
## 加速度
类似的，我们也可以定义**平均加速度**与**瞬时加速度**
$$
a_{av-x} = \frac{v_{2x} - v_{1x}}{t_{2} - t_{1}} = \frac{\Delta v_{x}}{\Delta t} 
$$
$$
a_{x} = \frac{dv_{x}}{dt} = \frac{d}{dt}\left( \frac{dx}{dt} \right) = \frac{d^{2}x}{dt^{2}}
$$

## 从加速度出发
变加速直线运动
$$
v_{x} -v_{0x} \approx \sum_{i} a_{x}(t_{i})\Delta t = \lim_{ \Delta t \to 0} = \int ^{t_{2}} _{t_{1}} a_{x}(t)dt
$$

# 高维空间
3+1维时空中的坐标 $(\vec{r}, t)$ 
$$
\vec{r} = x \vec{i} + y \vec{j} +z\vec{k}
$$
矢量的性质
- 大小 $|\vec{r}|$
- 方向 $\frac{\vec{r}}{|\vec{r}|}$ 
- 描述力，力矩和能量时，需要可以**乘**

### 平均速度矢量
$$
\vec{v_{av}} = \frac{\vec{r_{2}} - \vec{r_{1}}}{t_{2}- t_{1}} = \frac{\Delta \vec{r}}{\Delta t}
$$
### 瞬时速度矢量
$$
\vec{v} = \lim_{ \Delta t \to 0 } \frac{\Delta\vec{r}}{\Delta t} = \frac{d\vec{r}}{dt}
$$


## 笛卡尔坐标
$$
\vec{v} = \frac{d\vec{r}}{dt} = \frac{dx}{dt} \vec{i} + \frac{dy}{dt}\vec{j}+\frac{dz}{dt}\vec{k} = v_{x}\vec{i}+v_{y}\vec{j}+v_{z}\vec{k}
$$
$$
\frac{d\hat{i}}{dt} = \frac{d\hat{j}}{dt} = \frac{d\hat{k}}{dt} = 0
$$
笛卡尔坐标单位矢量**不随时间变化**

## 极坐标系
极坐标下，单位矢量是**时间的函数** $\vec{r} = r(t)\vec{e_{r}}(t)$
