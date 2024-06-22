# 数项级数
[[数项级数技巧.pdf]]
[[MA-EX-1]]
[[MA-EX-2]]
积分判别法要求**减函数**
交错级数的绝对收敛和条件收敛
- 绝对收敛级数性质
	- 重排
	- 乘积：在一个二维表格中任意选取相加的路径（比如说斜着加）
# 函数项级数
[[MA-EX-3]]
## 函数项数列
一致收敛的定义条件、**Cauchy条件**（**常用于不知道极限的时候**）和其等价条件（先取$\sup$，再取极限）
## 函数项级数
一致收敛的定义条件、Cauchy条件和其等价条件（$f_n$换成$S_n$）

内闭一致收敛-更弱的条件（反例$f(x) = x^n$在$1$附近）

大M判别法 - **绝对值**放大为一个收敛的正项级数（只和$n$有关，和$x$无关）
或者也采用比较判别法，绝对值放大为另一个已知一致收敛的函数项级数

一致收敛$\implies$ 连续性（**可弱化为内闭一致收敛**）、极限微分积分可交换性、逐项求微分积分
# 幂级数
[[MA-EX-4]]
收敛半径的计算（类似根式判别法）（不要忘记取倒数）
也可以使用比式判别法来计算 $\displaystyle\lim_{n \to \infty} \dfrac{\left|{a_{n+1}}\right|}{\left|{a_n}\right|} = \rho \implies \lim_{n \to \infty} \sqrt[n]{ a_n } = \rho$
在$x = \pm R$时需要单独讨论

极限不存在，使用上极限$\dfrac{1}{R} = \limsup_{n \to \infty} \sqrt[n]{|a_n|}$

一致收敛性和和函数的连续性
逐项求导、求积

## 幂级数的运算
两个幂级数相乘
[[Power Series#和函数的计算|和函数的计算]]
- 直接逐项积分
- 下降阶乘幂分解后逐项积分
- 构造幂级数来计算某个数项级数的值

## 函数的幂级数展开
Taylor级数不一定等于原来的函数
- 判定标准：余项的极限为$0$
- 三个类型的余项

$e^x, \sin(x), \cos(x) : \mathbb{R}$
$\ln(1+x):x\in (-1,1]$
$$(1+x)^\alpha: x \in \color{red} \begin{cases}
(-1, 1), & \alpha \le -1 \\
(-1, 1], & -1 < \alpha < 0 \\
[-1, 1], & \alpha > 0
\end{cases}
$$
推广的[[Power Series#两个特殊情况|两个特殊情况]]，得到$\arctan x$和$\arcsin x$的幂级数表达式


# Fourier 级数
$a_0, a_n,b_n$的表达式
表达式中的$l$怎么取，积分区间怎么取
周期延拓
### 计算程序
1. 计算$a_0$
2. 计算$a_n,b_n$, 通常利用分部积分，可以利用[[Table Method for Integration by Parts | 表格积分法]]
3. 计算在 **端点** 和 **不连续点**上，级数收敛至哪个值

## 注意
- Fourier级数的第一项是$\dfrac{a_0}{2}$
- 由于周期性，端点的收敛值等于趋近于区间两侧的极限的平均值，两个端点的收敛值应当是一样的
- 积分上下界不一定是关于原点对称的，应该按照定义域来
- 不要随便写$=$号，除非级数一致收敛于$f$本身，应该写$\sim$

## 奇延拓和偶延拓
展开为正弦级数和余弦级数

## 收敛定理
分段光滑的条件
Dirichlet条件

## Bessel 不等式
$$
\dfrac{a_0^2}{2} + \sum_{n = 1}^\infty (a_n^2 + b_n^2) \le \dfrac{1}{\pi}\int_{-\pi}^\pi f^2(x) \mathrm{d} x
$$
具体见[[Bessel Inequality|Bessel不等式]]

# 点集拓扑
内点 外点 界点 聚点 孤立点
开集 闭集 开域 闭域 （余集$E^c$）

# 多元函数极限
[[MA-Ex-6]]
[[MA-Ex-7]]
[[MA-Ex-8]] 综合练习
> [!Note] 求多元函数极限的方法
> 1. 定义 (绝对值放缩)
> 2. Taylor 展开 (等价无穷小)
> 3. 趋于$(0, 0)$：极坐标换元$x = r\sin \theta; y = r \sin \theta$，利用有界性[[MA-Ex-8]],[[MA-Ex-10]]
> 4. 猜极限为$0$：夹逼


## 连续性
$$
\lim_{P \to P_0;P \in D} f(P) = f(P_[](MA-Ex-8.md)续[](MA-Ex-10.md)## **闭域**上连续函数的性质
有最大最小值
可以定义一致连续

# 多元函数微分
[[MA-Ex-11]]
## 全微分的定义
设$D\subset \mathbb{R}^n$为[[Planar Point Set#开集|开集]]，有函数$f:D\to \mathbb{R}$. 设$\boldsymbol x^0=(x_1^0,\ldots, x_n^0)^t\in D$. 如果存在$\boldsymbol a \in \mathbb{R}^n$使得对于$x^0$附近的点$x$，有
$$
\Vert f(x) - \left[ f(x^0) +\boldsymbol a \cdot (\boldsymbol x - \boldsymbol x^0)\right]\Vert = o(\Vert \boldsymbol x - \boldsymbol x^0\Vert), \quad \boldsymbol x \to \boldsymbol x^0
$$
则称$f$在$\boldsymbol x^0$处*可微*

证明可微需要找到这个$\boldsymbol a$，也就是那些$\displaystyle\dfrac{\partial {f}}{\partial {x_i}}$，然后利用放缩证明上述等式

## 可微性和偏导数存在以及连续性之间的关系
## 二元函数的两种中值定理
### 在平行于$x,y$的两个折线上运用两次一元中值定理
设函数$f$在点$(x_0, y_0)$的某邻域内存在偏导数，若$(x, y)$属于该邻域，则存在$\xi = x_0 + \theta_1 (x - x_0)$, $\eta = y_0 + \theta_2 (y - y_0)$ ，$0 < \theta_1, \theta_2 < 1$使得
$$
f(x, y) = f(x_0 , y_0) + f_x(\xi, y_0) (x - x_0) + f_y(x_0, \eta)(y - y_0)
$$
### 在两点连线上运用一次中值定理
设二元函数$f$在凸开域$D \subset \mathbb{R}^2$上可微，则对任意两点$P(a, b), Q(a +h, b+ k) \in D$，则存在实数$\theta \in (0, 1)$使得
$$
f(a + h, b+ k) = f(a, b) + f_x(a + \theta h, b + \theta k)h + f_y(a + \theta h, b + \theta k)k
$$

## 高阶偏导数
[[MA-Ex-9]]
# 多元Taylor级数

$$
f(\boldsymbol x) = \sum_{k = 0}^m \sum_{\left|{\boldsymbol \alpha}\right| = k} \dfrac{D^{\boldsymbol \alpha}f(\boldsymbol a)}{\boldsymbol \alpha !}\cdot(\boldsymbol x - \boldsymbol a)^{\boldsymbol \alpha} + \sum_{\left|{\boldsymbol \alpha}\right|= m + 1}\dfrac{D^{\boldsymbol \alpha}f(\boldsymbol a + \theta(\boldsymbol x - \boldsymbol a))}{\boldsymbol \alpha!} \cdot (\boldsymbol x - \boldsymbol a)^{\boldsymbol \alpha}
$$
# 空间解析几何
空间曲线 切线 法平面
空间曲面 切平面 法线

# 例题
## 数项级数
判断级数$\displaystyle \sum_{n = 1}^\infty \dfrac{\left( n+\dfrac{1}{n} \right)^n}{n^{n+1/n}}$的敛散性
因为
$$
\lim_{n \to \infty} a_n = \lim_{n\to \infty} \dfrac{n^n}{n^n} = 1 \neq 0
$$
故发散

证明$\displaystyle \sum_{n = 1}^\infty \dfrac{1}{n^2}$收敛
$$
\dfrac{1}{n^2} <\dfrac{1}{n(n - 1) }=\dfrac{1}{n-1}-\dfrac{1}{n}
$$

判断级数$\dfrac{1}{\sqrt{ 2 }-1}-\dfrac{1}{\sqrt{ 2 } + 1} + \dfrac{1}{\sqrt{3 }-1} -\dfrac{1}{\sqrt{ 3 }+1}+\dfrac{1}{\sqrt{ 4}-1}-\dfrac{1}{\sqrt{ 4 }+1}$的收敛性
**因为收敛级数可以任意加括号，不改变它的收敛性及和**，故假设这个级数收敛，则计算
$$
\dfrac{1}{\sqrt{ n }-1}-\dfrac{1}{\sqrt{ n } + 1} = \dfrac{2}{n - 1}
$$
这个级数显然是发散的，故原级数发散

$\sum \sin \dfrac{1}{n}$发散因为$\sin \dfrac{1}{n} \sim \dfrac{1}{n}$, $\sum \sin^2{\dfrac{1}{n}}$收敛因为$\sin^2{\dfrac{1}{n}}\sim \dfrac{1}{n^2}$

讨论$\sum nx^{n-1}$的敛散性直接用比式判别法，不用把它求出来

讨论$\sum \dfrac{x^n}{1+x^{2n}}$的敛散性要注意到$\sqrt[n]{ 1+x^{2n} } = \max\left\{ 1,x^2 \right\}$

出现了$\dfrac{1}{n}$和$\ln(n)$如$\sum \dfrac{1}{n(\ln n)^p},\sum \dfrac{1}{n(\ln n)(\ln\ln n)^p}$采用积分判别法

若数列$\left\{ a_n \right\}$单调减且极限为$0$，那么证明$x\in(0,2\pi)$时$\sum a_n\sin nx$和$\sum a_n\cos nx$都收敛
因为**恒等式**
$$
\dfrac{1}{2} + \sum_{k = 1}^n \cos kx = \dfrac{\sin \left( n+\dfrac{1}{2} \right)x }{2\sin \dfrac{x}{2}}
$$
所以级数$\sum \cos nx$的部分和数列有界，由[[Polynomial Series#Dirichlet 判别法|Dirichlet判别法]]得到$\sum a_n \cos nx$收敛，同理可证明$\sum a_n \sin nx$收敛 

## 函数项级数

$f_n = nxe^{-nx^2},x\in\mathbb{R}^+$不一致收敛，这是因为
$$
f'_n = ne^{-nx^2}-nx\cdot2nxe^{-nx^2} = ne^{-nx^2}(1-2nx^2)
$$
有
$$
\sup_x f_n(x) = f_n(\dfrac{1}{\sqrt{ 2n }}) = \sqrt{ \dfrac{n}{2} }e^{-1/2}
$$
因此
$$
\lim_{n \to \infty} \sup_x f_n(x) \neq 0
$$


$x^n$在$(-1,1)$上不一致收敛但是内闭一致收敛是因为
$$
R_n(x) = S_n(x) - S(x) = \dfrac{1-x^n}{1-x} -\dfrac{1}{1-x} = \dfrac{x^n}{x-1}
$$
有
$$
\sup_{x\in(-1,1)} \left|{R_n(x)}\right| \ge \left|{\dfrac{\left( \dfrac{n}{n+1}\right)^n }{\left( \dfrac{n}{n+1}\right)-1}}\right|= n\left( \dfrac{n}{n+1}\right)^n\to \infty \text{ as } n \to \infty
$$
而对任意$0<a<1$有
$$
\sup_{x\in[-a,a]}\left|{R_n(x)}\right|  = \dfrac{a^n}{1-a} \to 0 \text{ as } n \to \infty
$$
注意靠近$1$时$x^n$的图像

函数项级数$\sum \dfrac{(-1)^n(x+n)^n}{n^{n+1}}$一致收敛，是因为$\sum\dfrac{(-1)^n}{n^{n+1}}$是**一致收敛**的，且对每一个$x$ $\left( 1+\dfrac{x}{n} \right)^n$是**单调有界**的，故由[[Function Series#Abel 判别法|Abel判别法]]可得

同样理利用[[Function Series#Dirichlet 判别法|Dirichlet判别法]]可以得到$\sum a_n \cos nx$一致收敛，其中$a_n$单调趋于$0$

函数$\xi(x) = \sum_{n = 1}^\infty \dfrac{1}{n^x}$在$(1,+\infty)$上具有连续的各阶导函数，这是因为
$$
u_n(x) = \dfrac{1}{n^x} \implies u^{(k)}_n(x) = (-1)^k\dfrac{\ln^k n}{n^x}
$$
考虑闭区间$[a,b] \subset(1,\infty)$先利用[[Function Series#Werierstrass 判别法|大M判别法]]和估阶技巧
$$
u_n^{(k)}(x) \le \dfrac{\ln^k n}{n^a} \le \dfrac{(Cn^{b/k})^k}{n^a} = C^k \dfrac{1}{n^{a-b}}
$$
我们希望右边的级数收敛，也就是$a - b>1$，故可取$b = \dfrac{a-1}{2}$，这时就有$\sum u_n^{(k)}(x)$在$(1, +\infty)$上内闭一致收敛

## 幂级数
计算级数$\sum_{n = 1}^\infty \dfrac{x^n}{n^2}$的收敛域，令$a_n = \dfrac{1}{n^2}$(**别把$x$也带进去**)，有
$$
\rho= \lim_{n \to \infty} \sqrt[n]{ a_n } = \lim_{n \to \infty} \dfrac{1}{\sqrt[n]{n^2 }} = 1
$$
于是$R = \dfrac{1}{\rho} = 1$，**特别地在$x=\pm1$时原级数收敛**，故收敛域为$[-1,1]$

同理，对于$\sum_{n=1}^\infty \dfrac{x^n}{n}$而言，有
$$
\rho = \lim_{n \to \infty} \dfrac{\dfrac{1}{n+1}}{\dfrac{1}{n}} = 1\implies R = \dfrac{1}{\rho} =1
$$
而在$x = 1$时原级数发散，故收敛域为$[-1,1)$

再看级数
$$
1+\dfrac{x}{3}+\dfrac{x^2}{2^2} + \dfrac{x^3}{3^3}+\dfrac{x^4}{2^4} + \dfrac{x^5}{3^5} + \cdots
$$
极限
$$
\lim_{n\to \infty} \sqrt[n]{ a_n }
$$
显然是不存在的，但是考虑**上极限**
$$
\lim_{n \to \infty } \sup \sqrt[n]{ a_n }  = \dfrac{1}{2}
$$
则有$R = 2$，验证得收敛域为$(-2,2)$

求**缺项级数**$\sum_{n = 1}^\infty \dfrac{x^{2n}}{n-3^{2n}}$的收敛域，这个级数的$a_{2n-1}$都是$0$，所以也可取上极限
$$
\lim_{n\to\infty} \sup \sqrt[n]{ \dfrac{1}{\dfrac{n}{2}-3^{n}} } = \lim_{n\to\infty} \sup \sqrt[n]{ \dfrac{1}{-3^{n}} } = \dfrac{1}{3}
$$
从而$R= 3$，注意这里题目里给出的是$a_{2n}$，**需要自己先化成$a_n$的形式**，这道题也可以做$x^{2n} \to x^n$的换元，**这样就不用约化$a_n$了，但是求出的收敛半径需要开根号**

考虑幂级数$\sum_{n=1}^\infty \dfrac{(x-1)^n}{2^nn}$，它的收敛半径显然是$R=2$，但是讨论得收敛域是$[-1,3]$

证明如下展开式
$$
\ln \dfrac{1}{1-x} = x+\dfrac{x^2}{2}+\dfrac{x^3}{3} +\dfrac{x^4}{4} +\cdot
$$
只需在下式**两边积分**即可
$$
\dfrac{1}{1-x} = 1+x+x^2 +x^3 +\cdots 
$$
上式**两边求导**还可以得到
$$
\dfrac{1}{(1-x)^2} =1 +2x +3x^2 +\cdots+nx^{n-1} + \cdots
$$

求级数$\sum_{n =1}^\infty (-1)^{n-1} n^2x^n$的和函数，先提出一个$x$来
$$
S(x) = \sum_{n =1}^\infty (-1)^{n-1}n^2x^n = x \sum_{n =1}^\infty (-1)^{n-1}n^2 x^{n-1} = xg(x)
$$
这样就可以积分消掉一个$n$
$$
\int_0^x g(t)\mathrm{d} t = \sum_{n =1}^\infty (-1)^{n-1} nx^n = x\sum_{n =1}^\infty(-1)^{n-1}nx^{n-1} = xh(x)
$$
再次积分消$n$
$$
\int_0^nh(t)\mathrm{d} t = \sum_{n =1}^\infty (-1)^{n-1}x^n = -\sum_{n =1}^\infty(-x)^n= -\left( \dfrac{1}{1+x}-1 \right) =\dfrac{x}{1+x}
$$
于是有
$$
\begin{aligned}
h(x) & =\dfrac{\mathrm{d}}{\mathrm{d} {x}}\left( \dfrac{x}{1+x} \right) = \dfrac{1}{(1+x)^2} \\
g(x) & = \dfrac{\mathrm{d}}{\mathrm{d} {x}} \left( \dfrac{x}{(1+x)^2} \right) =\dfrac{1-x}{(1+x)^3} \\ 
S(x) & = \dfrac{x(1-x)}{(1+x)^3}
\end{aligned}
$$

**关键在于适当地提出$x^k$使得剩下的$x^{n-k}$在积分后获得的$\dfrac{1}{n-k+1}$因子能消去前面的含$n$系数**

求$\arctan$和$\arcsin$的幂级数展开式，考虑
$$
(1+x)^\alpha = \sum_{k = 0}^\infty  \binom{\alpha}{k}x^k
$$
分别代入$x\to x^2, \alpha= -1;x\to -x^2,\alpha = -\dfrac{1}{2}$，再两边积分即可，它们的收敛域都是$[-1,1]$，需要端点单独验证

求$(1-x)\ln(1-x)$在$x=0$处的幂级数展开式，只需要在$\ln(1+x)$的展开式中代入$x\to-x$再两边同乘$(1-x)$即可

求非初等函数$\displaystyle F(x) = \int_0^xe^{-t^2}\mathrm{d} t$的幂级数展开式，直接
$$
\begin{aligned}
F(x) & = \int_0^x\left( 1-t^2+\dfrac{t^4}{2!}-\dfrac{t^6}{3!}+\cdots \right) \mathrm{d} t  \\ \\
 & = x -\dfrac{x^3}{3}+\dfrac{1}{2!} \dfrac{x^5}{5} -\dfrac{1}{3!} \dfrac{x^7}{7} + \cdots 
\end{aligned}
$$
即可

## Fourier 级数
求
$$
f(x) = \begin{cases}
x, & 0 \le x \le \pi \\
0, & -\pi<x<0
\end{cases}
$$
的Fourier展开式

先确定周期区间为$(-\pi,\pi)\implies 2l = 2\pi \implies l = \pi$
于是
$$
a_0 = \dfrac{1}{\pi}\int_{-\pi}^\pi f(x) \mathrm{d} x = \dfrac{1}{\pi} \int_0^\pi x\mathrm{d} x = \dfrac{\pi}{2}
$$
以及
$$
\begin{aligned}
a_n  & = \dfrac{1}{\pi} \int_{-\pi}^\pi f(x)\cos nx \mathrm{d} x \\
 & =\dfrac{1}{\pi}\int_0^\pi x\cos nx \mathrm{d} x
\end{aligned}
$$
这里采用[[Table Method for Integration by Parts|表格积分法]]的技巧，有
$$
\begin{matrix}
x & 1 & 0 \\
\cos nx & \dfrac{1}{n}\sin nx & -\dfrac{1}{n^2}\cos nx
\end{matrix}
$$
知
$$
\begin{aligned}
\int x\cos nx \mathrm{d} x&= \dfrac{x}{n}\sin nx +\dfrac{1}{n^2}\cos nx \\
\int_0^\pi x\cos nx\mathrm{d} x  & = \dfrac{1}{n^2}(\cos n\pi -1) \implies a_n = \dfrac{1}{n^2\pi}((-1)^n-1)
\end{aligned}
$$
同理计算
$$
b_n = \dfrac{1}{\pi}\int_0^\pi x\sin nx \mathrm{d} x
$$
因为
$$
\begin{matrix}
x & 1 & 0 \\
\sin nx & -\dfrac{1}{n}\cos nx & -\dfrac{1}{n^2}\sin nx
\end{matrix}
$$
所以
$$
b_n = \dfrac{1}{\pi}\left[ -\dfrac{x}{n}\cos nx+\dfrac{1}{n^2}\sin nx \right]\bigg\vert_0^\pi =  -\dfrac{1}{n}(-1)^n 
$$
于是得到
$$
f(x) = \dfrac{a_0}{2}+\sum_{n = 0}^\infty (a_n\cos nx+b_n\sin nx),\quad x\in(-\pi,\pi)
$$
特别地，当$x=\pm \pi$时，有
$$
f(x) = \dfrac{f(-\pi+0)+f(\pi-0)}{2} = \dfrac{\pi}{2}
$$

求函数
$$
f(x) = \begin{cases}
0, & -5\le x < 0 \\
3, & 0\le x < 5
\end{cases}
$$
积分区间为$(-5,5),2l=10\implies l = 5$
$$
\begin{aligned}
a_0 &= \dfrac{1}{5}\int_0^53\mathrm{d} x = 3 \\
a_n &= \dfrac{1}{5}\int_0^5 3\cos\dfrac{n\pi x}{5}\mathrm{d} x = 0 \\
b_n &= \dfrac{1}{5}\int_0^5 3\sin \dfrac{n\pi x}{5}\mathrm{d} x = \dfrac{3}{n\pi}(1-(-1)^n)
\end{aligned}
$$
且在端点$x=\pm 5$的时候有$f(x) = \dfrac{3}{2}$，**在不连续点$x=0$的时候也有$f(x)=\dfrac{3}{2}$**

把$f(x)=x$在$(0,2)$上展开成余弦级数，需要做偶式延拓
$$
f(x) = \begin{cases}
-x, & -2<x<0 \\
x & 0\le x < 2
\end{cases}
$$
积分区间$(-2,2),2l = 4\implies l = 2$
$$
\begin{aligned}
a_0  & = \dfrac{1}{2} \int_{-2}^2 f(x) \mathrm{d} x = \int_0^2 x\mathrm{d} x = 2 \\
a_n & = \dfrac{1}{2}\int_{-2}^2f(x) \cos \dfrac{n\pi x}{2}\mathrm{d} x= \int_0^2 x\cos \dfrac{n\pi x}{2} \mathrm{d} x
\end{aligned}
$$
由于
$$
\begin{matrix}
x & 1 & 0 \\
\cos\dfrac{n\pi x}{2} & \dfrac{2}{n\pi}\sin \dfrac{n\pi x}{2} & -\dfrac{4}{n^2\pi^2}\cos\dfrac{n\pi x}{2}
\end{matrix}
$$
故有
$$
\begin{aligned}
\int x\cos\dfrac{n\pi x}{2}\mathrm{d} x  & = \dfrac{2x}{n\pi}\sin\dfrac{n\pi x}{2}+\dfrac{4}{n^2\pi^2}\cos \dfrac{n\pi x}{2} \\
\implies a_n  & = \dfrac{4}{n^2\pi^2} \left( (-1)^n-1 \right) 
\end{aligned}
$$
于是有
$$
f(x) = \dfrac{a_0}{2} +\sum_{n = 1}^\infty a_n \cos \dfrac{n\pi x}{2}
$$
没有需要讨论的特殊点

## 点集拓扑
对于平面点集
$$
D = \left\{ (x,y)\mid1\le x^2+ y^2<4 \right\} 
$$
则内点：$1<x^2+y^2<4$, 界点$x^2+y^2=1, x^2+y^2=4$，聚点$1\le x^2+y^2 \le 4$

## 二元函数的极限

设
$$
f(x,y) =\begin{cases}
xy \dfrac{x^2-y^2}{x^2+y^2}, & (x,y)\neq(0,0) \\
0,  & (x,y) = (0,0)
\end{cases}
$$
求$\lim_{(x,y)\to(0,0)}f(x,y)$
$$
\begin{aligned}
\left|{f(x,y)}\right| \le \left|{xy\dfrac{x^2+y^2}{x^2+y^2}}\right| = \left|{xy}\right| 
\end{aligned}
$$
而
$$
\lim_{(x,y)\to(0,0)} \left|{xy}\right| = 0
$$
故
$$
\lim_{(x,y)\to(0,0)} f(x,y) = 0
$$
**或者利用极坐标换元**

$\lim_{(x,y)\to(0,0)} \dfrac{xy}{x^2+y^2}$不存在，是因为
$$
\lim_{(x,y)\to(0,0)} \dfrac{mx^2}{x^2+m^2x^2}= \dfrac{m}{1+m^2}
$$

$$
\lim_{(x,y)\to(0,0)}f(x,y),\quad f(x,y) = 
\begin{cases}
1, & 0<y<x^2,-\infty < x <+\infty \\
0, & \text{otherwise}
\end{cases}
$$
不存在，因为取路径$y=\dfrac{x^2}{2}$和$y =0$得到的结果不同


### 典型不存在类型
摘自[[MA-Ex-8]]
$$
\lim_{ (x, y) \to (0, 0) } \dfrac{xy^3}{x^2 + y^6}
$$
取路径$1: x = y$, 有
$$
\lim_{ (x, y) \to (0, 0) } \dfrac{x^4}{x^2 + x^6} = +\infty
$$
取路径$2:x = y^3$, 有
$$
\lim_{ (x, y) \to (0, 0) } \dfrac{x^6}{x^6 + x^6} = \dfrac{1}{2}
$$
故极限不存在（或者直接取$x = ky^3$）

$$
\lim_{ (x, y) \to (0, 0) } \dfrac{x^6y^8}{(x^2+y^4)^5}
$$
取路径$1$: $x = y$, 有
$$
\lim_{ (x, y) \to (0, 0) } \dfrac{x^{14}}{(x^2 + x^4)^5} = \lim_{ (x, y) \to (0, 0) } \dfrac{x^{14}}{x^{20} + o(x^{20})} = + \infty
$$
取路径$2: x = y^2$，有
$$
\lim_{ (x, y) \to (0, 0) } \dfrac{y^{20}}{2^5 y^{20} } = \dfrac{1}{2^5}
$$
故极限不存在（或者直接取$x = ky^2$）
> [!Tip] 上面这两种分母里次数不对称的肯定有问题

$$
\lim_{ (x, y) \to (0, 0) } \dfrac{e^x - e^y}{\sin xy}
$$
由Taylor展开
$$
\lim_{ (x, y) \to (0, 0) } \dfrac{e^x - e^y}{\sin xy} =  \lim_{ (x, y) \to (0, 0) } \dfrac{x - y}{xy}
$$
取两条路径$x = y, x = -y$即可知极限不存在

$$
\lim_{ (x, y) \to (0,0) } \dfrac{xy}{\sqrt{ x + y + 1 } - 1} 
$$
**取路径$y=-x+kx^2$**（关键是要分母在取完极限后能化成单项式）
$$
\lim_{ (x, y) \to (0,0) } \dfrac{x(-x+kx^2)}{\sqrt{ kx^2 +1}-1} = \lim_{ (x, y) \to (0,0) } \dfrac{x^2(kx-1)}{\dfrac{1}{2}kx^2} = - \dfrac{2}{k}
$$
所以极限不存在

## 二元函数的连续性
讨论函数
$$
f(x,y) = 
\begin{cases}
\dfrac{x^\alpha}{x^2+y^2}, & (x,y)\neq(0,0) \\
0 & (x,y) =(0,0)
\end{cases}
$$
在点$(0,0)$处的连续性，考虑极限
$$
\lim_{(x,y)\to(0,0)} \dfrac{x^\alpha}{x^2+y^2}
$$
代入路径$y=kx$则有
$$
\lim_{(x,y)\to(0,0)} \dfrac{x^\alpha}{(1+k^2)x^2} = \lim_{(x,y)\to(0,0)} \dfrac{x^{\alpha-2}}{1+k^2}
$$
极限存在的必要条件是
$$
\lim_{(x,y)\to(0,0)}  x^{\alpha-2}=0
$$
故而需要$\alpha>2$，此时一定有
$$
\lim_{(x,y)\to(0,0)}  \dfrac{x^\alpha}{x^2+y^2} = \lim_{(x,y)\to(0,0)} \dfrac{x^2}{x^2+y^2} \cdot x^\alpha \le \lim_{(x,y)\to(0,0)}  x^\alpha = 0
$$
故这也是充分条件（**也可利用极坐标换元来证**）

讨论
$$
f(x,y) = 
\begin{cases}
\dfrac{\sin xy}{\sqrt{ x^2+y^2 }}, & x^2+y^2 \neq 0 \\
0, & x^2+y^2=0
\end{cases}
$$
的连续性的时候**需要考虑整个$\mathbb{R}^2$上的连续性**

## 多元函数的微分
分析$f(x,y) = xy$在$(x_0,y_0)$处的可微性，则有
$$
\Delta f = (x_0+\Delta x)(y_0 + \Delta y) -x_0y_0 = x_0\Delta y + y_0 \Delta x + \Delta x \Delta y
$$
期中
$$
\lim_{\rho = \sqrt{ \Delta x^2 + \Delta y^2 } \to0} \left|{\dfrac{\Delta x \Delta y}{\rho}}\right| \le\lim_{t\to 0}\left|{\dfrac{t^2}{\sqrt{ 2 }t}}\right| = 0,\quad t = \max\{\Delta x,\Delta y\}
$$
故有
$$
\mathrm{d} f = x_0 \mathrm{d} y + y_0 \mathrm{d} x
$$

考察函数
$$
f(x,y) =
\begin{cases}
\dfrac{xy}{\sqrt{ x^2+y^2 }},  & x^2+y^2\neq0 \\
0, & x^2+y^2 = 0
\end{cases}
$$
在$(0,0)$处的可微性，先考察原点处的偏导数（**由于是分段函数，只能通过定义来求**）
$$
f_x(0,0) = \lim_{x\to0} f(x,0) - f(0,0) = 0
$$
同理
$$
f_y(0,0) = 0
$$
**如果$f$在原点可微**，则有
$$
\mathrm{d} f = \dfrac{\Delta x\Delta y}{\sqrt{ \Delta x^2+\Delta y^2 }} = f_x(0,0)\Delta x + f_y(0,0)\Delta y + o(\rho) = o(\rho)
$$
这告诉我们
$$
\lim_{\rho \to 0} \dfrac{\Delta x\Delta y}{\rho^2} = 0
$$
而左边的极限不存在，故不可微

应用公式$S=\dfrac{1}{2}ab\sin C$计算某三角形的面积，现在测得$a=a_0,b=b_0,C=c_0$，测量误差为$\Delta a, \Delta b, \Delta C$，则有**绝对误差**
$$
\begin{aligned}
\left|{\Delta S}\right| &\approx \left|{\mathrm{d} S}\right| = \left|{\dfrac{\partial {S}}{\partial {a}}\mathrm{d} a + \dfrac{\partial {S}}{\partial {b}} \mathrm{d} b + \dfrac{\partial {S}}{\partial {C}}\mathrm{d} C}\right|  \\
&\le \left|{\dfrac{\partial {S}}{\partial {a}}}\right| \left|{\mathrm{d} a}\right| + \left|{\dfrac{\partial {S}}{\partial {b}}}\right| \left|{\mathrm{d} b}\right| + \left|{\dfrac{\partial {S}}{\partial {C}}}\right|\left|{\mathrm{d} C}\right| \\
 & = \dfrac{1}{2}|b\sin C|\Delta a + \dfrac{1}{2}\left|{a\sin C}\right|\Delta b + \dfrac{1}{2}|ab\cos C|\Delta C
\end{aligned}
$$
和**相对误差限**$\left|{\dfrac{\Delta S}{S}}\right|$，**注意加绝对值**

### 复合函数高阶导数
摘自[[MA-Ex-9]]
#### T1
$$
u = f(w),\quad w=x^2 + y^2 + z^2
$$
求
$$
\dfrac{\partial^2 {u}}{\partial {x}^2}, \dfrac{\partial {u}}{\partial {x}}{y}
$$
**解**：
$$
\begin{aligned}
\dfrac{\partial {u}}{\partial {z}} &= 2f'x \\
\dfrac{\partial^2 {u}}{\partial {x}^2} &= \dfrac{\partial}{\partial {x}}\left(2x\dfrac{\partial {f}}{\partial {w}}\right) = 2\dfrac{\partial {f}}{\partial {w}} + 2x \dfrac{\partial}{\partial {w}}\;\left(\dfrac{\partial {f}}{\partial {w}}\right)\dfrac{\partial {w}}{\partial {x}} = 2f'+ \boxed{4x^2f''} \\
\dfrac{\partial {u}}{\partial {x}}{y} &= \dfrac{\partial}{\partial {y}}\left(2x\dfrac{\partial {f}}{\partial {w}}\right) = 2x \dfrac{\partial}{\partial {w}}\left(\dfrac{\partial {f}}{\partial {w}}\right)\dfrac{\partial {w}}{\partial {y}} = 4xyf''
\end{aligned}
$$
#### T2
$$
z = f(u, v, w);\;u = x + y; v = xy; z = \dfrac{x}{y}
$$
求
$$
z_{xx}, z_{xy}
$$
**解**：
$$
\begin{aligned}
z_x & = \dfrac{\partial {f}}{\partial {u}} + y \dfrac{\partial {f}}{\partial {v}} + \dfrac{1}{y} \dfrac{\partial {f}}{\partial {w}}  \\ 
z_{xx} & = \dfrac{\partial}{\partial {x}} \left( \dfrac{\partial {f}}{\partial {u}} + y \dfrac{\partial {f}}{\partial {v}} + \dfrac{1}{y} \dfrac{\partial {f}}{\partial {w}} \right)   \\
 & = \left[ \dfrac{\partial^2 {f}}{\partial {u}^2} + y\dfrac{\partial {f}}{\partial {u}}{v} + \dfrac{1}{y} \dfrac{\partial {f}}{\partial {u}}{w} \right]  \\
 & + y\left[ \dfrac{\partial {f}}{\partial {v}}{u} + y\dfrac{\partial^2 {f}}{\partial {v}^2} + \dfrac{1}{y} \dfrac{\partial {f}}{\partial {v}}{w} \right] \\
 & + \dfrac{1}{y} \left[ \dfrac{\partial {f}}{\partial {w}}{u} + y\dfrac{\partial {f}}{\partial {w}}{v} + \dfrac{1}{y} \dfrac{\partial^2 {f}}{\partial {w}^2} \right]   \\
 & = \dfrac{\partial^2 {f}}{\partial {u}^2} + 2y \dfrac{\partial {f}}{\partial {u}}{v} + \dfrac{2}{y} \dfrac{\partial {f}}{\partial {u}}{w} + y^2 \dfrac{\partial^2 {f}}{\partial {v}^2}+2\dfrac{\partial {f}}{\partial {v}}{w} + \dfrac{1}{y^2} \dfrac{\partial^2 {f}}{\partial {w}^2} \\
z_{xy} & = \dfrac{\partial}{\partial {y}} \left( \dfrac{\partial {f}}{\partial {u}} + y \dfrac{\partial {f}}{\partial {v}} + \dfrac{1}{y} \dfrac{\partial {f}}{\partial {w}} \right)   \\
 & = \left[ \dfrac{\partial^2 {f}}{\partial {u}^2} + x\dfrac{\partial {f}}{\partial {u}}{v} - \dfrac{x}{y^2} \dfrac{\partial {f}}{\partial {u}}{w} \right]  \\
 & + y\left[ \dfrac{\partial {f}}{\partial {v}}{u} + x\dfrac{\partial^2 {f}}{\partial {v}^2} - \dfrac{x}{y^2} \dfrac{\partial {f}}{\partial {v}}{w} \right] \\
 & + \dfrac{1}{y} \left[ \dfrac{\partial {f}}{\partial {w}}{u} + x\dfrac{\partial {f}}{\partial {w}}{v} - \dfrac{x}{y^2} \dfrac{\partial^2 {f}}{\partial {w}^2} \right] \\
 & + \boxed{\dfrac{\partial {f}}{\partial {v}} \dfrac{\partial}{\partial {y}} \left( y \right)  + \dfrac{\partial {f}}{\partial {w}} \dfrac{\partial}{\partial {y}} \left( \dfrac{1}{y} \right) } \\
 & = \dfrac{\partial^2 {f}}{\partial {u}^2} + (x + y) \dfrac{\partial {f}}{\partial {u}}{v} + \left( \dfrac{1}{y} -\dfrac{x}{y^2} \right) \dfrac{\partial {f}}{\partial {u}}{w} + xy \dfrac{\partial^2 {f}}{\partial {v}^2} - \dfrac{x}{y^3}\dfrac{\partial^2 {f}}{\partial {w}^2}  \\& + \boxed{\dfrac{\partial {f}}{\partial {v}} -\dfrac{1}{y^2}\dfrac{\partial {f}}{\partial {w}}} 
\end{aligned}
$$

#### 总结
要写成
$$z = f(u, v, w);\;u = x + y; v = xy; z = \dfrac{x}{y}$$
的形式，而不是直接
$$
z = f(x + y, xy, \dfrac{x}{y})
$$


对$f(x,y) = \dfrac{1}{\sqrt{ x^2-2xy+1 }}$应用微分中值定理，证明存在$\theta(0<\theta<1)$使得
$$
1-\sqrt{ 2 } = \sqrt{ 2 } (1-3\theta)(1-2\theta+3\theta^2)^{-3/2}
$$
计算
$$
f_x = -\dfrac{1}{2}(x^2-2xy+1)^{-3/2} \cdot (2x-2y) = (y-x)(x^2-2xy+1)^{-3/2}
$$
和
$$
f_y = -\dfrac{1}{2}(x^2-2xy+1)^{-3/2} \cdot (-2x) = x(x^2-2xy+1)^{-3/2}
$$
运用两点连线的微分中值定理
$$
\begin{aligned}
\dfrac{1}{\sqrt{ x^2-2xy+1 }} &- \dfrac{1}{\sqrt{ x_0^2-2x_0y_0+1 }}  \\
= f_x(x_0+\theta \Delta x,y_0+\theta\Delta y)\Delta x &+f_y(x_0+\theta\Delta x,y_0+\theta\Delta y)\Delta y
\end{aligned}
$$
总有这样一个因子
$$
\left[ (x_0+\theta\Delta x)^2-2(x_0+\theta\Delta x)(y_0+\theta \Delta y)+1 \right]^{-3/2} 
$$
展开有
$$
\left[ x_0^2+2\theta x_0 \Delta x + \theta^2\Delta x^2-2x_0y_0-2\theta x_0\Delta y-2\theta y_0\Delta x-2\theta^2\Delta x\Delta y +1\right]^{-3/2}
$$
整理后
$$
\left[  \Delta x(\Delta x-2\Delta y)\theta^2+2(x_0\Delta x-x_0\Delta y-y_0\Delta x)\theta+1+x_0^2-2x_0y_0\right] ^{-3/2}
$$
可以令$\Delta x=1, \Delta y= -1,x_0=0,y_0 =1\implies x=1,y=0$，就有
$$
\dfrac{1}{\sqrt{ 2 }} - 1 = \left[ 1\cdot((1-\theta)-(0+\theta)) -1\cdot(0+\theta) \right](1-2\theta+3\theta^2)^{-3/2} 
$$
即待证明的原式

求$f(x,y) = x^y$在点$(1,4)$的Taylor公式（取到二阶），回忆二元情况下的公式
$$
f(x_0+a,y_0+b) - f(x_0,y_0) = \sum_{k = 1}^\infty \left[ \dfrac{1}{k!} \sum_{p+q=k} \binom{k}{p}\dfrac{\partial^kf}{\partial^px\partial^qy}\bigg\vert_{(x_0,y_0)}a^pb^q\right] 
$$
取到二阶就是
$$
(1+a)^{4+b}- 1 = \left( \dfrac{\partial {f}}{\partial {x}}a+\dfrac{\partial {f}}{\partial {y}}b \right) +\dfrac{1}{2!}\left( \dfrac{\partial^2 {f}}{\partial {x}^2} a^2 + 2\dfrac{\partial {f}}{\partial {x}}{y}ab + \dfrac{\partial^2 {f}}{\partial {y}^2}b^2 \right) 
$$
计算并代入即可

求$f(x,y) = x^2+5y^2-6x+10y+6$的极值
$$
f_x=f_y = 0\implies x=3,y=-1
$$
且有
$$
\begin{pmatrix}
f_{xx}  & f_{xy} \\
f_{yx}  & f_{yy}
\end{pmatrix} = \begin{pmatrix}
2 & 0 \\
0 & 10
\end{pmatrix}
$$
正定，故$f(x,y)$在该点处取到极小值

函数$f(x,y) = (y-x^2)(y-2x^2)$在原点处取到驻点，但是Hessian矩阵不定无法判断，但是因为$f(0,0)=0$且$f(x)$在原点附近$x^2<y<2x^2$的区域小于$0$，在原点附近$x^2>y$的趋于大于$0$，故$f(x,y)$不可能在原点处取极值

## 隐函数
讨论Descartes叶型线$x^3+y^3-3axy=0$所确定的隐函数的一阶和二阶导数
设$F(x,y)=x^3+y^3-3axy=0$确定了隐函数$y=g(x)$，则有（**注意哪个Jacobian是分母，哪个是分子**）
$$
g'(x) = -\dfrac{F_x}{F_y} = -\dfrac{3x^2-3ay}{3y^2-3ax} = \dfrac{x^2-ay}{ax-y^2}
$$
再次求导得到（**注意$y$也是$x$的函数**）
$$
\begin{aligned}
g''(x) = - \dfrac{2a^3xy}{(y^2-ax)^3}
\end{aligned}
$$

