# Stefan-Boltzmann定律
黑体的[[Radiometry#辐射本领|辐射本领]]和温度的四次方成正比
$$
R = \sigma T^4,\quad \sigma = 5.67\times10^{-8} \mathrm{W\cdot m^{-2}\cdot K^{-4}}
$$
# Wein位移定律
黑体辐射中最强辐射的波长和温度成反比
$$
\lambda_m T = b,\quad b = 2898 \mathrm{\mu m\cdot K}
$$
# Planck黑体辐射定律
在任意温度$T$下，从一个黑体中发射出的电磁辐射的辐射率是频率$\nu$的函数
$$
L_{\nu} (\nu, T) = \dfrac{2h\nu^3}{c^{2}} \dfrac{1}{\exp(\dfrac{h\nu}{k_BT})-1}
$$
其中$L_\nu$是[[Radiometry#光谱辐射率(Spectral radiance)|光谱辐射率]]，$k_B$是[[Introduction to Molecular Dynamics Theory#温度的微观解释|Boltzmann常数]]，或者写成波长的函数
$$
L_\lambda(\lambda,T) = \dfrac{2hc^{2}}{\lambda^5} \dfrac{1}{\exp(\dfrac{hc}{\lambda k_BT})-1}
$$
注意这两个函数具有不同的单位：第一个函数是描述单位频率间隔内的辐射率，而第二个则是单位波长间隔内的辐射率. 因而它们不等价且有如下关系
$$
I_\nu (\nu,T) \mathrm{d}\nu = -I_\lambda (\lambda,T) \mathrm{d}\lambda
$$
通过单位频率间隔和单位波长间隔之间的关系，这两个函数可以相互转换
$$
\mathrm{d} \nu = \mathrm{d}\left( \dfrac{c}{\lambda} \right)  = c\mathrm{d}(\dfrac{1}{\lambda})=-\dfrac{c}{\lambda^{2}} \mathrm{d}\lambda
$$
