# 二元函数的极限
例如，计算
$$
\lim_{ (x, y) \to (0,\infty)} \left(1 + \dfrac{1}{x}\right)^{\dfrac{x^2}{x+y}}
$$
不能直接代入$y = 0$，而是应该令$t = \dfrac{1}{x}$且用万能公式代换
$$
\ln(\text{原式}) = \lim_{ (t, y) \to (0,0) } \dfrac{\ln(1 + t)}{t(1 + yt)} 
$$
之后使用Taylor展开
> [!Note] 求多元函数极限的方法
> 1. 定义 (绝对值放缩)
> 2. Taylor 展开 (等价无穷小)
> 3. 趋于$(0, 0)$：极坐标换元$x = r\sin \theta; y = r \sin \theta$
> 4. 猜极限为$0$：夹逼

# 介值定理依赖的是连通性
# 求偏导的值$f_x(x_0, y_0)$可以先代入$y = y_0$再求导

