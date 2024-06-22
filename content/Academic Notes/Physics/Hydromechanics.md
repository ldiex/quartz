# 流体静力学
## 应力
$$
\boldsymbol T = \dfrac{\mathrm{d} {\boldsymbol F}}{\mathrm{d} {S}}
$$
当$\boldsymbol T$的方向和$\hat {\boldsymbol n}$相同时，$\boldsymbol T$称为张应力；相反时，$\boldsymbol T$称为压应力. 在流体中，流体质元通常相互挤压，$\boldsymbol T$为压应力，取其大小，改记成
$$
p = \dfrac{\mathrm{d} {F}}{\mathrm{d} {S}}
$$
称为压强. 流体中任意一个点部位的压强**和面元$\mathrm{d} S$的取向无关**
## 浮力
$$
\boldsymbol F_{\text{浮}} = -\oint_\mathcal{V} \rho \boldsymbol g \mathrm{d} V
$$
浮力的作用中心，也就是**浮心**，是浸入流体的体积的几何中心
# 流体动力学
## 连续性方程
对于**不可压缩流体**，有
$$
\oint_\mathcal{S} \boldsymbol v \cdot \mathrm{d}{\boldsymbol S} = 0
$$
在一个流管中可以简化为
$$
v_1S_1 = v_2S_2 \implies Q_1 = Q_2
$$
## 定常流动
速度场和时间无关的流动被称为**定常流动**
### 动量定理
$$
\boldsymbol F_\text{合} = \rho Q(\boldsymbol v_2 - \boldsymbol v_1) = Q_m(\boldsymbol v_2 - \boldsymbol v_1)
$$
其中$Q_m =\rho Q = \rho Sv$是**质量流量**
### Bernoulli 方程
$$
p + \frac{1}{2}\rho v^2 + \rho g h = \text{constant}
$$
**Tips**: 先确定参考系和要分析的流体对象（只能是一种密度均匀的不可压缩流体），然后设置$h$的零点，建立$h$坐标系，最后再开始列Bernoulli方程. 
## 黏性流体的流动
### 黏力
定义粘力
$$
\mathrm{d} {\boldsymbol f} = \eta (\nabla {\boldsymbol v}) \mathrm{d} S \implies \mathrm{d} f = \eta \dfrac{\mathrm{d} {v}}{\mathrm{d} {z}}\mathrm{d} S
$$
可以通过观察$v$随$z$变化的趋势判断$f$是动力还是阻力，这里$\eta$被称为流体的**黏度**
### 层流和湍流
经验公式，定义
$$
Re = \frac{\rho v r}{\eta}
$$
为**Reynolds数**，其中$r$为流管半径. $Re$和**运动粘度**$\dfrac{\eta}{\rho}$成反比. 一般来说，运动粘度越低，$Re$越大，越容易发生湍流. 对于水平流管中的流体，其临界值大概在$1000 \sim 2000$左右
### Poiseuille 公式
在Reynolds数较小时，黏性流体在水平管道内作层流. 如果流动是定常的，从中央轴到管壁，流速有一稳定的法向分布$v = v(r)$. 现在取长为$L$的一段管道，对于半径为$r$的一段流体有
$$
(p_2 - p_1)\pi r^2 = \eta \dfrac{\mathrm{d} {v}}{\mathrm{d} {r}} 2\pi r L
$$
得到
$$
\mathrm{d} v = \frac{(p_2 - p_1) r}{2\eta L} \mathrm{d} r
$$
积分有
$$
v = \frac{p_1 - p_2}{4\eta L}(R^2 - r^2)
$$
管道的体积流量便是
$$
Q = \int_0^E v(r) 2\pi r\mathrm{d} r = \frac{p_1-p_2}{8\eta L} \pi R^4
$$
利用此结果可以方便地测定流体的黏度$\eta$
### 黏性流体中运动物体的受力
#### 黏性阻力
半径为$r$，平动速度为$v$的球体，理论上可以导得沿运动方向所受的合成黏性阻力大小为
$$
f_v = 4\pi r \eta v
$$
#### Stokes 公式
运动球体在流体中受到的阻力
$$
f = \text{黏性阻力} + \text{压差阻力} = 4\pi r\eta v + 2\pi r \eta v = 6 \pi r \eta v
$$





