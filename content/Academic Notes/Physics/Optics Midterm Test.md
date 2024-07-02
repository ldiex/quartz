# 题型
## 判断题
主要是概念
# 重点
## 几何光学
### 棱镜的最小偏向角
$$
n = \dfrac{\sin \dfrac{\alpha + \delta_\text{min}}{2}}{\sin \dfrac{\alpha}{2}}
$$
### Huggens 原理
波面上的每一个点都可以看作一个次波源，次波源波面的包络就是下一时刻的波面
### Fermat 原理
光程*平稳*：极大、极小或者为常数
### 焦深
物处在焦点附近的一个小范围内，使得像成在$[s_0, +\infty)$内。这个范围的宽度就是焦深
### 光阑光瞳和像差**不考**
### 望远镜两种型号的区别
开普勒型就是两个凸透镜，其角放大率是
$$
M = - \dfrac{f_O}{f_E}
$$
伽利略型物镜是凸透镜，目镜是凹透镜，其角放大率为
$$
M = \dfrac{f_O}{f_E}
$$
## 光度学
### 单位记忆
- 光通量：实际计算中的中间转化量 *单位 流明 $\mathrm{lm}$*
- 发光强度：描述光源的性质，只和光源本身有关，**单位立体角内的光通量** *单位 坎德拉 $\mathrm{Cd}$*
- 亮度：描述光源，但是和观察角度和距离有关，**单位投影面积上的发光强度** *单位 熙提 $\mathrm{Sb}$*
- 照度：描述被照射面，**单位面积上接受到的光通量** *单位 勒克斯 $\mathrm{lx}$*
### 点光源照度和面光源照度
$$
E = \dfrac{\mathrm{d} \Phi}{\mathrm{d} S'} = \dfrac{I \mathrm{d} \Omega}{\mathrm{d} S'} = \dfrac{I \mathrm{d} S' \cos \theta' / r^2}{\mathrm{d} S'} = \dfrac{I\cos\theta'}{r^2}
$$
$$
\mathrm{d} E = \dfrac{I\mathrm{d} \Omega}{\mathrm{d} S'} = \dfrac{B\mathrm{d} S\cos \theta' \mathrm{d} S' \cos \theta /r^2}{\mathrm{d} S'} = \dfrac{B \mathrm{d} S \cos \theta'\cos \theta}{r^2}
$$
#### 球面照度的计算
考虑球面积分，其中
$$
\mathrm{d} S = \mathrm{d} \ell_{\theta} \mathrm{d} \ell_{\varphi} = r \mathrm{d} \theta r\sin \theta \mathrm{d} \varphi
$$
一般只需积半个球面
## 电磁理论
### 偏振
可以表示任意偏振光的方程
$$
\begin{cases}
E_x = A\cos \omega t \\ E_y = A\cos (\omega t +\phi)
\end{cases}
$$
1. 自然光（部分偏振光）入射 - 反射和折射是部分偏振光
2. 圆偏振光（椭圆偏振光）入射 - 反射和折射是椭圆偏振光
3. 线偏振光入射 - 反射和折射是线偏振光，但是振动面有旋转
4. 全反射 - 反射光是椭圆偏振光
5. Brewster角入射 - 反射光是s线偏振光

#### Malus 定律
$$
I = I_0 \cos^2 \theta
$$
### Fresnel 方程
$$
\begin{gather}
R_s = \left|{\dfrac{n_1\cos \theta_i - n_2 \cos \theta_t}{n_1\cos \theta_i + n_2 \cos \theta_t}}\right|^2 \\
R_p = \left|{\dfrac{n_1\cos \theta_t - n_2 \cos \theta_i}{n_1\cos \theta_t + n_2 \cos \theta_i}}\right|^2
\end{gather}
$$
#### Brewster 角
令$R_p$等于$0$
$$
\tan \theta_i = \dfrac{n_2}{n_1}
$$
此时反射光称为$s$偏振光
## 干涉
### 波的合成
就是复振幅的合成
### 干涉项和干涉条件
*干涉项*
$$
\overline{2\boldsymbol{A}_1(p) \cdot \boldsymbol A_2(p) \cos [(\omega_1 - \omega_2)t + \delta(p)]}
$$
要让上面这项不为$0$，我们有*相干条件*
- 频率相同
- 存在着相互平行的振动分量
- 存在着稳定的相位差
### 几个重要的时间间隔
> [!note]
>几个重要的时间间隔：
> 1. 光扰动的时间周期： $T \sim 10^{-15}$ sec 
> 2. 实验观测的时间（人眼的响应时间）： $τ \sim 10^{-1}$ sec 
> 3. 探测器响应时间：$\Delta t \sim 10^{-9}$ sec
### 半波损失
等厚干涉和等倾干涉涉及到明暗条纹的，考虑**半波损失**（“汉堡包”型）
### 空间和时间相干性
#### 产生原因
空间相干性来源于扩展光源不同部分发光的独立性
时间相干性来源于光源发光过程在时间上的断续性
#### 结果
空间相干性主要表现在波场的横向（波前）上，集中体现在分波前干涉装置中；
时间相干性主要表现在波场的纵向（波线）上，集中体现在分振幅干涉装置中

#### 反比公式
空间相干性 $\Delta \theta b \sim \lambda$
时间相干性 $\tau_0 \Delta \nu \sim 1$

相干区域和相干时间都不是一个绝对的界限，实际上相干区域和相干时间内也有非相干的成分，而相干区域和相干时间之外，也有相干的成分，只是主导地位的不同，部分相干是最为普遍的，而反衬度则是相干程度的一种度量

### Newton 环
### 增透、增反膜
#### 增透膜
要求$n_1 < n < n_2$
当$n = \sqrt{n_1n_2}$时完全消除反射光
#### 增反膜
$n_1 < n > n_2$

