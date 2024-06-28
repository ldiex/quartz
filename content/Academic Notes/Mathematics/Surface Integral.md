# 第一型曲面积分
设$S$是空间中可求面积的曲面，$f(x,y,z)$是定义在$S$上的函数，对曲面$S$作分割$T$，它把$S$分割成$S_i\;(i=1, \ldots ,n)$，以$\Delta S_i$记小曲面块$S_i$的面积，$d_{S_i}$记$S_i$的直径，分割$T$的细度$\Vert T \Vert = \max{d_{S_{i}}}$，在$S_i$上任取点$(\xi_i,\eta_i,\zeta_i)$，若极限
$$
\lim_{ \Vert T \Vert \to 0  } \sum_{i = 1}^n f(\xi_i,\eta_i,\zeta_i) \Delta S_i
$$
存在且与取点的方式无关，则称此极限为$f(x,y,z)$在$S_i$上的第一型曲面积分，记作
$$
\iint_S f(x,y,z) \mathrm{d}S
$$
取合适的坐标系，利用曲面方程把$z$化成以$x,y$表达的函数，就可以把第一型曲面积分化成[[Multiple Integral#二重积分|二重积分]]

如果$S$由$z = z(x,y)$来表示，则利用[[Multiple Integral#曲面的面积|曲面面积的求法]]，有
$$
\iint_S f(x,y,z) \mathrm{d}S = \iint_D f(x,y,z(x,y)) \sqrt{ 1+z_x^{2}+z_y^{2} } \mathrm{d} x \mathrm{d}y
$$
更一般地，我们设$S$上的每一个点$\boldsymbol r$都可以通过两个参数来决定，即我们有$\boldsymbol r(s,t)$，其中$(s,t)$在 某个区域$D$内，那么
$$
\iint_S f \mathrm{d}S = \iint_D f(\boldsymbol r(s,t)) \left\Vert \frac{ \partial \boldsymbol r }{ \partial s } \times \frac{ \partial \boldsymbol r }{ \partial t } \right \Vert \mathrm{d}s \mathrm{d}t
$$
其中$\Vert\cdot \Vert$表示[[Euclidean Space|欧式空间]]中的[[Euclidean Space#长度和距离|长度]]
# 第二型曲面积分
## 曲面的侧
设连通曲面$S$上到处都有连续变动的切平面（或法线），$M$为曲面$S$上的一点，曲面在$M$处的法线有两个方向：当取定其中的一个方向为正方向时，另一个就是负方向。设$M_0$为$S$上任一点，$L$是$S$上任一经过点$M_0$，且不超出$S$边界的闭曲线。又设$M$为动点，它在$M_0$处与$M_0$有相同的法线方向，且有如下特性：当$M$从$M_0$出发沿$L$连续移动，这时作为曲面上的点$M$，它的法线方向也连续地变动。最后当$M$沿$L$回到$M_0$时，若这时$M$的法线方向仍然和$M_0$的法线方向一致，则说该曲面$S$时*双侧曲面*，若和$M_0$的法线方向相反，则说$S$是*单侧曲面*

单侧曲面的常见例子是*Möbius带*，而我们平时用$z = z(x,y)$表示的曲面基本都是双侧曲面，当以其法线正方向与$z$轴正向的夹角成锐角的一侧为正侧时，此时另一侧为负侧；当$S$为封闭曲面时，通常规定**曲面的外侧为正侧，内侧为负侧**

## 积分定义
定义了曲面的正侧和负侧后，我们就能给出法向量$\boldsymbol{\hat{n}}$的方向，那么我们对于向量值函数$\boldsymbol f(x,y,z)$就能类似地定义第二型曲面积分
$$
\iint_S\boldsymbol f\cdot \boldsymbol{\hat{n}} \mathrm{d}S = \iint_S f_x\hat{n}_x+f_y\hat{n}_y +  f_z\hat{n}_z \mathrm{d}S
$$
写出分量后即可转换位第一型曲面积分来计算

设积分曲面可由方程$F(x,y,z) = 0$来描述，则由[[Implicit Function#曲面的切平面与法线|隐函数定理]]，其上某点的法向量由隐函数$z = z(x,y)$确定
$$
\boldsymbol n = (z_x(x_0,y_0), z_y(x_0,y_0),-1) \text{ or } \boldsymbol n = —z_x(x_0,y_0), -z_y(x_0,y_0),1)
$$
根据不同的正负规定，可以得到
$$
\boldsymbol {\hat{n}} = \pm\left( \frac{z_x}{\sqrt{ 1+z_x^{2}+z_y^{2} }}, \frac{z_y}{\sqrt{ 1+z_x^{2}+z_y^{2} }}, - \frac{1}{\sqrt{ 1+z_x^{2}+z_y^{2} }} \right) 
$$
# 相关定理
散度定理 [[Gauss's Divergence Theorem]]
旋度定理 [[Stokes' Curl Theorem]]
