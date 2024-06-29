# 光吸收的线性规律
令单色平行光束沿$x$方向通过均匀介质. 设光的强度在经过厚度为$\mathrm{d} x$的一层介质时强度由$I$减为$I - \mathrm{d} I$. 实验表明，在相当广阔的光强范围内，有
$$
-\mathrm{d} I = \alpha I \mathrm{d} x
$$
式中$\alpha$是一个与光强无关的比例系数，称为该物质的*吸收系数*

为了求出光束穿过厚度为$l$的介质后强度的改变，只需把上式改写为
$$
\dfrac{\mathrm{d}I}{I} =-\alpha\mathrm{d} x
$$
积分就有
$$
\begin{aligned}
\ln(\dfrac{I}{I_0})  & = -\alpha l \\
\implies I  & = I_0\mathrm{e}^{-\alpha l}
\end{aligned}\tag{1}
$$
式子中$I_0$和$I$分别代表$x=0,l$处的光强，$\alpha$的量纲是长度的倒数. 上式被称为*Bouguer定律*或者*Lambert定律*

线性吸收规律在激光发明之前是相当精确的，但是如果光强很强，光的非线性性质就会呈现出来，这个领域称为*非线性光学*

# 复数折射率的意义
透明介质折射率的本意是$n = \dfrac{c}{v}$，而在介质中沿$x$方向传播的平面电磁波中的电场强度可写作如下形式
$$
\widetilde{E} = \widetilde{E}_0 \exp \left[ -\mathrm{i} (\omega t-\dfrac{x}{v}) \right] = \widetilde{E}_0\exp \left[ -\mathrm{i} \omega(t-\dfrac{nx}{c}) \right] 
$$
这里的$n$是实数，电磁波不随距离衰减。如果我们形式地把折射率看作是复数，并且记作
$$
\widetilde{n} = n(1 + \mathrm{i}\kappa)
$$
其中$n$和$\kappa$都是实数，则上式化为
$$
\widetilde{E} = \widetilde{E}_0 \exp \left[ -\mathrm{i}\omega(t-\dfrac{\widetilde{n}x}{c}) \right] = \widetilde{E}_0\exp \left( -\dfrac{n\kappa \omega x}{c} \right) \exp \left[ -\mathrm{i}\omega(t-\dfrac{nx}{c}) \right] \tag{2}
$$
而光强为
$$
I \propto \widetilde{E} ^ * \widetilde{E} =  \left|E_0\right|\exp \left( \dfrac{2n\kappa \omega x}{c} \right) 
$$
故这个式子表示一个随距离$x$衰减的平面波，故称$\kappa$为*衰减系数*. 比较$(2)$式和$(1)$式就有
$$
\alpha = \dfrac{2n\kappa \omega}{c} = \dfrac{4\pi n\kappa}{\lambda}
$$
# 光的吸收和波长的关系
若物质对各种波长$\lambda$的吸收程度几乎相等，即吸收系数$\alpha$和$\lambda$无关，则称为*普遍吸收*. 在**可见光的范围内的普遍吸收**意味着**光束通过介质后只改变强度，不改变颜色**. 例如空气、纯水，无色玻璃等介质都在可见光范围内产生普遍吸收

若物质对某些波长的光的吸收特别强烈，则成为*选择吸收*，对可见光进行选择吸收，会使白光变成彩色光。**绝大部分物体呈现彩色，都是其表面活体内对可见光进行选择吸收的结果**

对于广谱的电磁波而言，不存在普遍吸收的物质，实际上选择吸收才是物质和光相互作用的普遍规律

# 吸收光谱
令具有*连续谱*的光（白光）通过吸收物质后再经过光谱仪分析，可形成*吸收光谱*。对于同一物质而言，**其发射光谱中的亮线**和**吸收光谱中的暗线**是一一对应的，也就是说，**某种物质自身发射哪些波长的光，他就强烈地吸收哪些波长的光**

太阳的吸收光谱中的暗线被称为*Fraunhofer谱线*，用字母$\mathrm{A,B,C,\cdots}$表示. 把这些吸收谱线的波长和地球上已知物质发射原子光谱对比以下，就可以知道太阳表面层中包含哪些元素


