# 流和输运
- 系统从非平衡态趋向平衡态的变化过程为*输运过程*
- 非平衡态中存在宏观物理量（能量、动量、质量等）的不均匀，从而导致相应物理量的传递
- 物理量的传递形成相应的*流*
- 在孤立系统中，这些物理量的传递将使系统各区域的差异逐渐消失，从而促使热力学系统从非平衡态向平衡态过渡
- 对于气体而言，气体分子的碰撞决定着输运过程的性质

## 分类
### 热传导
系统各区域温度不均匀而使**能量（热量）** 从高温区域传递到低温区域的现象
### 扩散
系统各区域浓度不均匀而使**质量（粒子）** 从浓度高的区域传递到低浓度区域的现象
### 黏性
系统各区域粒子定向速度不均匀而使**动量**从动量高的区域传递到低动量区域的现象

# 输运过程的宏观规律
## 黏性现象的宏观规律
### 稳恒层流中的黏性现象
当气体各层流速不同时，通过任一平行于流速的截面，相邻两部分气体将沿平行于截面方向互施作用力；力的作用结果总是使流速较慢的那部分加速，而使流速较快的那部分减速. 这种相互作用力称为*内摩擦力*或*黏性*

### Newton 黏性定律
设气体平行于$xOy$平面沿$y$轴正方向流动，流速$u$是$z$的函数. 如在$z = z_0$处垂直于$z$轴取一截面$\mathrm{d} S$将气体分成上下两部分. 下层气体将通过该截面施与上层气体一平行于$y$轴的黏性力
$$
F(z_0) = -\eta \left(\dfrac{\mathrm{d} {u}}{\mathrm{d} {z}}\right)_{z_0} \mathrm{d} S
$$
其中$\eta$为气体的*黏度*，单位为$\mathrm{Pa} \cdot \mathrm{s}$

单位时间内通过$\mathrm{d} S$面元由下层气体传递给上册气体的动量为
$$
\mathrm{d} K(z) = F(z) \mathrm{d} t = - \eta \left(\dfrac{\mathrm{d} {u}}{\mathrm{d} {z}}\right) \mathrm{d} S \mathrm{d} t
$$
负号表明动量传递的方向与速度梯度的方向相反，即动量总是沿着速度减小的方向传递

**流体黏性现象的微观本质是分子定向运动动量的迁移，而这种迁移是通过气体分子的无规则热运动和碰撞来实现的**

### 黏度的测量：旋转黏度计
- 外筒：半径为$R + \delta \; (\delta \ll R)$, 恒定角速度$\omega$转动
- 内筒：半径$R$,有扭丝悬吊，两筒长度均为$L$
- 扭力距$M$可以由扭丝上的反光镜$C$的偏转角度测定
- 夹层流体的速度梯度可以近似为$\omega R / \delta$
- 待测流体的黏度$\eta = \dfrac{M\delta}{2\pi R^3 L \omega}$
- **气体黏度随温度升高而增大**
## 热传导现象的宏观解释
当系统内各部分的温度不均匀时，就有热量从高温处传递到低温处，这种现象称为热传导现象
### Fourier 定律
考虑气体层之间的热传导，设气层平行于$xOy$平面
- 各气层间无相对运动
- 各气层的分子数密度可以不相同， 但气层间无宏观粒子流
- 各气层的温度$T$是$z$的函数
如果在$z = z_0$处垂直于$z$轴取一截面$\mathrm{d} S$将气体分成上下两部分，在$\mathrm{d} t$时间间隔内下层气体将通过该截面项上层气体传递热量
$$
\mathrm{d} Q = - \kappa \left(\dfrac{\mathrm{d} {T}}{\mathrm{d} {z}}\right)_{z_0} \mathrm{d} S \mathrm{d} t
$$
其中$\kappa$为*导热系数*，单位为$\mathrm{W}/(\mathrm{m}\cdot \mathrm{K})$
定义*热流量*
$$
q = \dfrac{\mathrm{d} Q}{\mathrm{d} S \mathrm{d} t} = - \kappa \left(\dfrac{\mathrm{d} {T}}{\mathrm{d} {z}}\right)_{z_0}
$$
负号表示热量沿温度减小的方向传递

**气体热传导现象的微观本质是分子热运动能量的定向迁移，而这 种迁移是通过气体分子的无规则热运动和碰撞来实现的**
## 扩散现象的宏观规律
系统中各部分的密度不均匀时，就有质量从高密度处传递到低密度处，这种现象称为*扩散现象*

### 压强扩散
扩散过程中系统的压强分布不均匀
密度不均匀$\to$数密度不均匀$\to$压强不均匀$\to$宏观气流

如一种气体在真空中的扩散
### 纯扩散
扩散过程中系统的压强、温度分布均匀且恒定， 无宏观气流
扩散是由于分子热运动导致的

如种理想气体在某定容容器中之间的隔板被移除后的扩散

### Fick 定律
左侧$\alpha$气体，右侧$\beta$气体，$z$轴从左侧延伸到右侧
在$\mathrm{d} t$时间间隔内通过$\mathrm{d} S$面元从左侧扩散到右侧的$\alpha$分子数
$$
\mathrm{d} N_{\alpha} = -D_{\alpha\beta} \left(\dfrac{\mathrm{d} {n_\alpha}}{\mathrm{d} {z}}\right) \mathrm{d} S \mathrm{d} t
$$
其中*互扩散系数*$D_{\alpha\beta}$, 单位为$\mathrm{m}^2/\mathrm{s}$
负号表示扩散总是沿着浓度降低的方向进行

$\alpha$分子粒子流
$$
J_\alpha = - D_{\alpha\beta} \left(\dfrac{\mathrm{d} {n_\alpha}}{\mathrm{d} {z}}\right)
$$
$\beta$分子粒子流
$$
J_\beta = - D_{\beta\alpha} \left(\dfrac{\mathrm{d} {n_\beta}}{\mathrm{d} {z}}\right) = -J_\alpha
$$
因为
$$
D_{\alpha\beta} = D_{\beta \alpha}
$$

# 输运过程的微观解释
## 基本出发点
### 气体密度要求
$$
d \ll \bar \lambda \ll (\Delta V)^{1/3}
$$
- 气体须足够稀薄，平均自由程必须远大于有效直径
- 气体不能太稀薄：从非平衡态气体中取出任意一个小体积元，从宏观上看它很小，但从微观上看它仍然很大
### 局部平衡假设
任一宏观小微观大的体积元$\Delta V$，仍可用确定的宏观状态参量来描述它的状态；

整个系统可用在空间和时间上都变化的状态参量来确定它的状态

系统中宏观参量的变化非常缓慢，它们的二阶导数可忽略

## 初级气体分子动理论
输运现象是因某个宏观参量分布不均匀引起的相应物理量$W$的迁移，形成某种“流”$J$

物理量$W$的迁移是通过分子的**热运动**来输运的；而输运过程中物理量的交换，则是通过**碰撞**来完成的

### 物理量的输运
在$\mathrm{d} t$时间内沿$+z$方向净流过面元$\mathrm{d} S$的某物理量为
$$
\mathrm{d} W = \mathrm{d} S \mathrm{d} t\left(\Gamma \times\boxed{分子携带的物理量}\right)_A - \mathrm{d} S \mathrm{d} T \left(\Gamma \times\boxed{分子携带的物理量}\right)_B
$$
其中$\Gamma$是气体分子的碰壁数，由[[Maxwell Distribution of Speed | Maxwell 速率分布]] 给出
$$
\Gamma = n \int_{0}^{\infty} \mathrm{d} v_x f_M(v_x) v_x = n \bar v /4
$$
或者认为
$$
\Gamma = n\bar v /6
$$
上述两个情形都是基于气体分子的动理论得出的, 但是它们的推导过程和假设条件略有不同:

- $\Gamma = n \bar v /4$ 假设气体分子在各个方向上的运动是均匀的,即每个方向上的速度分量相等
- $\Gamma = n \bar v /6$ 假设气体分子在三个坐标轴方向上的速度分量是相互独立的. 可以把分子等分为$6$队，分别沿平行于$x, y,z$轴的正负方向运动；只有沿着$+z$方向运动的分子可以通过截面$\mathrm{d} S$
由此定义*物理量流度*
$$
J_{A \to B} = \dfrac{\mathrm{d} {W}}{\mathrm{d} {t}} = \dfrac{1}{4}[(nq\bar v)_A - (nq\bar v))_B]\mathrm{d} S
$$
这里当$q = m$时，$J$就代表质量流；$q = m\bar v$时，$J$就代表动量流
设粒子越过$\mathrm{d} S$后在$\alpha \bar \lambda$的路径中被同化，那么
$$
\begin{aligned}
J_{A \to B} &= \dfrac{1}{4}[(nq\bar v)_{z = z_0 - \alpha \bar \lambda} - (nq\bar v))_{z =z_0 + \alpha \bar \lambda}]\mathrm{d} S \\
&= -\dfrac{1}{2}\dfrac{\mathrm{d}}{\mathrm{d} {z}} (nq\bar v)\bigg\vert_{z = z_0} \alpha \bar \lambda \mathrm{d} S
\end{aligned}
$$
## 黏性现象的微观解释
设$q = m\boldsymbol u$, ($\boldsymbol u$是定向运动速度，$\bar v$是热运动速度)
$$
J_p = -\dfrac{\alpha}{2} \dfrac{\mathrm{d}}{\mathrm{d} {z}}(nm\bar v \boldsymbol u) \bigg\vert_{z = z_0} \bar \lambda \mathrm{d} S =  -\dfrac{\alpha}{2} \rho \bar v \bar \lambda \dfrac{\mathrm{d} {\boldsymbol u}}{\mathrm{d} {z}} \mathrm{d} S
$$
代入$\bar \lambda$的[[Mean Free Path | 公式]] ，可以得到粘滞系数$\eta$的关系式
$$
\eta = \dfrac{\alpha}{2}\rho \bar v \dfrac{1}{\sqrt{2} \sigma n} = \dfrac{\alpha}{2\sqrt{2}} \dfrac{m \bar v}{\sigma}
$$
再代入$\bar v = \sqrt{(8k_BT)/(\pi m)}$，有
$$
\eta = \dfrac{\alpha}{\sigma} \sqrt{\dfrac{mk_B T}{\pi}}
$$
## 热传导现象的微观解释
设$q = \bar \epsilon = c_V m T$, 这里$c_V$是[[Equipartition Theorem#理想气体的热容|定体比热容]] 
$$
h = J_E = -\dfrac{\alpha}{2}\dfrac{\mathrm{d}}{\mathrm{d} {z}}(nc_V mT \bar v) \bigg\vert_{z=z_0} \bar \lambda \mathrm{d} S
$$
带入$\bar v, \bar \lambda$， 若假设$n$处处相等
$$
\kappa = - \dfrac{3}{4\sqrt{2}} \dfrac{\alpha c_Vm\bar v}{\sigma} = -\dfrac{3}{2} \dfrac{\alpha c_V}{\sigma} \sqrt{\dfrac{mk_BT}{\pi}}
$$
上面的推导比较粗糙，常数因子并不准确. 例如对于近似理想气体的系统，考虑它的热传导过程时，更精确的假定是压强处处相等. 此时$p = nK_B T = \text{const}$，在计算过程中将得到不同的常数因子. 
## 扩散现象的微观解释
设$q = m$假设系统温度（或$\bar v$）处处相同
$$
J_M = - \dfrac{\alpha}{2} \dfrac{\mathrm{d}}{\mathrm{d} {z}}(nm\bar v)\bigg\vert_{z = z_0} \bar \lambda \mathrm{d} S = -\dfrac{\alpha}{2} \bar v \bar \lambda \dfrac{\mathrm{d} {\rho}}{\mathrm{d} {z}}\mathrm{d} S
$$
即为[[Transport Process of Gases#Fick 定律 |Fick 定律]]，带入$\bar b, \bar \lambda$, 有
$$
D = \alpha \sqrt{\dfrac{k_BT}{m\pi}} \dfrac{1}{n\sigma} = \alpha\dfrac{(k_BT)^{3/2}}{(m\pi)^{1/2}} \dfrac{1}{p\sigma}
$$
## 低压下气体的输运现象
*杜瓦瓶原理*：低压下气体导热系数随着压强的降低而减小，随系统线度的减小而减弱
