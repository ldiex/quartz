# 第一型曲线积分
设$\ell$是平面上可求长度的曲线段, $f(x,y)$为定义在$\ell$上的函数. 对曲线$\ell$作*分割*$T$, 它把$\ell$分成$n$个可求长度的小曲线段$\ell_i$, 其弧长为$\Delta s_i$, 分割的*细度*为$\Vert T\Vert = \max \Delta s_i$, 在$\ell_i$上取一点$(\xi_i,\eta_i)$, 若有极限
$$
\lim_{\Vert T \Vert \to 0} \sum_{i = 1}^n f(\xi_i,\eta_i)\Delta s_i = J
$$
且$J$的值和分割$T$及$(\xi_i,\eta_i)$的取法无关, 则称该极限为$f$在$\ell$上的第一型曲线积分, 记作
$$
\int_\ell f(x,y) \mathrm{d} s
$$
## 第一型曲线积分的计算
设光滑曲线$\ell$的参数方程为
$$
\ell:\begin{cases}
x = \phi(t) \\
y = \psi(t)
\end{cases}
\quad t\in [\alpha,\beta]
$$
且$f(x,y)$为定义在$\ell$上连续函数, 则有
$$
\int_\ell f(x,y)\mathrm{d} s = \int_\alpha^\beta f(\phi(t),\psi(t))  \sqrt{ \phi'^2(t) + \psi'^2(t) } \mathrm{d} t
$$
当曲线$\ell$可以用$y = \psi(x),\quad x\in[a,b]$来表示且$\psi(t)$存在连续的导函数时, 上式简化为
$$
\int_\ell f(x,y)\mathrm{d} s = \int_a^b f(x,\psi(x)) \sqrt{ 1+\psi'^2(x) } \mathrm{d} x
$$
# 第二型曲线积分
即定义在有向曲线上的向量的积分
$$
\int_{\ell} \boldsymbol F \cdot \mathrm{d} {\boldsymbol s} = \int_{\ell} F_x(x,y)\mathrm{d} x + F_y(x,y)\mathrm{d} y
$$
可以通过点乘的定义来转化成第一型曲线积分

## 第二型曲线积分的计算
设光滑曲线$\ell$的参数方程为
$$
\ell:\begin{cases}
x = \phi(t) \\
y = \psi(t)
\end{cases}
\quad t\in [\alpha,\beta]
$$
且$\boldsymbol F(x,y)$为定义在$\ell$上的连续向量函数, 则有
$$
\int_\ell \boldsymbol F(x,y)\mathrm{d} {\boldsymbol s} = \int_\alpha^\beta F_x(\phi(t),\psi(t)) \phi'(t)\mathrm{d} t + F_y(\phi(t),\psi(t)) \psi'(t)\mathrm{d} t
$$

