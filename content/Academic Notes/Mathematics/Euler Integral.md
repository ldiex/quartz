# Gamma函数
定义$\Gamma$函数
$$
\Gamma(s) = \int_0^{+\infty} x^{s-1}e^{-x}\mathrm{d} x
$$
这个函数可以被写成两个积分之和
$$
\Gamma(s) = \int_0^1 x^{s-1}e^{-x} \mathrm{d} x + \int_1^{+\infty} x^{s-1}e^{-x} \mathrm{d} x = \Phi(s) + \Psi(s)
$$
其中$\Phi(s)$在$s\ge 1$时是正常积分, 在$0<s<1$时是收敛的无界函数的反常积分（由[[Improper Integrals#比较原则|Cauchy判据]]）
$\Psi(s)$当$s>0$时也是收敛的无穷限反常积分（由[[Improper Integrals#比较原则|Cauchy判据]]）
所以$\Gamma(s)$在$\mathbb{R}^+$上收敛, 规定其定义域为$s>0$
## Gamma函数的性质
1. $\Gamma(s)$在$(0,+\infty)$上连续可导
$$
\begin{aligned}
\Gamma'(s)  & = \int_0^{+\infty} x^{s-1}e^{-x}\ln x \mathrm{d} x \\
\Gamma^{(n)}(s)   & =\int_0^{+\infty} x^{s-1} (\ln x)^n\mathrm{d} x \\
\end{aligned}
$$
2. 满足递推公式
$$
\Gamma(s+1) = s\Gamma(s)
$$
特别地, 当$s = n \in \mathbb{N}^*$时, 有$\Gamma(n + 1) = n!$
3. 图像（利用递推公式延拓定义域后）
![[数学-Gamma函数图像.png]]
# Beta函数
定义$B$函数
$$
B(p,q) = \int_0^1x^{p-1}(1-x)^{q-1}\mathrm{d} x
$$
同样由函数的收敛性, 规定定义域为$p,q>0$
## Beta函数的性质
1. $B(p,q)$在$\mathbb{R}^+ \times \mathbb{R}^+$上连续
2. 对称性$B(p,q) = B(q,p)$
3. 递推公式
$$
\begin{aligned}
B(p,q)  & = \dfrac{q-1}{p+q-1}B(p,q-1) \\
B(p,q)  & =\dfrac{p-1}{p+q-1}B(p-1,q) \\
\implies   B(p,q) &=\dfrac{(p-1)(q-1)}{(p+q-1)(p+q-2)}
\end{aligned}
$$
4. 常见的其他形式
令$x = \cos^2 \phi$, 就有
$$
B(p,q) = 2\int_0^{\pi/2} \sin^{2q-1}\phi \cos^{2p-1}\phi\mathrm{d} \phi
$$
令$x = \dfrac{y}{1+y}$, 就有
$$
B(p,q) = \int_0^{+\infty} \dfrac{y^{p-1}}{(1+y)^{p+q}} \mathrm{d} y
$$
设$y = \dfrac{1}{t}$, 我们有
$$
\int_1^{+\infty} \dfrac{y^{p-1}}{(1+y)^{p+q}} \mathrm{d} y + \int_1^0 \dfrac{t^{q-1}}{(1+t)^{p+q} }=0
$$
可以得出更对称的形式
$$
B(p,q) = \int_0^1\dfrac{y^{p-1}+y^{q-1}}{(1+y)^{p+q}}
$$
# Gamma函数和Beta函数之间的关系
## 关系公式
$$
B(p,q) = \dfrac{\Gamma(p)\Gamma(q)}{\Gamma(p+q)}
$$


## 应用: 计算$\Gamma(1/2)$
考虑
$$
B(a,1-a) = \dfrac{\Gamma(a)\Gamma(1-a)}{\Gamma(1)} = \Gamma(a)\Gamma(1-a)
$$
即
$$
\int_0^{+\infty} \dfrac{y^{a-1}}{1+y} \mathrm{d} y = \Gamma(a)\Gamma(1-a)
$$
取$a =\dfrac{1}{2}$就有
$$
\Gamma(\dfrac{1}{2}) = \sqrt{ \int_0^{+\infty} \dfrac{x^{-1/2}}{1+x}\mathrm{d} x } = \sqrt{ \int_0^{+\infty} \dfrac{2\mathrm{d} t}{(1+t^2)} } = \sqrt{ \pi }
$$
又因为
$$
\Gamma(s) = \int_0^{+\infty} x^{s-1}e^{-x}\mathrm{d} x = 2\int_0^{+\infty} t^{2s-1}e^{-t^2} \mathrm{d} t
$$
取$s = \dfrac{1}{2}$就有
$$
\boxed{\int_0^{+\infty} e^{-x^2}\mathrm{d} x = \dfrac{\sqrt{ \pi }}{2}}
$$

## 应用: 计算Wallis积分
回忆[[Mathematical Analysis 23 Fall Final#Wallis 积分|Wallis积分]]
$$
\int_0^{\pi/2} \sin^n x \mathrm{d} x= \begin{cases}
\dfrac{(n - 1)!!}{n!!} \cdot \dfrac{\pi}{2} &, \text{$n$为偶数} \\
\dfrac{(n - 1)!!}{n!!} &, \text{$n$为奇数}
\end{cases}
$$
考虑
$$
\begin{aligned}
\int_0^{\pi/2} \sin^{2n+1}x\mathrm{d} x  & = \int_0^{\pi/2} \sin^{2(n+1)-1}\phi\cos^{2(1/2)-1}\phi\mathrm{d} \phi \\
 & =\dfrac{1}{2 }B(n+1, \dfrac{1}{2}) = \dfrac{1}{2}\dfrac{\Gamma(n+1)\Gamma(\dfrac{1}{2})}{\Gamma(n+\dfrac{3}{2})} \\
 & = \dfrac{1}{2} \dfrac{n!\sqrt{ \pi }}{(n+\dfrac{1}{2})\Gamma(n+\dfrac{1}{2})} \\
 & = \dfrac{1}{2} \dfrac{n!\sqrt{ \pi }}{(n+\dfrac{1}{2})(n-\dfrac{1}{2})(n-\dfrac{3}{2})\cdots(\dfrac{1}{2})\sqrt{ \pi }} \\
 & =\dfrac{1}{2}\dfrac{n!\cdot 2^{n+1}}{(2n+1)!!} = \dfrac{(2n)!!}{(2n+1)!!}
\end{aligned}
$$
得到奇数的情况, 同理也可以计算出偶数的情况

