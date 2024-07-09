# 隐函数
## 定义
设$E \subset \mathbb{R}^2$,函数$F:E\to \mathbb{R}$, 对于方程
$$
F(x,y) = 0
$$
如果存在集合$I,J\in \mathbb{R}$使得对任意的$x \in I$, 有唯一确定的$y\in J$满足$(x,y) \in E$和上述方程，则该方程确定了一个$I\to J$的*隐函数*.

例如方程
$$
xy + y -1 = 0
$$
确定了一个定义在$(-\infty,-1)\cup(-1,+\infty)$的隐函数$y = f(x)$，且可以写成*显函数*的形式
$$
y = \dfrac{1}{1+x}
$$
## 隐函数存在唯一性定理
若函数$F(x,y)$满足以下条件：
1. $F$在以$P_0(x_0,y_0)$为内点的某一区域$D\subset \mathbb{R}^2$上连续
2. $F(x_0, y_0)=0$ （通常称为初始条件）
3. $F$在$D$上存在连续的偏导数$F_y(x,y)$
4. $F_y(x_0, y_0) \neq 0$
则
1. 存在点$P_0$的某个邻域$U(P_0)\subset D$，在$U(P_0)$上$F(x,y) = 0$唯一确定了一个定义在某区间$(x_0 - \alpha, x_0 + \alpha)$上的隐函数$y = f(x)$，使得当$x \in (x_0 - \alpha, x_0 + \alpha)$时，$(x,f(x)) \in U(P_0)$且$F(x, f(x)) \equiv 0, f(x_0) = y_0$
2. $f(x)$在$(x_0 -\alpha, x_0+\alpha)$上连续

## 隐函数可微性定理
设$F(x,y)$**满足隐函数存在唯一性定理**，且在$D$上还存在连续的偏导数$F_x(x,y)$, 则由方程$F(x,y) = 0$确定的隐函数$y = f(x)$在其定义域$(x_0 -\alpha, x_0 +\alpha)$上有连续导函数，且
$$
f'(x) = - \dfrac{F_x(x, y)}{F_y(x, y)}
$$
### 高阶导数
关键是要注意到这里$y$也是$x$的函数
$$
\begin{gather}
F(x,y) = 0  \\
\dfrac{\partial {F}}{\partial {x}} \dfrac{\mathrm{d} {x}}{\mathrm{d} {x}} + \dfrac{\partial {F}}{\partial {y}} \dfrac{\mathrm{d} {y}}{\mathrm{d} {x}} = 0  \\
\dfrac{\partial^2 {F}}{\partial {x}^2} \dfrac{\mathrm{d} {x}}{\mathrm{d} {x}} + \dfrac{\partial {F}}{\partial {x}}{y} \dfrac{\mathrm{d} {y}}{\mathrm{d} {x}} + \left( \dfrac{\partial {F}}{\partial {y}}{x} \dfrac{\mathrm{d} {x}}{\mathrm{d} {x}} + \dfrac{\partial^2 {F}}{\partial {y}^2} \dfrac{\mathrm{d} {y}}{\mathrm{d} {x}} \right) \dfrac{\mathrm{d} {y}}{\mathrm{d} {x}} + \dfrac{\partial {F}}{\partial {y}} \frac{ \mathrm{d}^{2} y }{ \mathrm{d} x^{2} } = 0 \\
\implies y'' = \dfrac{2F_xF_yF_{xy}-F_y^2F_{xx}-F_x^2F_{yy}}{F_y^3} 
\end{gather}
$$
## 隐函数极值问题
1. 求$y'$为$0$的点，即方程组$\displaystyle \begin{cases}F(x,y) = 0 \\ F_x(x,y) = 0\end{cases}$的解$A(x,y)$, 注意需满足$F_y(x,y) \neq 0$
2. 对于每一个$A$, 计算$y'' |_A = - \dfrac{F_{xx}}{F_y} \bigg\vert_A$，并由此判断是极大值还是极小值
# 隐函数组和隐映射
如由这样的方程组
$$
\begin{cases}
F(x, y, u, v) = 0 \\
G(x, y, u, v) = 0
\end{cases}
$$
所确定的*隐函数组*
$$
\begin{cases}
u = f(x, y) \\
v = g(x, y)
\end{cases} \quad (x, y) \in D,\; (u,v) \in W
$$
本质上可以看成由一个映射方程
$$
f(x, y) = (f_1(x, y),f_2(x, y))=0\quad x = (x_1, x_2),\; y=(y_1,y_2)
$$

确定的*隐映射*
$$
y = g(x), \quad x\in D
$$
## 隐映射定理
设$W$为$\mathbb{R}^{n + m}$中的[[Planar Point Set#开集|开集]]，$W$中的点用$(x,y)$来表示，其中$x = (x_1, \ldots, x_n),\; y = (y_1, \ldots, y_m)$. $f:W\to \mathbb{R}^m$为$C^k$映射:
$$
f(x, y) = (f_1(x, y), f_2(x,y), \ldots,f_m(x,y))
$$
设$(x^0, y^0)\in W, f(x^0, y^0)=0$且$\det Jf_y(x^0, y^0)\neq0$，其中
$$
Jf_y(x, y) = \left( \dfrac{\partial {f_i}}{\partial {y_j}}(x,y) \right)_{m \times m}
$$
则存在$x^0$的开邻域$V \subset \mathbb{R}^n$以及唯一的$C^k$映射$g:V\to \mathbb{R}^m$使得
1. $y^0 = g(x^0), f(x,g(x)) = 0, \forall x \in V$
2. $Jg(x) = -\left[ Jf_y(x,g(x)) \right]^{-1}Jf_x(x, g(x))$
特别地，当$n = m = 2$时，利用[[Adjugate Matrix|伴随矩阵]]可以直接解得
$$
\begin{aligned} \\
(y_1, y_2)  & = g(x_1,x_2) \\
Jg = -(Jf_y)^{-1} Jf_x &= -\dfrac{1}{\det(Jf_y)} (Jf_y)^* Jf_x\\
\implies\begin{pmatrix}
 \displaystyle\dfrac{\partial {y_1}}{\partial {x_1}} &  \displaystyle\dfrac{\partial {y_1}}{\partial {x_2}} \\
 \displaystyle\dfrac{\partial {y_2}}{\partial {x_1}} &  \displaystyle\dfrac{\partial {y_2}}{\partial {x_2}}
\end{pmatrix} &= - \begin{vmatrix}
 \displaystyle\dfrac{\partial {f_1}}{\partial {y_1}} &  \displaystyle\dfrac{\partial {f_1}}{\partial {y_2}} \\
 \displaystyle\dfrac{\partial {f_2}}{\partial {y_1}} &  \displaystyle\dfrac{\partial {f_2}}{\partial {y_2}}
\end{vmatrix}^{-1} 
\begin{pmatrix}
 \displaystyle\dfrac{\partial {f_2}}{\partial {y_2}} & - \displaystyle\dfrac{\partial {f_1}}{\partial {y_2}} \\
-  \displaystyle\dfrac{\partial {f_2}}{\partial {y_1}} &  \displaystyle\dfrac{\partial {f_1}}{\partial {y_1}}
\end{pmatrix} \begin{pmatrix}
 \displaystyle\dfrac{\partial {f_1}}{\partial {x_1}} &  \displaystyle\dfrac{\partial {f_1}}{\partial {x_2}} \\
 \displaystyle\dfrac{\partial {f_2}}{\partial {x_1}} &  \displaystyle\dfrac{\partial {f_2}}{\partial {x_2}}
\end{pmatrix}
\end{aligned}
$$
> [!Note] 符号说明
>若需要明确指出$f;x,y$的每一个分量的具体的符号，也可以把上面的$Jf_x,Jf_y$写成$\dfrac{D(f_1, \ldots, f_m)}{D(x_1,\ldots, x_n)},\dfrac{D(f_1,\ldots,f_m)}{D(y_1,\ldots,y_m)}$
> 并定义$\dfrac{\partial(f_1, \ldots, f_m)}{\partial(x_1,\ldots, x_m)}= \left|{\dfrac{D(f_1, \ldots, f_m)}{D(x_1,\ldots, x_m)}}\right|,\; \dfrac{\partial(f_1,\ldots,f_m)}{\partial(y_1,\ldots,y_m)} = \left|{\dfrac{D(f_1,\ldots,f_m)}{D(y_1,\ldots,y_m)}}\right|$
> 注意在需要求[[Determinant|行列式]]的时候上面得取$m = n$，也就是Jacobian矩阵应当为一方阵

# 逆映射和变量代换
若上面的确定的隐映射
$$
y = g(x)
$$
是[[Injective, Surjective and Bijective#Bijective (One-to-One Correspondence)|双射]]，那么就有*逆映射*
$$
x = g^{-1}(y)
$$
它存在当且仅当（*隐映射定理*）
$$
\det Jy_x = \left|{\dfrac{D(y_1,\ldots,y_m)}{D(x_1,\ldots,x_m)}}\right| \neq0
$$
特别地，我们有
$$
\det Jy_x \cdot \det Jx_y  = \left|{\dfrac{D(y_1,\ldots,y_m)}{D(x_1,\ldots,x_m)}}\right| \left|{\dfrac{D(x_1,\ldots,x_m)}{D(y_1,\ldots,y_m)}}\right| = 1
$$
这个工具可以用于分析变量代换，如直角坐标和球坐标之间的变换
$$
\begin{cases}
x = r\sin\varphi\cos\theta \\
y = r\sin\varphi\sin\theta \\
z = r\cos\theta
\end{cases}
$$
由于
$$
\begin{aligned}\frac{\partial\left(x,y,z\right)}{\partial\left(r,\varphi,\theta\right)}&=\begin{vmatrix}\sin\varphi\cos\theta&r\cos\varphi\cos\theta&-r\sin\varphi\sin\theta\\\sin\varphi\sin\theta&r\cos\varphi\sin\theta&r\sin\varphi\cos\theta\\\cos\varphi&-r\sin\varphi&0\end{vmatrix}\\&=r^{2}\sin\varphi,\end{aligned}
$$
所以在$r^2\sin\varphi\neq0$即除去$z$轴上的一切点，都可以给出$r,\varphi,\theta$为$x,y,z$的函数

如果我们要求（比如说需要在一个关于$u=u(x,y,z)$微分方程中变换变量为$r,\varphi,\theta$）给出$u_r,u_\varphi,u_\theta$，则由链式法则
$$
\begin{aligned}
\begin{pmatrix}u_x\\u_y\\u_z\end{pmatrix}& \left.=\left(\begin{array}{ccc}{{r_{x}}}&{{\theta_{x}}}&{{\varphi_{x}}}\\{{r_{y}}}&{{\theta_{y}}}&{{\varphi_{y}}}\\{{r_{z}}}&{{\theta_{z}}}&{{\varphi_{z}}}\end{array}\right.\right)\left(\begin{array}{c}{{u_{r}}}\\{{u_{\theta}}}\\{{u_{\varphi}}}\end{array}\right)=\left(\begin{array}{ccc}{{x_{r}}}&{{y_{r}}}&{{z_{r}}}\\{{x_{\theta}}}&{{y_{\theta}}}&{{z_{\theta}}}\\{{x_{\varphi}}}&{{y_{\varphi}}}&{{z_{\varphi}}}\end{array}\right)^{-1}\left(\begin{array}{c}{{u_{r}}}\\{{u_{\theta}}}\\{{u_{\varphi}}}\end{array}\right)  \\
&\left.=\frac{1}{J}\left(\begin{array}{cccc}r^{2}\sin^{2}\theta\cos\varphi&r^{2}\sin^{2}\theta\sin\varphi&r^{2}\sin\theta\cos\theta\\r\sin\theta\cos\theta\cos\varphi&r\sin\theta\cos\theta\sin\varphi&-r\sin^{2}\theta\\-r\sin\varphi&r\cos\varphi&0\end{array}\right.\right)\left(\begin{array}{c}u_{r}\\u_{\theta}\\u_{\varphi}\end{array}\right).
\end{aligned}
$$
其中
$$
J = \dfrac{\partial(x,y,z)}{\partial(r,\varphi,\theta)} =r^2\sin \varphi
$$
这里用到了
$$
 \left.\left(\begin{array}{ccc}{{r_{x}}}&{{\theta_{x}}}&{{\varphi_{x}}}\\{{r_{y}}}&{{\theta_{y}}}&{{\varphi_{y}}}\\{{r_{z}}}&{{\theta_{z}}}&{{\varphi_{z}}}\end{array}\right.\right)\left(\begin{array}{ccc}{{x_{r}}}&{{y_{r}}}&{{z_{r}}}\\{{x_{\theta}}}&{{y_{\theta}}}&{{z_{\theta}}}\\{{x_{\varphi}}}&{{y_{\varphi}}}&{{z_{\varphi}}}\end{array}\right) = E
$$
因为有
$$
\begin{gather} 
\dfrac{\partial {r}}{\partial {x}} \dfrac{\partial {x}}{\partial {r}} + \dfrac{\partial {r}}{\partial {y}}\dfrac{\partial {y}}{\partial {r}}+ \dfrac{\partial {r}}{\partial {z}}\dfrac{\partial {z}}{\partial {r}} = \dfrac{\partial {r}}{\partial {r}} = 1 \\
\cdots
\end{gather}

$$
对矩阵积的对角线元素成立，和
$$
\begin{gather} \\
\dfrac{\partial {r}}{\partial {x}} \dfrac{\partial {x}}{\partial {\theta}} + \dfrac{\partial {r}}{\partial {y}}\dfrac{\partial {y}}{\partial {\theta}}+ \dfrac{\partial {r}}{\partial {z}}\dfrac{\partial {z}}{\partial {\theta}} = \dfrac{\partial {r}}{\partial {\theta}} = 0 \\
\cdots
\end{gather}
$$
对矩阵积的非对角线元素成立

# 几何应用
## 平面曲线的切线和法线
对于平面曲线
$$
F(x, y) = 0
$$
如果在$(x_0, y_0)$附近**满足隐函数定理的条件**，那么由
$$
f'(x) = -\dfrac{F_x}{F_y}
$$
得到**切线**
$$
F_x(x_0,y_0)(x-x_0) + F_y(x_0,y_0)(y - y_0) = 0
$$
和**法线**
$$
F_x(x_0,y_0)(x-x_0) - F_y(x_0,y_0)(y - y_0) = 0
$$
## 空间曲线的切线和法平面
对于由参数方程确定的空间曲线
$$
L:x=x(t),\;y=y(t),\;z =z(t), \quad\alpha \le t \le \beta
$$
由[[Analytical Geometry in Space#对称式方程|对称式方程]]，可以得到$L$在$(x_0, y_0,  z_0)$的切线方程为
$$
\dfrac{x-x_0}{x'(t_0)} = \dfrac{y - y_0}{y'(t_0)} = \dfrac{z - z_0}{z'(t_0)}
$$
而法平面$\Pi$满足
$$
(x'(t_0), y'(t_0),z'(t_0)) \cdot (x-x_0,y-y_0,z-z_0) = 0
$$
即
$$
x'(t_0)(x-x_0) + y'(t_0)(y - y_0) + z'(t_0)(z - z_0) = 0
$$
如果能够给出确定$L$的隐映射
$$
L:f(x,y,z) = (f_1(x,y,z),f_2(x,y,z)) = (0,0)
$$
且在$(x_0,y_0,z_0)$的某邻域满足隐映射定理
要求$\dfrac{\mathrm{d} {x}}{\mathrm{d} {z}}$和$\dfrac{\mathrm{d} {y}}{\mathrm{d} {z}}$，则可取自变量$X = (z)$，因变量$Y = (x,y)$，满足$(x,y) = g(z)$有
$$
\begin{aligned}
Jg(z)  & = -(Jf_Y(x,y))^{-1} (Jf_X(x,y))  \\
 & = -\begin{vmatrix}
\dfrac{\partial {f_1}}{\partial {x}}  & \dfrac{\partial {f_1}}{\partial {y}} \\
\dfrac{\partial {f_2}}{\partial {x}} & \dfrac{\partial {f_2}}{\partial {y}}
\end{vmatrix}^{-1}  \begin{pmatrix}
\dfrac{\partial {f_2}}{\partial {y}} & -\dfrac{\partial {f_1}}{\partial {y}} \\
-\dfrac{\partial {f_2}}{\partial {x}} & \dfrac{\partial {f_1}}{\partial {x}}
\end{pmatrix}
\begin{pmatrix}
\dfrac{\partial {f_1}}{\partial {z}}  \\ \dfrac{\partial {f_2}}{\partial {z}}
\end{pmatrix} \\
\end{aligned}
$$
即可算出
$$
\dfrac{\mathrm{d} {x}}{\mathrm{d} {z}} = \dfrac{\partial {x}}{\partial {z}} = \dfrac{\partial {g_1}}{\partial {z}};\quad \dfrac{\mathrm{d} {y}}{\mathrm{d} {z}} = \dfrac{\partial {y}}{\partial {z}}=\dfrac{\partial {g_2}}{\partial {z}}
$$

于是有**法平面方程**
$$
\dfrac{x-x_0}{\dfrac{\mathrm{d} {x}}{\mathrm{d} {z}}} + \dfrac{y -y _0}{\dfrac{\mathrm{d} {y}}{\mathrm{d} {z}}} + (z-z_0) = 0
$$
和**切线方程**
$$
\dfrac{x-x_0}{\dfrac{\mathrm{d} {x}}{\mathrm{d} {z}}} = \dfrac{y -y _0}{\dfrac{\mathrm{d} {y}}{\mathrm{d} {z}}} = \dfrac{z-z_0}{1}
$$
## 曲面的切平面与法线
设曲面方程
$$
F(x,y,z) = 0
$$
在$(x_0,y_0,z_0)$的某邻域满足隐映射定理
结合[[Differential of Multivariable Functions#可微性几何意义|可微性的几何意义]]，要先确定隐函数$z = f(x,y)$才能写出法向量
$$
\boldsymbol n = (f_x(x_0,y_0),\;f_y(x_0,y_0),\; -1)
$$
由于
$$
\begin{pmatrix}
\dfrac{\partial {z}}{\partial {x}} & \dfrac{\partial {z}}{\partial {y}}
\end{pmatrix} = -\begin{pmatrix}
\dfrac{\partial {F}}{\partial {z}}
\end{pmatrix}^{-1} \begin{pmatrix}
\dfrac{\partial {F}}{\partial {x}} & \dfrac{\partial {F}}{\partial {y}}
\end{pmatrix}
$$
故有**法线方程**
$$
\dfrac{x-x_0}{F_x} = \dfrac{y-y_0}{F_y} = \dfrac{z-z_0}{F_z}
$$
和**切平面方程**
$$
F_x(x-x_0) + F_y(y - y_0) + F_z(z-z_0) = 0
$$


