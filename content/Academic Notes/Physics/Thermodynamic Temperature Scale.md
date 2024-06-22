# 热力学温标
回忆[[The Second Law of Thermodynamics#Carnot定理|Carnot定理]], 工作于两个恒温热源之间的可逆热机，其效率只跟热源的温度有关，而与工作物质或所做的功的大小无关；故其效率是两个温度$\theta_1,\theta_2$的普适函数
$$
\eta = 1-\dfrac{Q_2}{Q_1} \implies \dfrac{Q_2}{Q_1} = 1-\eta=f(\theta_1,\theta_2)
$$
考虑下图所示热机
![[热学-热力学温标推导.png]]
则有
$$
\dfrac{Q_1}{Q_3} = f(\theta_3,\theta_1),\; \dfrac{Q_2}{Q_3}=f(\theta_3,\theta_2)
$$
于是有
$$
\dfrac{Q_2}{Q_1} = \dfrac{Q_2/Q_3}{Q_1/Q_3} \implies f(\theta_1,\theta_2) = \dfrac{f(\theta_3,\theta_2)}{f(\theta_3,\theta_1)}
$$
因为$\theta_3$是一个独立变量，则普适函数$f$可写成
$$
f(\theta_1,\theta_2) = \dfrac{\Psi(\theta_2)}{\Psi(\theta_1)} = \dfrac{Q_2}{Q_1}
$$
由此可定义温标$T = A\Psi(\theta)$，其中$A$为与温度无关的常数，则有
$$
\dfrac{T_2}{T_1} = \dfrac{\Psi(\theta_2)}{\Psi(\theta_1)} = \dfrac{Q_2}{Q_1}
$$
该温标是建立在热力学第二定律的基础上、不依赖于具体测温物质的普适温标，称为*热力学温标*或*绝对温标*，单位为*开尔文*$\mathrm{K}$，固定点为水的三相点$273.16\mathrm{K}$

由此，如果我们已经知道一个温度$T_0$，要测量温度$T$，就可以构造一个工作在其中的一个Carnot热机来测量吸热和放热的比值，从而得到$T$和$T_0$的比值
