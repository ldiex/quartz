# 光度学基本概念
## 辐射能通量和光通量
- 光度学 - 人眼（主观）
- 辐射度学 - 功率（物理）
类似于[[Radiometry#辐射通量(Radiant Flux)|辐射通量]], 定义*光通量*
$$
\Phi = K_M \int V(\lambda)\psi(\lambda) \mathrm{d} \lambda
$$
其中$\phi(\lambda)$是*辐射能谱密度*, $V(\lambda)$表示人眼对光波的敏感性, $\Phi$的单位是流明$\mathrm{lumen}$

对于一个点光源, 这表示通过包含它的一个闭合曲面上的光能（按照人眼敏感度加权）的总和
## 发光强度
当光源的线度足够小, 或距离足够远, 从而眼晴无法分辨其形状时, 我们把它叫做*点光源*.  在实际中多数情形里, 我们看到的光源有一定的发光面积, 这种光源叫做*面光源*, 或*扩展光源*

点光源$Q$沿某一方向$\boldsymbol r$的*发光强度*$I$定义为**沿此方向上单位立体角内发出的光通量**.  我们以$\boldsymbol r$为轴取一立体角元$\mathrm{d} \Omega$, 设$\mathrm{d} \Omega$内的光通量为$\mathrm{d} \Phi$, 则沿$\boldsymbol r$方向的发光强度为
$$
I = \dfrac{\mathrm{d} {\Phi}}{\mathrm{d} {\Omega}}
$$

单位是$\mathrm{Cd}$, *坎德拉*
![[光学-发光强度.png]]
## 亮度
扩展光源表面的每块面元$\mathrm{d} S$沿桌方向$\boldsymbol r$有一定的发光强度$\mathrm{d} I$. 当一个观察者迎着$\boldsymbol r$的方向观察$\mathrm{d} S$时, 它的投影面积为$\mathrm{d} S^* = \mathrm{d} S \cos \theta$. 面元$\mathrm{d} S$沿$\boldsymbol r$方向的光度学亮度（简称亮度）$B$定义为在此方向上单位投影面积的发光强度
$$
B = \dfrac{\mathrm{d} I}{\mathrm{d} S \cos \theta} = \dfrac{{\mathrm{d}}^2 \Phi}{\mathrm{d} \Omega \mathrm{d} S \cos\theta}
$$
单位为$\mathrm{Sb}$, *熙提*
![[光学-亮度.png]]
由[[Imagery#Lagrange-Helmholtz 不变量 | Lagrange - Helmholtz 不变量]] 可知亮度是几何光学中的不变量
人眼对光线强度的感知主要来自于亮度, 而不是总的光通量

## 余弦发射体
又称为*漫射体*, *Lambert 发光体*, 其发光强度满足*Lambert 定律*
$$
I = I_0 \cos \theta
$$
即从理想的漫反射表面或理想的漫反射体观察到的辐射强度或发光强度与**观察者的视线与表面法线之间的夹角**θ的余弦成正比

一个均匀的球形余弦发射体, 从远处的观察者看来, 与同样半径同样亮度的一个均匀发光圆盘无异. 因为我们可以把面对观察者的半球上每个面元$\mathrm{d} S$投影到圆盘上, 得到一个面积为$\mathrm{d} S^* = \mathrm{d} S \cos \theta$的面元. 这两个面元在指向观察者方上的发光强度和投影面积都是一样的, 因而亮度也一样

![[光学-余弦发光体.png]]

太阳看起来近似像一个亮度均匀的圆盘, 这表明它接近于一个余弦发射体此外, 日常生活里常见的光源, 许多接现实中大部分的发光体都是余弦发光体
## 定向发射体
利用天线或其他波导结构来控制波束的形状和方向, 如激光

## 照度
*照度（illuminance）* 是每单位面积所**接收**到的光通量；可理解为: 单位面积内获得多少光
$$
E = \dfrac{\mathrm{d} {\Phi'}}{\mathrm{d} {S'}}
$$
单位是$\mathrm{Lux, lx}$, *勒克斯*
### 点光源照度

对于发光强度为$I$的点光源, 其产生的光通量和照度
$$
\begin{aligned}
\mathrm{d} \Phi' &= I \mathrm{d} \Omega = I\mathrm{d} S' \cos \theta / r^2 \\
\implies &E = \dfrac{I \cos \theta}{r^2}
\end{aligned}
$$
![[光学-点光源照度.png]]
### 面光源照度
在光源表面和被照表面各取一个面元$\mathrm{d} S$和$\mathrm{d} S'$, 令二者连线和各自**法线**的夹角未$\theta, \theta'$, 面光源的亮度为$B$, 则由$\mathrm{d} S$发出并照射在$\mathrm{d} S'$上的光通量是
$$
\begin{aligned}\mathrm{d}\Phi^{\prime}=&B\mathrm{d}\Omega\mathrm{d}S\mathrm{cos}\theta=B\bigg(\frac{\mathrm{d}S^{\prime}\mathrm{cos}\theta^{\prime}}{r^2}\bigg)\mathrm{d}S\mathrm{cos}\theta\\=&\frac{B\mathrm{d}S\mathrm{d}S^{\prime}\mathrm{cos}\theta\mathrm{cos}\theta^{\prime}}{r^2}\end{aligned}
$$
于是有
$$
E = \iint_{\text{光源表面}} \dfrac{B\mathrm{d} S \cos \theta \cos \theta'}{r^2}
$$

![[光学-面光源照度.png]]
## 总结
- 光通量: 实际计算中的中间转化量
- 发光强度: 描述光源的性质, 只和光源本身有关, 单位立体角内的光通量
- 亮度: 描述光源, 但是和观察角度和距离有关, 单位投影面积上的发光强度
- 照度: 描述被照射面, 单位面积上接受到的光通量
# 像的亮度、照度和主观亮度
## 像的亮度
人眼瞳孔接收很小的立体角, 视细胞很小, 像的亮度是单位立体角像的光通量$B$

对于理想光具组$B'  = kB$ 其中$k$是*光具组的透过率*

对于单个折射面$\dfrac{B'}{B} = k(\dfrac{n'}{n})^2$
## 像的照度
对于余弦发射体 $B = \dfrac{E}{\pi}$
对于光具组
