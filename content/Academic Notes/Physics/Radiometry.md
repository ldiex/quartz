# 辐射能(Radiant Energy)
符号为$Q$, 单位为$\mathrm{J}$, 表示辐射具有的能量大小

# 辐射通量(Radiant Flux)
每单位时间内的辐射能量, 也称作*辐射功率*
$$
\Phi = \frac{ \mathrm{d} Q }{ \mathrm{d} t } 
$$
单位为$\mathrm{W}$, 对照[[Introduction to Photometry#辐射能通量和光通量|光通量]]
# 辐射本领
即从物体单位面积发出的辐射通量
$$
R = \dfrac{\Phi}{S}
$$
又称为*辐射出射度（Radiant Exitance）*, 单位为$\mathrm{W\cdot m^{-2}}$

# 辐射强度(Radiant Intensity)
即每单位立体角的辐射通量
$$
I = \frac{ \mathrm{d} \Phi }{ \mathrm{d} \Omega } 
$$
对照[[Introduction to Photometry#发光强度|发光强度]]
设光子单位时间内发射出光子的数密度为$N$, 光子能量为$h\nu$, 则有如下关系成立
$$
I = N h \nu
$$
# 辐射率(Radiance)
即每单位立体角每单位投射表面的辐射通量
$$
B = \dfrac{\mathrm{d} I}{\mathrm{d} S \cos \theta} = \dfrac{{\mathrm{d}}^2 \Phi}{\mathrm{d} \Omega \mathrm{d} S \cos\theta}
$$
对照[[Introduction to Photometry#亮度|亮度]]

# 辐照度(Irradiance)
表述单位入射表面接受到的辐射通量
$$
E = \frac{ \mathrm{d} \Phi' }{ \mathrm{d} S' } 
$$
对照[[Introduction to Photometry#照度|照度]]

# 光谱辐射率(Spectral radiance)
即在辐射谱中每单位波长的辐射率
$$
L_{\lambda} = \frac{ \mathrm{d} B }{ \mathrm{d} \lambda } 
$$
或者是单位频率的辐射率
$$
L_\nu = \frac{ \mathrm{d} B }{ \mathrm{d} \nu } 
$$