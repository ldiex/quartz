# 二重积分
## 二重积分的定义
设$D$为$xy$平面上可求面积的有界[[Planar Point Set#闭域|闭区域]]，$f(x,y)$为定义在$D$上的函数. 用任意曲线把$D$分割成$n$个可求面积的小区域$\sigma_1,\ldots,\sigma_n$，以$\Delta \sigma_i$表示$\sigma_i$的面积，这些小区域构成$D$的一个分割$T$，以$d_i$表示$\sigma_i$的直径，称$\Vert T\Vert =\max d_i$ 为分割$T$的*细度*，在每个$\sigma_i$上任取一点$(\xi_i,\eta_i)$作和式
$$
\sum_{i=1}^n f(\xi_i,\eta_i)\Delta \sigma_i
$$
称它为函数$f(x,y)$在$D$上属于分割$T$的一个*积分和*，$(\xi_i,\eta_i)$称为*介点*

设$f(x,y)$是定义在可求面积的有界闭区域$D$上的函数，$J$是一个确定的数，若对于任给的实数$\varepsilon$，总是存在某个正数$\delta$，使得对于$D$的任意分割$T$，当它的细度$\Vert T\Vert < \delta$时，属于$T$的所有积分和都有
$$
\left| \sum_{i = 1}^n f(\xi_i,\eta_i)\Delta \sigma_i -J\right| < \varepsilon 
$$
则称$f(x,y)$在$D$上*可积*，数$J$称为$f(x,y)$在$D$上的*二重积分*，记作
$$
J = \iint_D f(x,y)\mathrm{d} \sigma 
$$
可以把$J$在几何上看做是以$z =f(x,y)$为曲顶，$D$为底的曲顶柱体的*有向体积*. 

如果采用平行于坐标轴的直线网来分割$D$，则可以把上面的$J$记作
$$
J = \iint_Df(x,y)\mathrm{d} x \mathrm{d} y
$$
## 二重积分的可积性
类似于一元积分，我们可以定义*Darboux上和*和*下和*
$$
\begin{aligned}
S(T) = \sum_{i = 1}^n \sup_{(x,y) \in \sigma_i}f(x,y) \Delta\sigma_i; \\
s(T) = \sum_{i = 1}^n \inf_{(x,y) \in \sigma_i}f(x,y) \Delta\sigma_i
\end{aligned}
$$
则$f(x,y)$在$D$上*可积*的**充要条件**是
$$
S(T) = s(T),\; \Vert T \Vert \to 0
$$
并且有界闭区域$D$上的**连续函数必然可积**，或者更一般地，**设$f(x,y)$在有界闭域$D$上有界，且其不连续点集$E$是零面积集，则$f(x,y)$在$D$上可积**

## 二重积分的性质
### 线性
$$
\iint_D\left[ \alpha f(x,y)+\beta g(x,y) \right] \mathrm{d} \sigma = \alpha\iint_Df(x,y)\mathrm{d} \sigma + \beta\iint_D g(x,y)\mathrm{d} \sigma
$$
且当$D_1\cap D_2 = \emptyset$时，
$$
\iint_{D_1\cup D_2} f(x,y)\mathrm{d} \sigma = \iint_{D_1} f(x,y)\mathrm{d} \sigma + \iint_{D_2} f(x,y)\mathrm{d} \sigma
$$
### 中值定理
若$f(x,y)$在有界闭区域$D$上**连续**，则存在$(\xi,\eta)\in D$使得
$$
\iint_D f(x,y) \mathrm{d} \sigma = f(\xi,\eta) S_D
$$
这里$S_D$是区域$D$的面积

## 直角坐标系下二重积分的计算
### 和累次积分的关系
若$D = [a,b]\times[c,d]$，且右边的积分存在，则有
$$
\iint_D f(x,y) \mathrm{d} \sigma = \int_a^b \mathrm{d} x \int_c^d f(x,y) \mathrm{d} y = \int_c^d \mathrm{d} y \int_a^bf(x,y)\mathrm{d} x
$$
也就是说**积分顺序是任意**的
### 有一组平行边的情况
这时候我们可以把平面区域分成
- $x$型区域$D = \left\{ (x,y)\mid y_1(x)\le y \le y_2(x),\; a\le x \le b \right\}$
- $y$型区域$D = \left\{ (x,y) \mid x_1(y) \le x \le x_2(y),\;c\le y \le d\right\}$
则可以分别通过
$$
\iint_Df(x,y)\mathrm{d} \sigma = \int_a^b\mathrm{d} x\int_{y_1(x)}^{y_2(x)} f(x,y)\mathrm{d} y
$$
和
$$
\iint_Df(x,y)\mathrm{d} \sigma = \int_a^b\mathrm{d} y\int_{x_1(y)}^{x_2(y)} f(x,y)\mathrm{d} x
$$
来计算
# Green公式
## 用曲线积分计算二重积分
设区域$D$的[[Planar Point Set#界点|边界]]$L$由一条或几条光滑曲线组成. 边界曲线的正方向规定为：当人沿边界行走时，区域$D$总是在他的左边.

若函数$P(x,y),\;Q(x,y)$在闭区域$D$上连续，且有连续的一阶偏导数，则有
$$
\iint_D\left( \frac{ \partial Q }{ \partial x } -\frac{ \partial P }{ \partial y }  \right) \mathrm{d}\sigma = \oint_LP \mathrm{d}x + Q \mathrm{d}y
$$
设$\boldsymbol f(x,y)= P(x,y) \boldsymbol {\hat x} + Q(x,y) \boldsymbol{\hat y}$，$\mathrm{d} \boldsymbol s = \boldsymbol{\hat x} \mathrm{d}x + \boldsymbol{\hat y} \mathrm{d}y$，$\nabla = \frac{ \partial}{ \partial x }\boldsymbol{\hat x} + \frac{ \partial  }{ \partial y }\boldsymbol{\hat y}$,则有
$$
\iint_D (\nabla \times \boldsymbol f) \mathrm{d}\sigma = \oint_L \boldsymbol f \cdot \mathrm{d}\boldsymbol {s}
$$
称此为*Green公式*
## 曲线积分与路线的无关性
### 单联通区域
若对于平面区域$D$上任一封闭曲线，皆可不经过$D$以外点而连续收缩于$D$的某一点，则称此平面区域为*单连通区域*，否则称为*复连通区域*.

单连通区域也可以这样叙述：$D$内任一封闭曲线所围成的区域内只含有$D$中的点. 更直观地说，单连通区域就是没有“洞”的区域，复连通区域是有“洞”的区域

### 单连通闭区域的性质
设$D$是单连通闭区域，若函数$P(x,y),Q(x,y)$在$D$内连续，且具有一阶连续偏导数，则以下四个条件等价
1. 沿$D$内任一按段光滑封闭曲线$L$，有
$$
\oint_L P \mathrm{d}x+ Q \mathrm{d}y = 0
$$
2. 对$D$中任一按段光滑曲线$L$，曲线积分
$$
\int_L P \mathrm{d}x+ Q \mathrm{d}y
$$
与路线无关，只与$L$的起点和终点有关
3. $P\mathrm{d}x+ Q \mathrm{d}y$是$D$内某一函数$u(x,y)$的[[Differential of Multivariable Functions#全微分|全微分]]，即在$D$内有
$$
\mathrm{d}u = P \mathrm{d}x+Q \mathrm{d}y
$$
4. 在$D$内处处成立
$$
\frac{ \partial P }{ \partial y } = \frac{ \partial Q }{ \partial x } 
$$

## 用来求原函数
如果$P,Q$满足上述四个条件中的任意一个（一般判定满足$\displaystyle \frac{ \partial P }{ \partial y }= \frac{ \partial Q }{ \partial x }$最为方便），则说明了二元函数在以固定的$A(x_0,y_0)$为起点，可变的$B(x,y)$为终点的曲线$L$上有
$$
\begin{aligned}
u(x,y) &= \int_{L} P \mathrm{d}x + Q \mathrm{d}y = \int_{A(x_0,y_0)}^{B(x,y)} P(s,t) \mathrm{d}s+ Q(s,t) \mathrm{d}t \\
& = \int_{x_0}^xP(s,y_0) \mathrm{d}s + \int_{y_0}^yQ(s,t) \mathrm{d}t\quad (x_0,y_0) \to (x,y_0) \to(x,y) \\
& = \int_{x_0}^xP(s,t) \mathrm{d}s + \int_{y_0}^yQ(x_0,t) \mathrm{d}t\quad (x_0,y_0) \to (x_0,y) \to(x,y) 
\end{aligned}
$$
两条不同的路径给出了不同的积分方式，但是最终的积分结果总是具有性质
$$
\mathrm{d}u = P \mathrm{d}x + Q \mathrm{d}y
$$
也就是说，我们利用上面的积分找到$P\mathrm{d}x + Q \mathrm{d}y$的一个*原函数*

# 二重积分的变量变换
## 二重积分的变量变换公式
设变换$T:x= x(u,v),\;y = y(u,v)$将$uv$平面上按段光滑封闭曲线所围成的闭区域$\Delta$一对一地映射成$xy$平面上的闭区域$D$，函数$x(u,v),\;y(u,v)$在$\Delta$内分别具有一阶连续偏导数且它们的[[Implicit Function#隐映射定理|Jacobian行列式]]
$$
J(u,v) = \frac{ \partial (x,y) }{ \partial (u,v) } = \det \begin{pmatrix}
\dfrac{ \partial x }{ \partial u }  & \dfrac{ \partial x }{ \partial v } \\
\dfrac{ \partial y }{ \partial u }  & \dfrac{ \partial y }{ \partial v }  
\end{pmatrix} \neq 0
$$
则区域$D$的面积
$$
\mu(D) = \iint_\Delta \left|J(u,v)\right| \mathrm{d}u \mathrm{d}v
$$
注意这里是先取行列式再取绝对值
$$
\mu (D) = \iint_\Delta \left|\begin{vmatrix}
\dfrac{ \partial x }{ \partial u }  & \dfrac{ \partial x }{ \partial v } \\
\dfrac{ \partial y }{ \partial u }  & \dfrac{ \partial y }{ \partial v }  
\end{vmatrix}\right| \mathrm{d}u \mathrm{d}v
$$
且对于在$D$上可积的函数$f(x,y)$，有
$$
\iint_D f(x,y) \mathrm{d}x \mathrm{d}y = \iint_\Delta f(x(u,v),\;y(u,v)) \left|J(u,v)\right| \mathrm{d}u \mathrm{d}v
$$
例如要求积分$\displaystyle \iint_D\exp(\dfrac{x-y}{x+y}) \mathrm{d}x \mathrm{d}y$，其中$D$是$x=0,y=0,x+y=1$围成的区域，那么我们可以作变换
$$
T:(x,y) = \left[ \dfrac{1}{2}(u+v), \;\dfrac{1}{2}(v-u) \right] 
$$
则有
$$
J(u,v) = \begin{vmatrix}
\dfrac{1}{2} & \dfrac{1}{2}  \\
-\dfrac{1}{2} & \dfrac{1}{2}
\end{vmatrix} = \dfrac{1}{2} \neq 0
$$
而新的区域由$y = 1,\;y = x,\;y = -x$围成，有
$$
\begin{aligned}
\iint_D \exp(\dfrac{x-y}{x+y}) \mathrm{d}x \mathrm{d} y  & = \iint_\Delta \exp(\dfrac{u}{v}) \dfrac{1}{2}\mathrm{d}u \mathrm{d}v = \dfrac{1}{2} \int_0^1 \mathrm{d}v \int_{-v}^v \exp(\dfrac{u}{v}) \mathrm{d}u \\
& = \dfrac{1}{2} \int_0^1 v(e-\dfrac{1}{e}) = \dfrac{1}{4}\left( 1-\dfrac{1}{e} \right) 
\end{aligned}
$$
又例如求抛物线$y^{2}=mx,\;y^{2} = nx$和直线$y = \alpha x,\;y = \beta x$所围区域$D$的面积，其中$0<m<n,$$\;0<\alpha<\beta$，则可以作变换
$$
x = \dfrac{u}{v^{2}},\quad y = \dfrac{u}{v}
$$
则有在$uv$平面上$\Delta = [m,n]\times[\alpha,\beta]$，且
$$
J(u,v) = \begin{vmatrix}
\dfrac{1}{v^{2}} & - \dfrac{2u}{v^3} \\
\dfrac{1}{v}
 & - \dfrac{u}{v^{2}}\end{vmatrix} = \dfrac{u}{v^4} >0
$$
所以
$$
\begin{aligned}
\mu(D) &= \iint_D \mathrm{d}\sigma = \iint_\Delta  \dfrac{u}{v^4} \mathrm{d}u \mathrm{d}v  \\
&= \int_\alpha^\beta  \dfrac{\mathrm{d}v}{v^4} \cdot \int_m^n u \mathrm{d}u = \dfrac{(n^{2}-m^{2})(\beta^3-\alpha^3)}{6\alpha^3\beta^3}
\end{aligned}
$$
## 用极坐标计算二重积分
当积分区域是圆域或圆域的一部分时，或者被积函数的形式为$f(x^{2}+y^{2})$时，则我们一般采用极坐标变换
$$
T : (x,y) = (r\cos \theta,\;r\sin \theta)
$$
其对应的函数行列式为
$$
J(r,\theta) = \begin{vmatrix}
\cos \theta & -r\sin \theta \\
\sin \theta  & r\cos \theta
\end{vmatrix} = r
$$
容易知道，极坐标变换把$r\theta$平面上的矩形$[0,R]\times[0,2\pi]$变换成$xy$平面上的圆域$D=\left\{ (x,y)\mid x^{2}+y^{2}\leq R^{2} \right\}$. 但是这个对应**不是一对一的**，例如$xy$平面上的原点与$r\theta$平面上的直线$r=0$对应，且此时还有$J(r,\theta) = 0$，但是我们仍然有下列结论

设$f(x,y)$满足上节变量替换的条件，则在极坐标变换下也成立
$$
\iint_D f(x,y) \mathrm{d}x \mathrm{d}y = \iint_\Delta f(r\cos \theta, r \sin \theta) r \mathrm{d}r \mathrm{d}\theta
$$

上面的极坐标变换也可以推广到
$$
T :(x,y) = (ar\cos \theta,\;br\sin \theta)
$$
此时变换公式依然成立，且有
$$
J(r,\theta) = \begin{vmatrix}
a \cos \theta & -ar\sin \theta \\
b \sin \theta & br\cos \theta
\end{vmatrix} = abr
$$
# 三重积分
## 三重积分定义
设$f(x,y,z)$为定义在三维空间可求体积的有界闭区域$V$上的函数，$J$是一个确定的数，若对任给的正数$\varepsilon$，总存在某一正数$\delta$，使得对于$V$的任何分割$T$，只要$\Vert T \Vert<\delta$，属于分割$T$的所有积分和有
$$
\left|\sum_{i = 1}^n f(\xi_i,\eta_i,\zeta_i)\Delta V_i - J\right|<\varepsilon
$$
则称$f(x,y,z)$在$V$上可积，数$J$称为函数$f(x,y,z)$在$V$上的三重积分，记为
$$
J = \iiint_Vf(x,y,z) \mathrm{d}V = \iiint_Vf(x,y,z) \mathrm{d}x \mathrm{d}y \mathrm{d}z
$$
## 三重积分换元法
和二重积分换元法类似，如果函数行列式
$$
J(u,v,w)= \begin{vmatrix}
\dfrac{ \partial x }{ \partial u } & \dfrac{ \partial x }{ \partial v } & \dfrac{ \partial x }{ \partial w } \\
\dfrac{ \partial y }{ \partial u } & \dfrac{ \partial y }{ \partial v } & \dfrac{ \partial y }{ \partial w } \\
\dfrac{ \partial z }{ \partial u } & \dfrac{ \partial z }{ \partial v } & \dfrac{ \partial z }{ \partial w }  
\end{vmatrix} \neq 0,\;(u,v,w)\in V'
$$
则有三重积分换元公式
$$
\iiint_V f(x,y,z) \mathrm{d}x \mathrm{d}y \mathrm{d}z = \iiint_{V'} f(x(u,v,w),y(u,v,w),z(u,v,w))\left|J(u,v,w)\right| \mathrm{d}u \mathrm{d}v \mathrm{d}w
$$
### 柱坐标变换
考虑变换
$$
T : \begin{cases}
x = r\cos \theta, & 0 \leq r < +\infty \\
y = r\sin \theta, & 0 \leq \theta \leq 2\pi \\
z =z, & -\infty<z<+\infty
\end{cases}
$$
其对应的函数行列式
$$
J(r,\theta,z) = \begin{vmatrix}
\cos \theta & -r\sin \theta & 0 \\
\sin \theta & r\cos \theta & 0 \\
0 & 0 & 1
\end{vmatrix} = r
$$
故有换元公式
$$
\iiint_Vf(x,y,z) \mathrm{d}x \mathrm{d}y \mathrm{d}z = \iiint_{V'} f(r\cos \theta, r\sin \theta,z)r \mathrm{d}r \mathrm{d}\theta \mathrm{d}z
$$
### 球坐标变换
考虑变换
$$
T : \begin{cases}
x = r\sin \phi \cos \theta, & 0 \leq r < +\infty \\
y = r\sin \phi \sin \theta, & 0 \leq \phi \leq \pi \\
z = r \cos \phi, & 0 \leq \theta \leq 2\pi
\end{cases}
$$
也就有
$$
J(r,\phi,\theta) = \begin{vmatrix}
\sin \phi \cos \theta & r\cos \phi \cos\theta &-r\sin \phi \sin \theta \\
\sin \phi \sin \theta & r\cos \phi \sin \theta & r\sin \phi \cos \theta \\
\cos \phi & -r\sin \phi  & 0
\end{vmatrix} = r^{2}\sin \phi
$$
即有
$$
\iiint_Vf(x,y,z) \mathrm{d}x \mathrm{d}y \mathrm{d}z = \iiint_{V'}f(r\sin \phi \cos \theta,r\sin \phi \sin \theta,r\cos \phi)r^{2}\sin \phi \mathrm{d}r \mathrm{d}\phi \mathrm{d}\theta
$$
也可以拓展至广义球坐标变换
$$
T : \begin{cases}
x = ar\sin \phi \cos \theta, & 0 \leq r < +\infty \\
y = br\sin \phi \sin \theta, & 0 \leq \phi \leq \pi \\
z = cr \cos \phi, & 0 \leq \theta \leq 2\pi
\end{cases}
$$
相应地有
$$
J(r,\phi,\theta) = abcr^{2}\sin \phi
$$
## 重积分的应用
## 曲面的面积
设函数$f(x,y)$在$D$上具有连续的一阶偏导数，对于方程
$$
z = f(x,y),\; (x,y)\in D
$$
确定的曲面，它的面积为
$$
\Delta S = \iint_D \sqrt{ 1 + f_x^{2}(x,y) +f_y^{2}(x,y) } \mathrm{d}x \mathrm{d}y
$$
或者写成
$$
\Delta S = \iint_D \dfrac{\mathrm{d}x \mathrm{d}y}{\left|\cos \left< \boldsymbol n, \boldsymbol {\hat{z}} \right> \right|}
$$
## 质心的位置
对于某三维物体
$$
\bar{x} = \dfrac{\iiint_V x\rho(x,y,z) \mathrm{d}V}{\iiint_V \rho(x,y,z) \mathrm{d}V},\quad \bar{y} = \dfrac{\iiint_V y\rho(x,y,z) \mathrm{d}V}{\iiint_V \rho(x,y,z) \mathrm{d}V}
$$
对于平面薄板
$$
\bar{x} = \dfrac{\iint_D x \rho(x,y) \mathrm{d}\sigma}{\iint_D \rho(x,y) \mathrm{d}\sigma},\; \bar{y} = \dfrac{\iint_D y \rho(x,y) \mathrm{d}\sigma}{\iint_D \rho(x,y) \mathrm{d}\sigma}
$$
## 转动惯量
回顾力学定义
$$
J_o = \iiint_V R^{2}\mathrm{d}m = \iiint \Vert \overrightarrow{OR} \Vert ^{2} \rho \mathrm{d}V
$$
则有
$$
\begin{aligned}
J_x & = \iiint_V (y^{2}+z^{2}) \rho(x,y,z) \mathrm{d}V \\
J_y & = \iiint_V (x^{2}+z^{2}) \rho(x,y,z) \mathrm{d}V \\
J_z & = \iiint_V (x^{2}+y^{2}) \rho(x,y,z) \mathrm{d}V \\
J_{xy} & = \iiint_V (z^{2}) \rho(x,y,z) \mathrm{d}V \\
J_{yz} & = \iiint_V (x^{2}) \rho(x,y,z) \mathrm{d}V \\
J_{zx} & = \iiint_V (y^{2}) \rho(x,y,z) \mathrm{d}V
\end{aligned}
$$
