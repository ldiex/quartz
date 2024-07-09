# 积分相等的前提
$$
\int_0^x f(t) \mathrm{d} t = F(x) \iff \color{red}{F(0) = 0}
$$

# 逐步求导、积分时注意定义域
先确定收敛区是$[-R, R],(-R, R],[-R, R), (-R, R)$
然后在这个区间上求导、积分的时候，如果得到的新函数在这个区间内的某一点没有定义，需要缩小对应的定义域
并在最后对这些奇点单独讨论

# 要求某一个函数的幂级数展开可以先对它求导/求积
例如求
$$
f(x) = \ln(x + \sqrt{1 + x^2})
$$
可以由
$$
\dfrac{\mathrm{d} {f}}{\mathrm{d} {x}} = \dfrac{1}{\sqrt{1 + x^2}}
$$
方便地给出

# 幂级数系数可能为$0$
如级数
$$
\sum_{n = 1}^\infty \dfrac{x^{2n-1}}{(2n - 1)!}
$$
它的$a_n$为
$$
a_n = 
\begin{cases} \dfrac{1}{n!} &, n \text{ is odd} \\
0 &, n \text{ is even}
\end{cases}
$$

# 更快地估计$\ln 2$的近似值
利用$\ln 2 = \ln \dfrac{1+x}{1-x} \big{|}_{x = 1/3}$，收敛更快
对于余项，由于不是直接通过Taylor公式推得，只能手动计算$n$项后所有幂函数的和
$$
\begin{aligned}
0 < R_n &= 2\left(\dfrac{1}{2n + 1} \dfrac{1}{3^{2n + 1}} + \dfrac{1}{2n + 3} \dfrac{1}{3^{2n + 3}} + \cdots\right) \\
&< \dfrac{2}{(2n + 1)3^{2n + 1}} \left(1 + \dfrac{1}{3^2} + \dfrac{1}{3^4} + \cdots\right) \\
&= \dfrac{1}{4(2n + 1) 3^{2n - 1}}
\end{aligned}
$$
# 收敛条件的充要版本是上极限
$$
\dfrac{1}{R} = \limsup_{n \to \infty} \sqrt[n]{|a_n|}
$$
# 表格积分法
[[Table Method for Integration by Parts]]
可用于简化部分的Fourier展开计算

