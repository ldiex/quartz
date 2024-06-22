# Fourier 变换基础
见[[Fourier Transformation|Fourier变换]]和[[Fourier Transformation in Optics|光学中的Fourier变换]]
# 衍射系统和屏函数
凡是能使波前复振幅发生改变的物，统称为衍射屏
![[光学-Fourier衍射系统.png#invert_B]]
定义*屏函数*
$$
\tilde t (x, y) = \dfrac{\widetilde U_2(x,y)}{\widetilde U_1(x, y)}
$$
有接收平面上的振幅分布
$$
\begin{gathered}
\widetilde{U}(x',y') =\frac{-i}\lambda\iint_{(\Sigma_0)}\widetilde{t}(x,y)\cdot\widetilde{U}_1(x,y)\frac{e^{ikr}}rdxdy \\
\neq\frac{-i}\lambda\iint_{(\Sigma_0)}\widetilde{U}_1(x,y)\frac{e^{ikr}}rdxdy 
\end{gathered}
$$
由于衍射屏函数的作用，改变了波前，从而改变了后场的分布，于是发生的衍射
## 屏函数的分类
振幅型：$\tilde t (x,y) = t(x, y)$，特别地对孔或者遮光屏而言
$$
t(x,y) = \begin{cases}
1 & \text{透光部分} \\
0 & \text{遮光部分}
\end{cases}
$$
位相型：$\tilde t(x,y) = e^{\mathrm{i}\varphi(x, y)}$
## 相因子判断法
通过相位的表达式$e^{\mathrm{i}\varphi(x,y)}$，判断一束波的类型
### 平面波
为常数
### 发散球面波
$$
\exp \left( {\mathrm{i}k\dfrac{x^2+y^2}{2z}} \right) 
$$
### 汇聚球面波
$$
\exp \left(-\mathrm{i}k \dfrac{x^2+y^2}{2z}\right)
$$
## 求解屏函数
![[光学-屏函数的求解.png#invert_B]]
考虑到[[Imagery#焦距公式|透镜的磨镜者公式]]，有
$$
\begin{aligned}
\varphi_L(x,y)& =-\frac{2\pi}\lambda\frac{n-1}2\Bigg(\frac1{r_1}-\frac1{r_2}\Bigg)\Bigg(x^2+y^2\Bigg)  \\
&=-k\frac{x^2+y^2}{2F} 
\end{aligned}
$$
其中
$$
F=\frac1{(n-1){\left(\dfrac1{r_1}-\dfrac1{r_2}\right)}}
$$
这是*透镜屏函数*

对于正入射平面波$\widetilde U_1(x,y) = A_1 = \text{const}$
有
$$
\tilde{U}_2(x,y)=\tilde{U}_1(x,y)\tilde{t}_L(x,y)=A_1e^{-ik\frac{x^2+y^2}{2F}}
$$
这是会聚在透镜后距离$F$处的球面波，和几何光学一致
# 正弦光栅
## 空间频率
某一面内光场随空间位置的周期性变化
$$
\tilde{U}(x,y)=Ae^{ik\sin\theta x}=Ae^{iq_xx}
$$
有
- 时间周期$T\iff$空间周期$d$
- 时间频率$\nu = \dfrac{1}{T}\iff$空间频率$f = \dfrac{1}{d}$
- 时间圆频率$\omega = 2\pi \nu\iff$ 空间圆频率$q=2\pi f$
### 二维的情况
![[光学-空间频率2.png#invert_B]]
## 正弦光栅定义
就是透过率是空间的正弦函数的光栅
![[光学-正弦光栅的屏函数.png#invert_B]]
$$
\tilde{t}\left(x,y\right)=t_0+t_1\cos\left(q_xx+q_yy+\varphi_0\right)
$$
## 正弦光栅的衍射图样
考虑平行光入射$\widetilde U_1 A_1$
$$
\begin{aligned}
\widetilde{U}_2(x,y)& =\tilde{U}_1(x,y)\tilde{t}(x,y)  \\
&=A_1[t_0+t_1\cos(2\pi fx+\varphi_0)] \\
&\begin{aligned}&=A_1t_0+A_1t_1\frac{e^{i(2\pi fx+\varphi_0)}+e^{-i(2\pi fx+\varphi_0)}}2\\&=\tilde{U}_0(x,y)+\tilde{U}_{+1}(x,y)+\tilde{U}_{-1}(x,y)\end{aligned}
\end{aligned}
$$
由相因子判断出射光为三个不同方向的平面波，其中$\sin\theta_{\pm1} = \pm f\lambda$
![[光学-正弦光栅的衍射图样.png#invert_B]]
## 任意光栅的屏函数
利用[[Fourier Series|Fourier展开]]把任意光栅的屏函数展开为正弦光栅的屏函数的叠加
$$
\begin{aligned}\widetilde{t}\left(x\right)&=\sum_{n=-\infty}^\infty\widetilde{t}_ne^{i2\pi nfx}\\ \\
\text{where}\quad\widetilde{t}_n&=\frac1d\int_{-d/2}^{d/2}\widetilde{t}\left(x\right)e^{-i2\pi nfx}dx\end{aligned}
$$
### 例子：黑白光栅
设光栅常数为$d$，缝宽为$a$
$$
\begin{gathered}
t(x)=\begin{cases}1,&\left|x\right|<a/2\\0,&\left|x\right|>a/2\end{cases} \\
t_0=\frac{1}{d}\int\limits_{-a/2}^{a/2}dx=\frac{a}{d} \\
\tilde{t}_n=\frac{1}{d}\int_{-a/2}^{a/2}e^{-i2\pi nfx}dx=\frac{a}{d}\frac{\sin\pi f_na}{\pi f_na} \\
=\frac ad\frac{\sin n\pi fa}{n\pi fa}=\frac ad\frac{\sin(n\pi a/d)}{n\pi a/d} 
\end{gathered}
$$
对于正入射平行光$\widetilde U_1(x) = A_1$
$$
\begin{aligned}
\widetilde{U}_2(x)& =\tilde{U}_1(x)\tilde{t}\left(x\right)=A_1\tilde{t}\left(x\right)  \\
&=A_1t_0+A_1\sum_{n\neq0}\widetilde{t}_ne^{i2\pi nfx}
\end{aligned}
$$
在$n$级平面波衍射方向
$$
\begin{aligned}&\sin\theta_n=nf\lambda=\frac{n\lambda}d\\&I_n\propto\left|\tilde{t}_n\right|^2=\left(\frac ad\right)^2\boxed{\left(\frac{\sin a_n}{a_n}\right)^2}\\&a_n=\pi a\sin\theta_n/\lambda\end{aligned}
$$

