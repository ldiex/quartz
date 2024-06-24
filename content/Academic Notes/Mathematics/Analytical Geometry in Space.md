# 空间坐标系和空间向量
## 两点间距离
$$
\rho = \sqrt{(x_1 - x_2)^2 + (y_1 - y_2)^2 + (z_1 - z_2)^2}
$$
## 空间向量
### 方向余弦
设$P_0(x_0, y_0, z_0),\; P(x, y, z)$则有
$$
\cos \alpha = \dfrac{x - x_0}{\left|{\overrightarrow{P_0P}}\right|},\; \cos \beta = \dfrac{y - y_0}{\left|{\overrightarrow{P_0P}}\right|},\; \cos \gamma = \dfrac{z - z_0}{\left|{\overrightarrow{P_0P}}\right|}
$$
### 内积
$$
\vec a \cdot \vec b = a_1a_2 + b_1 b_2 + c_1 c_2
$$
### 外积
$$
\vec a \times \vec b = \left|{\begin{matrix}
\vec i & \vec j & \vec k \\
a_1 & b_1 & c_1 \\
a_2 & b_2 & c_2
\end{matrix}}\right|
$$
满足
$$
\left|{\vec a \times \vec b}\right| = \left|{\vec a}\right| \left|{\vec b}\right| \sin \langle\vec a , \vec b\rangle
$$
# 空间平面
## 平面方程
### 点法式方程
已知一平面$\Pi$通过已知点$M_0(x_0, y_0, z_0)$且垂直于非零向量$\vec n = (A, B, C)$，则$\Pi$的方程为
$$
A(x - x_0) + B(y - y_0) + C(z - z_0) = 0
$$
### 三点式方程
平面$\Pi$通过三个点$(x_1, y_1, z_1), (x_2, y_2, z_2), (x_3, y_3, z_3)$，则$\Pi$的方程为
$$
\left|{
\begin{matrix}
x - x_1 & y - y_1 & z - z_1 \\
x_2 - x_1 & y_2 - y_1 & z_2 - z_1 \\
x_3 - x_1 & y_3 - y_1 & z_3 - z_1
\end{matrix}}\right| = 0
$$
### 截距式方程
平面$\Pi$和三坐标轴的交点分别为$(a, 0, 0), (0, b, 0), (0, 0, c)$时，$\Pi$的方程为
$$
\dfrac{x}{a} + \dfrac{y}{b} + \dfrac{z}{c} = 1\; (a,b, c \neq 0)
$$
### 一般方程
即三元一次方程
$$
Ax + By + Cz + D = 0 \; (A^2 + B^2 + C^2 \neq 0)
$$
当$D = 0$时，平面通过原点
当$A = 0$时，平面平行于$x$轴
当$B = 0$时，平面平行于$y$轴
当$C = 0$时，平面平行于$z$轴
## 平面夹角
设平面$\Pi_1$的法向量为$\vec n_1 = (A_1, B_1, C_1)$，平面$\Pi_2$的法向量为$\vec n_2 = (A_2, B_2, C_2)$，则两平面夹角$\theta$的余弦为
$$
\cos \theta = \dfrac{\left|{\vec n_1 \cdot \vec n_2}\right|}{\left|{\vec n_1}\right| \left|{\vec n_2}\right|}
$$
特别地，$\Pi_1 \perp \Pi_2 \iff \vec n_1 \perp \vec n_2$且$\Pi_1 \parallel \Pi_2 \iff \vec n_1 \parallel \vec n_2$
# 空间直线
## 直线方程
### 一般式方程
直线可视为两平面交线，故其一般式方程
$$
\begin{cases}
A_1 x + B_1 y + C_1 z + D_1 = 0 \\ A_2 x + B_2 y + C_2 z + D_2 = 0
\end{cases}
$$
对于某一直线，**其一般式方程不唯一**
### 对称式方程
直线上一点$M_0(x_0, y_0, z_0)$和它的方向向量$\vec s = (m, n, p)$可确定该直线的方程
$$
\dfrac{x - x_0}{m} = \dfrac{y - y_0}{n} = \dfrac{z - z_0}{p}
$$
对称式方程也称为*点向式方程*
> [!Tip] 在空间的情况用对称式方程而不是用两个平面的点斜式方程联立
### 参数式方程
由*对称式方程*可直接得到
$$
\begin{cases}
x = x_0 + mt \\ y = y _0 + nt \\ z = z_0 + pt
\end{cases}
$$
## 线面间位置关系
### 两直线夹角
就是两直线的方向向量的夹角
$$
\cos \varphi = \dfrac{\left|{\vec s_1 \cdot \vec s_2}\right|}{\left|{\vec s_1}\right| \left|{\vec s_2}\right|}
$$
### 直线和平面的夹角
就是直线的方向向量和平面的法向量的夹角的余角
$$
\sin \varphi = \dfrac{\left|{\vec s \cdot \vec n}\right|}{\left|{\vec s}\right|\left|{\vec{n}}\right|}
$$
# 曲面
## 曲面方程
如果曲面$S$与方程$F(x, y, z) = 0$有下述关系：
1. 曲面$S$上的任意点的坐标都满足此方程
2. 不在曲面$S$上的点的坐标不满足次方程
则$F(x, y, z) = 0$称为曲面$S$的*方程*，曲面$S$称为方程$F(x, y, z) = 0$的*图形*
## 旋转曲面
一条平面曲线绕其平面上一条定直线旋转一周所形成的曲面叫做*旋转曲面*. 该定直线称为*旋转轴*

当旋转轴为$z$轴时，旋转曲面方程有如下形式
$$
f(\sqrt{x^2 + y^2}, z) = 0
$$
## 柱面
沿定曲线$C$移动的直线$l$形成的轨迹叫做*柱面*，其中$C$叫做*准线*，$l$叫做*母线*

方程$F(x, y) = 0$表示母线平行于$z$轴，准线在$xOy$面上的柱面
方程$F(y, z) = 0$表示母线平行于$x$轴，准线在$uOz$面上的柱面
方程$F(x, z) = 0$表示母线平行于$y$轴，准线在$xOz$面上的柱面
## 椭球面
$$
\dfrac{x^2}{a^2} + \dfrac{y^2}{b^2} + \dfrac{z^2}{c^2} = 1\; (a, b, c>0)
$$
# 空间曲线
## 方程
### 一般方程
空间曲线可视为两曲面的交线, 其一般方程为方程组
$$
\begin{cases}
F(x, y, z) = 0 \\ G(x, y, z) = 0
\end{cases}
$$
### 参数方程
$$
\begin{cases}
x =x (t) \\ y = y(t) \\  z = z(t)
\end{cases}
$$
## 空间曲线在坐标面上的投影
设一般方程为
$$
\begin{cases}
F(x, y, z) = 0 \\ G(x, y, z) = 0
\end{cases}
$$
消去$z$得到投影柱面$H(x, y) = 0$
则$C$在$xOy$面上的*投影曲线*$C'$为
$$
\begin{cases}
H(x, y) = 0\\ z = 0
\end{cases}
$$
消去$x$得$C$在$yOz$面上的投影曲线方程
$$
\begin{cases}
R(y, z) = 0 \\ x = 0
\end{cases}
$$
消去$y$得$C$在$xOz$面上的投影曲线方程
$$
\begin{cases}
T(x, z) = 0 \\ y = 0
\end{cases}
$$
# 曲面所围区域
## 确定空间区域在$xy$平面上的投影区域
1. 区域侧面是母线平行于$z$轴的柱面，则此时在$xy$平面上的投影方程和该柱面有相同的形式
2. 区域由一个特殊的封闭曲面（如椭球面）所围成，则此时只需要用平面$z = c$去截这个曲面，其中“最大”截痕的方程就是投影区域的边界方程
3. 区域由几个特殊曲面围成，则从方程中消去变量$z$通常就得到投影区域的边界方程
## 由曲面方程确定曲面的形状
截痕法：确定交线的投影曲线，即在方程中分别令$x = a, y = b, z = c$，看得到什么样的曲线