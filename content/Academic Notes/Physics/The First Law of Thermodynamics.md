# 热力学过程
热力学系统从一个状态到另外一个状态的变化过程称为*热力学过程*, 简称*过程*
## 非静态过程
过程中系统经历了非平衡态
## 准静态过程
过程中的每一个时刻, 系统都可近似认为处于平衡态, 这是一种理想化的过程, 需要过程无限缓慢, 所以**不可能严格实现**

在理想条件下, 处理准静态过程时可始终采用平衡态的理论, **并忽略时间效应**

当过程变化的*特征时间*远大于系统的[[Temperature and Equilibrium State#平衡态|弛豫时间]]时, 该过程就可以近似地看作准静态过程, 比如说在气缸活塞上逐渐倒上沙子, 此时活塞应为压力变化对气体影响的特征时间约为$0.1\mathrm{s}$, 而气体系统从非平衡态达到平衡态的弛豫时间约为$0.001\mathrm{s}$, 因此可以近似为准静态过程

## 过程曲线
- 准静态过程中的每一时刻都可以用确定的状态参量来描述, 即对应于[[Phase Transition#相图|相图]]上的一个点；
- 准静态过程可以用相图上的一条有方向的曲线来表示；
- 准静态过程可分为: 等温过程、等压过程、等体过程、[[Processes of Ideal Gases#绝热过程|绝热过程]]和[[Processes of Ideal Gases#循环过程|循环过程]]

# 功
功是在热力学过程中, 系统和外界环境之间由于**力学效应**而产生的能量转移
## 体积功
**在无摩擦的情况下**, 系统体积改变$\mathrm{d} V$的微元过程中, 外界对系统所做的元功为（注意**负号**）
$$
\mathrm{d} W = - p \mathrm{d} V
$$
准静态过程中外界所做的功的数值, 不仅与该过程中系统地初态、终态有关, 还与从初态到终态的过程有关

**这里的$\mathrm{d} W$不是一个[[Differential of Multivariable Functions#全微分|全微分]]**, 因为它是一个过程量而不是状态量, 不能连续地变化, 这里的微分符号$\mathrm{d}$只是形式上地表示一个小量

体积功的实质是有规则的宏观运动（机械能）与无规则热运动（内能）之间的能量转换
> [!tip] 固体的体积功
> 一般地, 在数学上我们有
> $$\mathrm{d}V = \left( \frac{ \partial V }{ \partial T }  \right)_p \mathrm{d} T + \left( \frac{ \partial V }{ \partial p }  \right)_T \mathrm{d}p $$
> 且在恒温条件下
> $$\mathrm{d}V = \left( \frac{ \partial V }{ \partial p }  \right)_T \mathrm{d}p = -\kappa_TV \mathrm{d}p$$
> 故有
> $$W = -\int_1^2 p \mathrm{d}V = \int_{p_1}^{p_2} V \kappa_T p \mathrm{d}p$$
> 又因为[[Response Function#等温压缩系数|固体的等温压缩系数]]特别小, 所以过程中的体积可以近似为$V_1$, 于是就有
> $$W = \int_{p_1}^{p_2} V_1 \kappa_T p \mathrm{d}p = \dfrac{1}{2} V_1 \kappa_T(p_2^{2}-p_1^{2})$$
## 其他形式的功
### [[Liquid#表面性质|表面张力]]功
$$
\begin{gather}
F = 2\gamma l \\
\mathrm{d} W = 2\gamma l \mathrm{d} x = \gamma \mathrm{d} S
\end{gather}
$$
这里的$2$表示液体有两个表面的情况
### [[Electrostatic Field|电]]功
$$
\mathrm{d} W = V \mathrm{d} Q
$$
## 广义功
$$
\mathrm{d} W = \sum_{i} \mathrm{d} W_i,\quad \mathrm{d} W_i = Y_i \mathrm{d} x_i
$$
- $x_i$是[[Equation of State#广义坐标和物态方程的普遍形式|广义坐标]], 是广延量（整体是部分之和）
- $Y_i$是对应的*广义力*, 是强度量（整体和部分相同）

做功是系统和外界相互作用的一种形式, 当系统在广义作用力下有广义位移时, 就发生了某种类型的做功过程；在做功过程中, 外界和系统之间交换能量, 从而引起系统状态的变化

# 热量
热量是在热力学过程中, 外界环境与系统之间的**由于热学相互作用**而产生的**能量转移**
- 当系统和外界环境存在温差时,  通过热传导方式发生的能量转移
- 微观本质: 分子无规则热运动的能量从高温物体向低温物体传递

## 准静态过程中的热量
微元过程中, 外界传递给系统的热量$\mathrm{d} Q = C \mathrm{d} T$, 其中*热容*$C$依赖于过程, 如定体、定压等

## 功和热量的异同
相同: 都是过程量, 且都改变了系统能量

不同: 
1. 热量是系统和外界内能之间的能量传递, 而功是和外界其他形式能量之间的能量传递; 
2. 功是有规则整体运动的能量, 而热量是无规则热运动的能量； 
3. 功到热是有序到无序, 而热到功是从无序到有序的改变（见[[The Second Law of Thermodynamics#热力学第二定律的统计意义|热力学第二定律的统计意义]]）
# 内能
## 微观定义
一个热力学系统的内能是组成该系统微观粒子无规则热运动的动能和分子之间相互作用的势能的总和；不包含这个系统做整体运动的动能和在外场（如重力场）中的势能. 
$$
U = \sum_{i}\dfrac{1}{2}mv_i^2 + \sum_{i < j} u(\boldsymbol r_{ij})
$$
内能还包括化学能、电离能和原子核内部的核能, 但我们考虑的热力学过程一般不涉及化学反应, 物质的原子结构、核结构也不发生变化, 所以可以忽略不计

## 宏观定义
系统内能的增量等于绝热过程中外界对系统所做的功
$$
\Delta U = U_2 - U_1 = W_{\text{绝热}}
$$
## 性质
- 内能是状态函数（非过程函数）, 即独立状态参量的单值函数
- 理想气体的内能只是温度的单值函数, 与压强无关
- 内能是一个相对量, 其具体数值不重要, 实际有意义的是内能的变化量（同势能）
- 改变内能的两种方式: 做功和热传递

# 热力学第一定律
设经过某一过程（不要求是准静态过程）系统由平衡态$1$变到平衡态$2$, 系统内能的增量等于在此过程中外界对系统所传递的热量和外界对系统做功之和
$$
\mathrm{d} U = \mathrm{d} Q + \mathrm{d} W
$$
其中只有$\mathrm{d} U$是全微分
# 焓
在**定压过程**中
$$
(\Delta Q)_p = (\Delta U + p \Delta V)_p = [\Delta(U + pV)]_p
$$
定义状态函数*焓*
$$
\boxed{H = U + pV}
$$
则定压过程中**系统吸收的热量等于其焓的增量**

由此可以定义*定压热容*
$$
C_p = \lim_{\Delta T \to 0} \dfrac{(\Delta Q)_p}{\Delta T} = \lim_{\Delta T \to 0} \dfrac{(\Delta H)_p}{\Delta T} = \left(\dfrac{\partial {H}}{\partial {T}}\right)_p
$$
是一个状态函数

在实际应用中, 焓比内能更加实用, 这是因为
- 固体和液体的[[Response Function#压强系数|压强系数]]较大, 故实验上定压热容的测量要容易得多
- 地球表面上得物体一般都是处于确定得大气压下, 大部分工程技术或者化学反应等热力学过程都是在确定得压强下进行的
- 由定压热容和定体热容可以得出[[Processes of Ideal Gases#绝热过程|绝热指数]]$\gamma = \dfrac{C_p}{C_V}$
- 已经有大量物质在不同温度和压强下的焓值数据. 
# 理想气体的内能、焓和热容
由[[Equipartition Theorem#多原子分子理想气体的内能和热容|能量均分定理]], 我们知道理想气体内能为$U = \dfrac{t + r + 2s}{2} \nu RT = U(T)$, 由此可以推出理想气体焓: $H = U + pV = U(T) + \nu RT = H(T)$

> [!Tip] 焦耳定律
> 理想气体的内能和焓都是状态函数, 它们仅与温度有关, 与体积、压强无关

理想气体的热容: 
$$
\begin{aligned}
C_V = \dfrac{t + r + 2s}{2} \nu R &\implies U = C_V T \\
C_p = C_V + \nu R &\implies H = C_pT
\end{aligned}
$$
和[[Processes of Ideal Gases#绝热过程|绝热指数]]
$$
\gamma = \dfrac{C_p}{C_V} = \dfrac{C_V + \nu R}{C_V}
$$
# 一般气体的内能
## 内能公式
由[[The Second Law of Thermodynamics#Carnot定理|Carnot定理]]可以推得*内能公式*
$$
\left(\dfrac{\partial U}{\partial V}\right)_T = T \left(\dfrac{\partial p}{\partial T}\right)_V - p
$$
也就是说可以直接从状态方程$f(p,V,T)$的形式在推导出$\left( \frac{ \partial U }{ \partial V } \right)_T$
## Van der Waals气体的内能
通过内能公式可计算[[Van der Waals Equation of State|Van der Waals气体]]的内能
$$
\left( \dfrac{\partial {U}}{\partial {V}} \right) = \dfrac{a\nu^2}{V}  \implies \mathrm{d} U = \left( \dfrac{\partial {U}}{\partial {T}} \right) \mathrm{d} T + \left( \dfrac{\partial {U}}{\partial {V}} \right) \mathrm{d} V = C_V\mathrm{d} T + \dfrac{a\nu^2}{V^2} \mathrm{d} V 
$$
于是
$$
U = \int_{T_0}^T C_V\mathrm{d} T + U_0 - \dfrac{a\nu^2}{V}
$$
