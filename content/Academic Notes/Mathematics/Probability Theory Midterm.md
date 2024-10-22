# 变量变换
## 一般情况
$$
f_{\boldsymbol Y} \left( \boldsymbol y \right)  = f_{\boldsymbol X}(\boldsymbol g^{-1}(\boldsymbol y)) \left|\begin{vmatrix}
\dfrac{ \partial \boldsymbol x }{ \partial \boldsymbol y } 
\end{vmatrix}\right|
$$
where $\boldsymbol g: \boldsymbol X = \boldsymbol x \iff \boldsymbol Y = \boldsymbol g(\boldsymbol x)$
## 加法/减法
For **independent** $X, Y$
$$
f_{X+Y}(z) = \int_{-\infty}^\infty f_X(x) f_Y(z - x) \mathrm{d}x
$$
## 乘法
For **independent** $X, Y$
$$
f_{XY}(z ) = \int_{-\infty}^{\infty} \dfrac{1}{\left|x\right|} f_X(x) f_Y(\dfrac{z}{x}) \mathrm{d}x
$$
## 除法
For **independent** $X, Y$
$$
f_{X/Y}(z ) = \int_{-\infty}^{\infty} {\left|y\right|} f_X(yz) f_Y(y) \mathrm{d}y
$$
# 常见分布及其性质
## 二项分布
$$
X \sim \mathrm{Bin}(n, p) \iff P(X = k) = \binom{n}{k} p^k (1-p)^{n-k}
$$
with $\mathrm{E}[X] = np,\ \mathrm{Var}(X) = n p (1-p)$

If $X_i \sim \mathrm{Bin}(n_i,p)$ and $X_1, \ldots ,X_k$ are **independent**, we can conclude
$$
\sum_{i = 1}^k X_i \sim \mathrm{Bin}\left( \sum_{i= 1}^k n_i,\ p \right) 
$$
## 多项分布
$$
P(X_1=n_1, \ldots ,X_k = n_k) = \dfrac{n!}{n_1!n_2! \cdots n_k!}\cdot p_1^{n_1} p_2^{n_2} \cdots p_k^{n_k}
$$
where $n_1 + n_2 + \cdots + n_k = n$, 
with $\mathrm{E}[X_i] = np_i$,$\mathrm{Var}(X_i) = np_i(1-p_i)$,$\mathrm{Cov}(X_i, X_j) = -np_ip_j \ (i \neq j)$
## 几何分布
$$
P(X = k) = (1-p)^{k-1}p
$$
with $\mathrm{E}[X] = \dfrac{1}{p}$,$\mathrm{Var}(X)=\dfrac{1-p}{p^{2}}$
## 负二项分布
$X$for all trials until$r$success
$$
P(X = k) = \binom{k -1}{r -1} p^r (1-p)^{k - r}
$$
with $\mathrm{E}[X] = \dfrac{r}{p},\ \mathrm{Var}(X) = \dfrac{r(1-p)}{p^{2}}$
## 超几何分布
$$
P(X = k) = \dfrac{\binom{N}{k}\binom{N-K}{n-k}}{\binom{N}{n}}
$$
with $\mathrm{E}[X] = n \cdot \dfrac{K}{N}$
## 指数分布
$X$ be the waiting time until the first arrival of a success which arrives at a rate of $\lambda$successes per unit of time.
$$
f(x)  = \lambda \exp(-\lambda x)
$$
with $\mathrm{E}[X] = \dfrac{1}{\lambda}$and$\mathrm{Var}(X) = \dfrac{1}{\lambda^{2}}$
## Poisson分布
Under a Poisson distribution with the expectation of $\lambda$ events in a given interval, the probability of $k$ events in the same interval is
$$
P(X = k) = \dfrac{\lambda^k \exp(-\lambda)}{k!}
$$
with $\mathrm{E}[X]= \lambda, \ \mathrm{Var}(X) = \lambda$

Let $X_1 \sim \mathrm{Pois}(\lambda_1), \ X_2 \sim \mathrm{Pois}(\lambda_2)$ and $X_1, X_2$ are independent, then we will have
$$
X_1 + X_2 = \mathrm{Pois}(\lambda_1 + \lambda_2)
$$
## Beta分布
$$
f(x) = \frac{1}{\beta(a,b)}x^{a-1}(1-x)^{b-1}, \quad 0 < x < 1
$$
where
$$
\beta(a,b) = \int_0^1 x^{a-1}(1-x)^{b-1} \mathrm{d}x
$$
with $\mathrm{E}[X] = \dfrac{a}{a+b}$
## Gamma分布
$$
f(y) = \frac{1}{\Gamma(a)}(\lambda y)^a e^{-\lambda y} \frac{1}{y}, \quad y>0
$$
where
$$
\Gamma(s) = \int_0^{+\infty} x^{s-1}e^{-x}\mathrm{d} x
$$
# 数字特征
## 期望
Linearity
$$
\mathrm{E}[aX + bY] = a\mathrm{E}[X] + b \mathrm{E}[Y]
$$
For **independent** r.v.s$X_1, \ldots ,X_n$, we have
$$
\mathrm{E}[X_1 \cdots X_n] = \mathrm{E}[X_1] \cdots \mathrm{E}[X_n]
$$
## 方差
Definition
$$
\mathrm{Var}(X) = \mathrm{E} \left[ \left( X - \mathrm{E[X]} \right) ^{2} \right] 
$$
With the linearity of expectation
$$
\mathrm{Var} (X) = \mathrm{E}\left[ X^{2} \right] - \mathrm{E}^{2}[X]
$$
- $\mathrm{Var}(X+c) = \mathrm{Var}(X)$ for any constant$c$
- $\mathrm{Var}(cX) = c^{2} \mathrm{Var}(X)$ for any constant$c$
- If $X$ and $Y$ are independent, then $\mathrm{Var}(X+Y) = \mathrm{Var}(X) + \mathrm{Var}(Y)$
- For any constant $c$, $\mathrm{Var}(X) \leq \mathrm{E}\left[ \left( X-c \right)^{2} \right]$. The equality holds if and only if $c = \mathrm{E}[X]$. This means $\mathrm{E}\left[ (X-c)^{2} \right]$reaches its minimum when $c = \mathrm{E}[X]$, and the value of this minimum is $\mathrm{Var}(X)$
## 条件期望
### Conditional Expectation
$$
\mathrm{E}[Y] = \mathrm{E}[\mathrm{E}[Y | X]]
$$
### Conditional Variance
$$
\mathrm{Var}(Y) = \mathrm{Var}(\mathrm{E}[Y | X])+ \mathrm{E}[\mathrm{Var}(Y | X)]
$$
## 协方差和相关系数
$$
\mathrm{Cov}(X,Y) = \mathrm{E}\left[ (X-\mathrm{E}[X])(Y - \mathrm{E}[Y]) \right] 
$$
this implies
$$
\mathrm{Cov}(X,Y) = \mathrm{E}[XY] - \mathrm{E}[X] \mathrm{E}[Y]
$$
> While independence implies a zero covariance,$X$and$Y$are uncorrelated does not mean they are independent. 

1.$\mathrm{Cov}(X, a) = 0$
2.$\mathrm{Cov}(X,X) = \mathrm{Var}(X)$
3.$\mathrm{Cov}(X,Y) = \mathrm{Cov}(Y, X)$
4.$\mathrm{Cov}(X+ a, Y + b) = \mathrm{Cov}(X, Y)$
5. 
$$
\begin{aligned}
\mathrm{Cov}(aX + bY, cW + dV) &= ac\ \mathrm{Cov}(X, W)+ ad\ \mathrm{Cov}(X, V)  \\
&\quad+ bc\ \mathrm{Cov}(Y, W) + bd \ \mathrm{Cov}(Y,V)
\end{aligned}
$$

# 题目
## T1
> 从一批产品中任取$n$件, 以事件$A_i$表示"第$i$件取得正品", 用它们表示以下事件
> 1. 仅仅只有一件是是次品
> 2. 至少有两件不是次品

1. 可以直接列出所有情况得
$$
E_1 =  \bar{A}_1 A_2 \cdots A_n + A_1 \bar{A}_2 \cdots A_n + A_1 A_2 \cdots \bar{A}_n
$$
或者用示性函数表达
$$
E_1 : I_{A_1} + \cdots +I_{A_n} = n-1
$$
其中
$$
I_A= \begin{cases}
1, & A \\
0, & \bar{A}
\end{cases}
$$
2. 直接使用示性函数
$$
I_{A_1} + I_{A_2} + \cdots +I_{A_n} \geq 2
$$
## T2
> 设有来自$2$个地区的考生的报名表, 其中第$k$个地区男女生报名表分别有$b_k$份和$g_k$份, $k = 1, 2$. 随机取一个地区的报名表, 从中先后抽取两份, 求
> 1. 先抽到的一份是女生表的概率
> 2. 已知后抽到的一份是男生表, 求先抽到的一份是女生表的概率
> 3. 假设不先确定一个地区, 而是从所有报名表中随机抽取两份. 如果已知后抽到的一份是
> 一个男生的报名表, 那么问先抽到的一份是同地区一个女生的报名表的可能性有多大?

1. 设$P_k$代表选择$k$地区的报名表的概率
$$
P(G, \cdot)  = P(G_1, \cdot) P_1+ P(G_2, \cdot)P_2 = \dfrac{1}{2} \dfrac{g_1}{b_1 + g_1} + \dfrac{1}{2} \dfrac{g_2}{b_2+ g_2}
$$
2. 由条件概率定义
$$
P(G, \cdot \mid \cdot, B) = \dfrac{P(G, B)}{P(\cdot, B)}
$$
其中
$$
\begin{aligned}
P(G, B) &= P(G_1, B_1) P_1 + P(G_2, B_2) P_2 \\
&= \dfrac{g_1 b_1}{2(g_1 + b_1)(g_1 + b_1 - 1)} + \dfrac{g_2 b_2}{2(g_2 + b_2)(g_2 + b_2 - 1)} 
\end{aligned}
$$
以及
$$
P(\cdot, B) = P(\cdot, B_1)P_1 + P(\cdot, B_2) P_2 = \dfrac{1}{2} \dfrac{b_1}{g_1 + b_1} + \dfrac{1}{2} \dfrac{b_2}{g_2 + b_2}
$$
于是可得$P(G, \cdot \mid \cdot, B)$
3. 有全概率公式
$$
\begin{aligned}
P(G, \cdot \mid \cdot, B;\text{同一地区}) &= P(G_1, \cdot \mid \cdot, B_1) P(\cdot, B_1 \mid \cdot, B) + P(G_2, \cdot \mid \cdot, B_2) P(\cdot, B_2 \mid \cdot, B) \\
&= \dfrac{P(G_1, B_1) + P(G_2, B_2)}{P(\cdot, B)}
\end{aligned}
$$
其中
$$
P(G_i, B_i) = \dfrac{g_i}{b_1 + g_1 + b_2 + g_2} \dfrac{b_i}{b_1 + g_1 + b_2 + g_2-1}
$$
以及
$$
P(\cdot, B) = \dfrac{b_1 + b_2}{b_1 + g_1 + b_2 + g_2}
$$

## T3
> 从装有$m$个白球, $n$个黑球的袋中不放回地取球, 直到摸出白球时停止, 记$X$为取出的黑球的个数, 求$X$的分布

考虑$X = k$的情况, 此时则前$k$次都是黑球, 而第$k + 1$次摸出的白球
$$
\begin{aligned}
P(\text{前$k$次都是黑},\text{第$k+1$次是白}) &= P(\text{第$k+1$次是白} \mid \text{前$k$次都是黑}) P(\text{前$k$次都是黑}) \\
&= \dfrac{m}{n + m - k} \cdot \dfrac{\binom{n}{k}}{\binom{n+m}{k}}
\end{aligned}
$$
> [!Tip]
> **不要相信直觉**! 尽可能使用条件概率和全概率公式来推理

## T4
> 独立重复抛硬币, $A =$“抛一次得正面”, $p = P(A)$, 记$X$为最早得到2个正面时抛硬币的次数, $Y$为最早得到连续2个正面时抛硬币的次数. 求$X, Y$各自的概率分布. 

考虑$X=k$的情况, 则第$k$次是正面且前$k -1$次出现了$1$次正面, 则
$$
\begin{aligned}
P(\text{第$k$次是正}, \text{前$k -1$次$1$次正}) &= P(\text{第$k$次是正}| \text{前$k -1$次$1$次正})P(\text{前$k -1$次$1$次正}) \\
&= p \cdot \binom{k - 1}{1} p(1-p)^{k -2}\\
&= (k-1) p^{2} (1-p)^{k-2}
\end{aligned}
$$
考虑$Y = k$的情况, 当$k >2$时, 采用首步分析法
$$
P(Y = k) = P(Y =k \mid \bar{A}_1) P (\bar{A}_1) + P(Y = k \mid A_1A_2) P(A_1 A_2) = P(Y = k \mid A_1 \bar{A}_2) P(A_1\bar{A}_2)
$$
其中
$$
P(Y = k \mid \bar{A}_1 ) = P (Y = k -1), \ P(Y = k \mid A_1A_2) = 0, \ P(Y = k \mid A_1 \bar{A}_2) = P(Y = k - 2)
$$
从而设$p_k = P(Y = k)$, 有
$$
p_k = (1-p)p_{k -1} + p(1-p) p_{k -2}
$$
> [!Tip]
> 对于一个序列事件, 既可以用全概率公式展开尾部情况, 也可以站看首部情况

## T5
> 设随机变量$X$服从$(- \pi /2, \pi / 2)$上的均匀分布, 求
> 1. 随机变量$Y = \cos X$的概率密度函数
> 2. $Y$的数学期望和方差

1. 当$x > 0$时, 
$$
y = \cos x \implies x = \arccos(y) \implies \frac{ \partial x }{ \partial y } = - \dfrac{1}{\sqrt{ 1 - y^{2} }}
$$
从而由变换公式
$$
\begin{aligned}
f_Y(y|x > 0) = f_X(x | x > 0) \left|\frac{ \partial x }{ \partial y } \right| &= f_X \left[ \arccos(y) \right] \cdot \dfrac{1}{\sqrt{ 1-y^{2} }} \\
&= \dfrac{2}{\pi \sqrt{ 1-y^{2} }}
\end{aligned}
$$
同理又有$f_Y(y| x < 0) = \dfrac{2}{\pi}\sqrt{ 1-y^{2} }$, 故
$$
f_Y(y) = \dfrac{1}{2}f_Y(y | x > 0) + \dfrac{1}{2} f_Y(y| x < 0) = \dfrac{2}{\pi \sqrt{ 1-y^{2} }}
$$
> [!Tip]
> 注意$\arccos$的值域, 不要忘记分类讨论

2. 由定义
$$
\mathrm{E}[y] = \int_0^1 y f_Y(y)\mathrm{d}y = \int_{0}^1 \dfrac{2y \mathrm{d}y}{\pi \sqrt{ 1-y^{2} }} = - \dfrac{1}{\pi} \int_1^0 \dfrac{\mathrm{d}(1-y^{2})}{\sqrt{ 1-y^{2} }} = \dfrac{1}{\pi}\left[ 2 u^{1/2} \right] \bigg|^1_0 = \dfrac{2}{\pi}
$$
且
$$
\mathrm{E}[Y^{2}]= \int_0^1 \dfrac{2y^{2} \mathrm{d}y}{\pi \sqrt{ 1-y^{2} }} 
$$
设$y = \sin t, \ t\in[0, \dfrac{\pi}{2}]$, 从而$\mathrm{d}y = \cos t \mathrm{d}y,\  \sqrt{ 1-y^{2} } = \cos t$, 于是
$$
\begin{aligned}
\mathrm{E}[Y^{2}] &= \int_0^{\pi/2} \dfrac{2\sin ^{2}t \cos t \mathrm{d}t}{\pi \cos t} \\
&= \int_0^{\pi/2} \dfrac{2}{\pi} \sin ^{2}t \mathrm{d}t \\
&= \dfrac{1}{\pi} \int_0^{\pi/2} \left( 1 - \cos 2t \right)  \mathrm{d}t \\
&= \dfrac{1}{\pi} \left[ t - \dfrac{1}{2}\sin2t \right] \bigg|_0^{\pi/2} \\
&= \dfrac{1}{\pi} \left( \dfrac{\pi}{2}  \right) = \dfrac{1}{2}
\end{aligned}
$$
从而$\mathrm{Var}(Y) = \mathrm{E}[Y^{2}] - \mathrm{E}^{2}[Y] = \dfrac{1}{2} - \dfrac{4}{\pi^{2}}$

## T6
> 袋中装有$N$个球, 其中白球的数量为随机变量$X$, 已知$\mathrm{E}[X] = n$. 
> 1. 证明从该袋中摸出一球为白球的概率$\dfrac{n}{N}$. 
> 2. 由1中结论解决如下问题: 从装有$a$个黑球, $b$个白球的袋中每次取出一个球, 每次把取出的球换成一个黑球并将其放回. 记$H_k$表示事件“第$k$次取出的是黑球”, 求$P(H_k)$的值

1. 由全概率公式
$$
P(B) = \sum_{k  = 0}^N P(B \mid X = k) P(X = k) = \sum_{k=0}^N \dfrac{k}{N} P(X = k) = \dfrac{n}{N}
$$
2. 设$X_k$为第$k$次取球前袋中的黑球数, 则
$$
P(H_k) = \dfrac{\mathrm{E}[X_k]}{a + b}
$$
其中
$$
X_k = X_{k -1} + I_{\bar{H}_{k}} = \begin{cases}
X_{k-1}, &H_{k} \\
X_{k-1} + 1 &\bar{H}_k
\end{cases}
$$
于是
$$
\mathrm{E}[X_k] = \mathrm{E}[X_{k-1}] P(H_k) + \left( \mathrm{E}[X_{k-1} ] + 1 \right) (1 - P(H_k))  
$$
从而
$$
\mathrm{E}[X_k] = \mathrm{E}[X_{k - 1}] + 1 - \dfrac{\mathrm{E[X_k]}}{a+b}
$$
解差分方程可以得到答案
## T7
> 一盒子里有$n$个球, 编号为$1,2, \ldots ,n$. 逐个有放回地从盒子里随机取出$m$个球, $m\leq n$. 求取出的球的编号按照严格上升次序排列的概率

先计算总的取法个数, 因为每次取完球都会放回, 所以每次都有$n$种可能, 而一共有$m$次, 从而总取法为$n^m$. 而严格上升次序相当于我要在$n$个球中挑出$m$个球, 然后把它们按照升序排序, 所以一共有$\binom{n}{m}$中取法, 所以总的概率就是
$$
P = \dfrac{\binom{n}{m}}{n^m} = \dfrac{n!}{m!(n-m)! n^m}
$$

## T8
> 将$n$根短绳的$2n$个端头任意两两连接, 试求恰好连成$n$个圈的概率

考虑这$2n$个端头, 第$1$个端头可以连接剩下的$(2n-1)$个端头, 设第$2$个端头就是那个和第1个连接的, 那么第$3$个端头就可以连接剩下的$(2n-3)$个端头, 以此类推就一共有
$$
(2n-1)(2n-3) \cdots 3 \cdot 1 = (2n-1)!!
$$
种连接方案, 所以概率应该为$\dfrac{1}{(2n-1)!!}$. 

> [!Tips]
> 求样本空间的大小时一般必须满足不能重复（**所以建议用小样例进行验证**）. 但事实上我们也可以设计一个可以有“重复”的样本空间来求概率

**另解**: 设想把$2n$个端头排成一行, 然后规定$2k-1$个端头与第$2k$个端头相连接. 于是每一种排法对应一种连接方式（这其实是有重复情况出现的, 但是没关系）, 从而$\left|\Omega\right| = (2n)!$. 以$A$表示恰好连成$n$个圈的事件, $A_k$表示第$k$号短绳被连成$1$个圈的事件, 则$A = A_1 \cap \cdots \cap A_n$.

当$A_1$发生时, 相当于有一个$k\in[n]$使得在$2n$个端头的排列中, $1$号短绳的两个端头排在第$2k-1$和第$2k$个位置上, 所以$\left|A_1\right| = 2n(2n-2)!$. 因此
$$
P(A_1) = \dfrac{\left|A_1\right|}{\left|\Omega\right|} = \dfrac{1}{2n-1}
$$
再考虑事件$A_2|A_1$, 这其实就是把问题转化为了$n' = n-1$的情况从而
$$
P(A_2|A_1) = \dfrac{\left|A_1'\right|}{\left|\Omega'\right|} = \dfrac{1}{2n' -1} = \dfrac{1}{2n -3}
$$
同理可得
$$
P(A_k|A_1A_2 \cdots A_{k-1}) = \dfrac{1}{2n-2k + 1}, \quad k = 3,4, \ldots ,n
$$
于是就有
$$
P(A) = P(A_1A_2 \cdots A_k) = \dfrac{1}{2n-1} \cdot \dfrac{1}{2n-3} \cdots \dfrac{1}{1} = \dfrac{1}{(2n-1)!!}
$$


