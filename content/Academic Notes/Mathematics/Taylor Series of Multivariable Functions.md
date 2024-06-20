# 高阶偏导数
二元函数的二阶偏导数有四种场景
$$
\begin{aligned}
\dfrac{\partial}{\partial {x}} \left(\dfrac{\partial {z}}{\partial {x}}\right)  & = \dfrac{\partial^2 {z}}{\partial {x}^2} = f_{xx} (x, y)  \\
\dfrac{\partial}{\partial {y}} \left(\dfrac{\partial {z}}{\partial {x}}\right)  & = \dfrac{\partial^2 {z}}{\partial {x}^2}{y} = f_{xy} (x, y)  \\
\dfrac{\partial}{\partial {x}} \left(\dfrac{\partial {z}}{\partial {y}}\right)  & = \dfrac{\partial^2 {z}}{\partial {y}^2}{x} = f_{yx} (x, y)  \\
\dfrac{\partial}{\partial {y}} \left(\dfrac{\partial {z}}{\partial {y}}\right)  & = \dfrac{\partial^2 {z}}{\partial {y}^2} = f_{yy} (x, y)
\end{aligned}
$$
类似地也可定义三阶偏导数如$\dfrac{\partial^3 z}{\partial x^2 \partial y} =\displaystyle \dfrac{\partial}{\partial {y}} \left(\dfrac{\partial^2 {z}}{\partial {x}^2}\right)$
> [!Tip]
> 注意，一般来说$\displaystyle \dfrac{\partial {z}}{\partial {x}}{y} \neq \dfrac{\partial {z}}{\partial {y}}{x}$，但是若$f_{xy}(x, y), f_{yx}(x, y)$都在点$(x_0, y_0)$连续，则有$f_{xy}(x_0, y_0) = f_{yx}(x_0, y_0)$，这个结论对$n$元函数的混合偏导数也成立

在本节中，若无特殊说明，都认为分析的函数无数阶连续可导，从而混合偏导数和求导顺序无关
# 中值定理
> [!Note]
> 若区域$D$上任意两点的连线都含于$D$，则称$D$为*凸区域*

设二元函数$f$在凸开域$D \subset \mathbb{R}^2$上可微，则对任意两点$P(a, b), Q(a +h, b+ k) \in D$，则存在实数$\theta \in (0, 1)$使得
$$
f(a + h, b+ k) = f(a, b) + f_x(a + \theta h, b + \theta k)h + f_y(a + \theta h, b + \theta k)k
$$
## 一般形式的推广
设凸域$D \subset \mathbb{R}^n$且$f:D\to \mathbb{R}$[[Differential of Multivariable Functions#全微分|可微]]，则任给$a, b \in D$存在$\xi \in D$使得
$$
f(b) - f(a) = Jf(\xi)\cdot (b - a)
$$
其中$\xi = a + \theta(b - a), \;\theta\in(0, 1)$，即$\xi$位于连接$a,b$的直线段上，而关于$Jf(\xi)$见[[Differential of Mappings#Jacobian矩阵|Jacobian矩阵]]
> [!Tip] 
> 这说明了**如果一个多元函数可微，则它可以用线性函数逼近**，利用这一点我
们可以做近似计算

此中值定理**对向量值函数不成立**
# Taylor定理
## 记号约定
设$\alpha_i \in \mathbb{R}^+ \;(1 \le i \le n)$，记$\boldsymbol \alpha = (\alpha_1, \ldots, \alpha_n)^t$称为*多重指标*，记
$$
\left|{\boldsymbol \alpha}\right| = \sum_{i = 1}^n \alpha_i, \; \boldsymbol \alpha! = \prod_{i = 1}^n \alpha_i!
$$
如果$\boldsymbol x = (x_1\ldots, x_n)^t \in \mathbb{R}^n$，则记
$$
x^{\boldsymbol {\alpha}} = x_1^{\alpha_1}\dots x_n^{\alpha_n}
$$
和
$$
D^{\boldsymbol \alpha} f(\boldsymbol x^0) = \dfrac{\partial^{\left|{\boldsymbol \alpha}\right|}f}{\partial_{x_1}^{\alpha_1}\cdots \partial_{x_n}^{\alpha_n}} (\boldsymbol x^0)
$$
## 二元情况
若函数$f$在点$P_0(x_0, y_0)$的某邻域$U(P_0)$上有直到$n + 1$阶的连续偏导数，则对$U(P_0)$上的任一点$(x_0 + h, y_0 + k)$都存在相应的$\theta \in (0, 1)$，使得
$$
\begin{aligned}
f(x_0 + h, y_0 + k) &= f(x_0, y_0) + \left(h \dfrac{\partial}{\partial {x}} + k \dfrac{\partial}{\partial {y}}\right)f(x_0, y_0) \\
&+ \dfrac{1}{2!} \left(h \dfrac{\partial}{\partial {x}} + k \dfrac{\partial}{\partial {y}}\right)^2 f(x_0, y_0)  + \cdots  \\
&+ \dfrac{1}{n!}\left(h \dfrac{\partial}{\partial {x}} + k \dfrac{\partial}{\partial {y}}\right)^n f(x_0, y_0)  \\
&+\dfrac{1}{(n+1)!} \left(h\dfrac{\partial}{\partial {x}} + k\dfrac{\partial}{\partial {y}}\right)^{n + 1} f(x_0 + \theta h, y_0 + \theta k)
\end{aligned}
$$
其中
$$
\left(h \dfrac{\partial}{\partial {x}} + k \dfrac{\partial}{\partial {y}}\right)^m f(x_0, y_0) = \sum_{i = 0}^m \mathrm{C}_m^i \dfrac{\partial^m}{\partial x^i \partial y^{m - i}} f(x_0, y_0) h^i k^{m - i}
$$

## 多元情况
设凸域$D\subset \mathbb{R}^n$，$f \in C^{m+1}(D),\; \boldsymbol a = (a_1,\ldots, a_n)^t \in D$. 则任给$\boldsymbol x \in D$存在$\theta \in (0,1)$使得
$$
f(\boldsymbol x) = \sum_{k = 0}^m \sum_{\left|{\boldsymbol \alpha}\right| = k} \dfrac{D^{\boldsymbol \alpha}f(\boldsymbol a)}{\boldsymbol \alpha !}\cdot(\boldsymbol x - \boldsymbol a)^{\boldsymbol \alpha} + \sum_{\left|{\boldsymbol \alpha}\right|= m + 1}\dfrac{D^{\boldsymbol \alpha}f(\boldsymbol a + \theta(\boldsymbol x - \boldsymbol a))}{\boldsymbol \alpha!} \cdot (\boldsymbol x - \boldsymbol a)^{\boldsymbol \alpha}
$$


