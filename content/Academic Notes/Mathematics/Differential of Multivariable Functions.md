# 多元函数的微分
## 偏导数
$f(x, y)$的*偏导数*$\displaystyle \dfrac{\partial {f}}{\partial {x}}, \dfrac{\partial {f}}{\partial {y}}$，或者记成$f_x, f_y$，被定义为
$$
\begin{gather}
\dfrac{\partial {f}}{\partial {x}} = \lim_{\Delta x \to 0} \left[f(x + \Delta x, y) - f(x, y)\right] \\
\dfrac{\partial {f}}{\partial {y}} = \lim_{\Delta y \to 0} \left[f(x, y + \Delta y) - f(x, y)\right]
\end{gather}
$$
## 全微分
设$D\subset \mathbb{R}^n$为[[Planar Point Set#开集|开集]]，有函数$f:D\to \mathbb{R}$. 设$\boldsymbol x^0=(x_1^0,\ldots, x_n^0)^t\in D$. 如果存在$\boldsymbol a \in \mathbb{R}^n$使得对于$x^0$附近的点$x$，有
$$
\Vert f(x) - \left[ f(x^0) +\boldsymbol a \cdot (\boldsymbol x - \boldsymbol x^0)\right]\Vert = o(\Vert \boldsymbol x - \boldsymbol x^0\Vert), \quad \boldsymbol x \to \boldsymbol x^0
$$
则称$f$在$\boldsymbol x^0$处*可微*

如果$f$是在某个定义域内可微，那么在这个定义域内有
$$
\mathrm{d} f = \sum_{i = 1}^n \dfrac{\partial {f}}{\partial {x_i}} \mathrm{d} x_i
$$
这样的形式称为*全微分*
> [!Hint] 可微的必要条件
> 可微$\implies$偏导数存在，对于一般情况参考[[Differential of Mappings|映射的微分]]

> [!Note] 可微的充分条件
>  偏导数都存在 且 $f_x, f_y, f_z$在点$(x_0, y_0, z_0)$**连续**$\implies$函数$f$在点$(x_0,y_0,z_0)$可微
>**但是反过来不一定成立**

注意，**函数在可微点一定连续**，但是函数的**连续点不一定存在偏导数**，且函数**存在偏导数的点也不一定连续**，因为连续性是全局的性质，而偏导数只能反映函数沿特点的性质，即
- 局部：偏导数
- 全局：全微分、连续性

## 二元函数的中值定理

设函数$f$在点$(x_0, y_0)$的某邻域内存在偏导数，若$(x, y)$属于该邻域，则存在$\xi = x_0 + \theta_1 (x - x_0)$, $\eta = y_0 + \theta_2 (y - y_0)$ ，$0 < \theta_1, \theta_2 < 1$使得
$$
f(x, y) = f(x_0 , y_0) + f_x(\xi, y_0) (x - x_0) + f_y(x_0, \eta)(y - y_0)
$$

# 可微性几何意义
一元函数可微，在几何上反映为存在不平行$y$轴的切线，类似地，对于二元函数来说，可微性则反映为曲面和其切平面之间的关系
> [!Note]
> 设$P$是曲面$S$上一点，$\Pi$是通过点$P$的一个平面，曲面$S$上的动点$Q$到顶点$P$和到平面$\Pi$的距离分别为$s$和$h$. 若当$Q$在$S$上以任何方式趋近于$P$时，恒有$\dfrac{h}{d}\to 0$，则称平面$\Pi$为曲面$S$在$P$处的*切平面*，$P$为*切点*
> - 求切平面常用$(\boldsymbol v - \boldsymbol v_0)\cdot \boldsymbol n = 0$
> - 求法线常用[[Analytical Geometry in Space#对称式方程|对称式方程]]，即$$\dfrac{x - x_0}{n_x}=\dfrac{y - y_0}{n_y}=\dfrac{z - z_0}{n_z}$$
> - 一种常用的取法向量的方法是取$n_x= f_x(x_0,y_0),n_y=f_y(x_0,y_0),n_z = -1$于是它对应的切平面就是$z - z_0 = f_x(x_0,y_0)(x-x_0) + f_y(x_0,y_0)(y - y_0)$

于是，$f(x, y)$上某点存在不平行于$z$轴的切平面的充要条件是$f$在$(x_0, y_0)$可微

# 全微分和近似计算
**例子** 求$1.08^{3.96}$的近似值
设$f(x, y) = x^y$，则有
$$
\begin{aligned}
1.08^{3.96} &= f(1 + 0.08, 4 - 0.04) \\
&\approx f(1, 4) + f_x(1, 4) \times 0.08 + f_y(1,4) \times (-0.04) \\
&=1.32
\end{aligned}
$$
**例子** 求使用$S = \dfrac{1}{2} ab \sin C$计算三角形面积时的绝对误差限和相对误差限
$$
\begin{aligned}
|\Delta S|  & \approx |\mathrm{d} S| = \left|{\dfrac{\partial {S}}{\partial {a}} \Delta a + \dfrac{\partial {S}}{\partial {b}} \Delta b + \dfrac{\partial {S}}{\partial {C}} \Delta C}\right| \\
 & \le \left|{\dfrac{\partial {S}}{\partial {a}}}\right| |\Delta a| + \left|{\dfrac{\partial {S}}{\partial {b}}}\right| |\Delta b| + \left|{\dfrac{\partial {S}}{\partial {C}}}\right| |\Delta C| \\
 & = \dfrac{1}{2} \left|{b \sin C}\right| |\Delta a| + \dfrac{1}{2} \left|{a \sin C}\right| |\Delta b| + \dfrac{1}{2} \left|{ab \cos C}\right| |\Delta C|
\end{aligned}
$$
相对误差限为$\left|{\dfrac{\Delta S}{S}}\right|$
# 复合函数的微分
## 链式法则
若函数$x = \phi (s,t), y = \psi (s,t)$在点$(s, t) \in D$可微，$z = f(x, y)$在点$(x, y)$可微，则复合函数
$$
z = f(\phi(s, t), \psi(s, t))
$$
在点$(s, t)$可微，且它关于$s, t$的偏导数分别为
$$
\begin{aligned}
\dfrac{\partial {z}}{\partial {s}} \bigg\vert_{(s, t)} = \dfrac{\partial {z}}{\partial {x}} \bigg\vert_{(x, y)} \dfrac{\partial {x}}{\partial {s}} \bigg\vert_{(s, t)} + \dfrac{\partial {z}}{\partial {y}} \bigg\vert_{(x, y)} \dfrac{\partial {y}}{\partial {s}} \bigg\vert_{(s, t)}  \\
\dfrac{\partial {z}}{\partial {t}} \bigg\vert_{(s, t)} = \dfrac{\partial {z}}{\partial {x}} \bigg\vert_{(x, y)} \dfrac{\partial {x}}{\partial {t}} \bigg\vert_{(s, t)} + \dfrac{\partial {z}}{\partial {y}} \bigg\vert_{(x, y)} \dfrac{\partial {y}}{\partial {t}} \bigg\vert_{(s, t)} 
\end{aligned}
$$
并可推广到$n$元函数的场景；并且，由此亦可推导出$f$的全微分
> [!Tip] 多元函数的全微分形式不变性
> $$
> \mathrm{d} z= \dfrac{\partial {z}}{\partial {x}} \mathrm{d} x + \dfrac{\partial {z}}{\partial {y}} \mathrm{d} y = \dfrac{\partial {z}}{\partial {s}} \mathrm{d} s + \dfrac{\partial {z}}{\partial {t}} \mathrm{d} t
> $$
> 只要$(x, y)$或者$(s, t)$能够完全表达$z$

# 方向导数和梯度
## 方向导数
设三元函数$f$在点$P_0(x_0, y_0, z_0)$的某邻域$U(P_0) \in \mathbb R^3$有定义，$\boldsymbol l$是从$P_0$出发的射线，$P(x, y, z)$是$\boldsymbol l$上含于$U(P_0)$的任一点，以$\rho$表示$P,P_0$之间的距离. 若极限
$$
\lim_{ \rho \to 0^+} \dfrac{f(P) - f(P_0)}{\rho}   
$$
存在，则称此极限为$f$在点$P_0$沿方向$\boldsymbol l$的*方向导数*，记作
$$
\dfrac{\partial {f}}{\partial {\boldsymbol l}} \bigg\vert_{P_0}, \; f_l (P_0) , \; f_l(x_0, y_0, z_0)
$$
若函数$f$在点$P_0(x_0, y_0, z_0)$可微，则$f$在点$P_0$沿任一方向$\boldsymbol l$的方向导数恰为
$$
f_l(P_0) = f_x(P_0) \cos \alpha + f_y(P_0) \cos \beta + f_z(P_0) \cos \gamma
$$
其中$\cos \alpha, \cos \beta, \cos \gamma$为方向$\boldsymbol l$的*方向余弦*
$$
\cos \alpha = \dfrac{l_x}{|\boldsymbol l|}, \; \cos \beta = \dfrac{l_y}{|\boldsymbol l|}, \; \cos \gamma = \dfrac{l_z}{|\boldsymbol l|}
$$
## 梯度
若$f(x, y, z)$在点$P_0(x_0, y_0, z_0)$存在对所有自变量的偏导数，则称向量$(f_x(P_0), f_y(P_0), f_z(P_0))$为函数$f$在点$P_0$的*梯度*，记作
$$
\nabla f = (f_x, f_y, f_z)
$$
由此，得到$f$在方向$\boldsymbol l$上的方向导数为
$$
f_l(P_0)  = \nabla f(P_0) \cdot \dfrac{\boldsymbol l}{|\boldsymbol l|}
$$

