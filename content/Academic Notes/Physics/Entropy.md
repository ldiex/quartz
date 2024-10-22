# 熵的引入
回忆[[The First Law of Thermodynamics#广义功|广义功]]的定义
> [!Note]
> $$
> \mathrm{d} W = \sum_{i} \mathrm{d} W_i,\quad \mathrm{d} W_i = Y_i \mathrm{d} x_i
> $$
> - $x_i$是广义坐标, 是广延量（整体是部分之和）
> - $Y_i$是对应的广义力, 是强度量（整体和部分相同）

做功过程中系统与外界的广义力差是系统状态（广义坐标）发生改变的“动力”和“原因”, 而广义坐标的改变是“位移”和“结果”

热传递的“动力”和“原因”是温度差, 类比有
$$
\mathrm{d} Q = T \mathrm{d} S
$$
**熵的改变量是热传导过程中系统在温差作用下的“位移”和“结果”**

# Clausius等式和不等式
由[[The Second Law of Thermodynamics#Carnot定理|Carnot定理]]可知, Carnot热机的效率为
$$
\eta = 1 - \dfrac{\left|{Q_2}\right|}{\left|{Q_1}\right|} \le 1 -\dfrac{T_2}{T_1}
$$
其中等号在热机可逆的时候取到
可推广至对于任意循环过程, 热温比的总和小于等于$0$
$$
\oint \dfrac{\mathrm{d} Q}{T} \le 0
$$
当循环过程可逆时取等号, 此时为*Calusius等式*, 取不等号时为*Calusius不等式*

# 熵的宏观定义
对于**可逆循环**, 由于热温比的积分和路径无关, 由此可定义对应的势能（状态函数）, 称为*熵*$S$使得
$$
\int_i^t \dfrac{\mathrm{d} Q}{T} = S_t - S_i
$$
# 熵变计算
上式可计算**可逆过程中**任意两个状态间给定路径的*熵变*, 利用[[The First Law of Thermodynamics|热力学第一定律]]和[[The First Law of Thermodynamics#内能公式|内能公式]], 可得
$$
\begin{aligned}
\mathrm{d} S = \dfrac{\mathrm{d} Q}{T} = \dfrac{\mathrm{d} U + p \mathrm{d} V}{T}  & =\dfrac{C_V\mathrm{d} T +\left( \dfrac{\partial {U}}{\partial {V}} \right)_T\mathrm{d} V + p\mathrm{d} V }{T}  \\
 & = \dfrac{C_V}{T}\mathrm{d} T +\dfrac{1}{T}\left[ \left( \dfrac{\partial {U}}{\partial {V}} \right)_T + p \right] \mathrm{d} V  \\
 & = \dfrac{C_V}{T}\mathrm{d} T+ \left( \dfrac{\partial {p}}{\partial {T}} \right) \mathrm{d} V 
\end{aligned}
$$
即
$$
\Delta S = \int_i^t \left[ \dfrac{C_V}{T}\mathrm{d} T + \left( \dfrac{\partial {p}}{\partial {T}} \right)_V \mathrm{d} V \right] 
$$
## 理想气体的熵变
$$
pV = \nu RT \implies \left( \dfrac{\partial {p}}{\partial {T}} \right)_V = \dfrac{\nu R}{V} 
$$
于是
$$
\Delta S = \int_{(T_0, V_0)}^{(T_1, V_1)} \left[ C_V \dfrac{\mathrm{d} T}{T} + \nu R \dfrac{\mathrm{d} V}{V} \right] = C_V \ln \dfrac{T}{T_0} + \nu R\ln \dfrac{V}{V_0}
$$
# 熵增加原理
对于**一般过程**, 有
$$
\Delta S = S_t - S_i \ge \int_i^t \dfrac{\mathrm{d} Q}{T}
$$
考虑[[Processes of Ideal Gases#绝热过程|绝热过程]], 有$\mathrm{d} Q = 0$, 故此时$\Delta S \ge 0$
> [!Note] 熵增加原理
> 当热力学系统从一平衡态经**绝热**过程到达另一个平衡态时, 它的**熵永不减少**. 如果过程是**可逆**的, 则其**熵不变**；如果过程是**不可逆**的, 则其**熵增加**

- 熵增加原理**只适用于绝热过程**, 不适用于其它过程；熵增加原理**只适用于孤立系统**, 不适用于开放系统；
- 如果一个准静态过程可逆但是不绝热, 该过程中系统的熵可以增加、减少, 也可以不变；
- 熵增加原理是孤立系统中绝热过程是否可逆的判据；
- 熵增加原理是孤立系统中绝热过程自发进行方向的判据；
- 熵增加原理是[[The Second Law of Thermodynamics#热力学第二定律|热力学第二定律]]在孤立系统中的一种表述. 
> [!Tip] Clausius不等式 vs 熵增加原理
> - Calusius描述的是对于任意循环过程, 其回到原状态后, 热温比的和也就是熵变始终大于等于零
> - 熵增加原理表述的是对于任意绝热过程（不需要回到原点）, 过程中系统的熵变也始终大于等于零
> - 二者都在过程可逆的时候熵变取零

# 特殊过程的分析
## 理想气体自由膨胀
因为自由膨胀是不可逆过程, 故无法直接计算熵变, 所以我们需要假设一个等效的过程来辅助计算. 

考虑理想气体由体积$V_1$自由膨胀到$V_2$, 过程中$Q=W=\Delta U = 0$且温度不变, 设一个**等温膨胀**过程连接其初态和终态. 

由[[Entropy#理想气体的熵变|理想气体的熵变公式]]可直接得到$\Delta S = \nu R \ln \dfrac{V_2}{V_1}$, 可知不可逆的自由膨胀过程中熵是增加的
## 热传导过程
一绝热容器被**一固定的导热隔板分成两部分**, 分别盛有热容为常量$C_1$, $C_2$, 温度为$T_1$, $T_2$ 的理想气体；经足够长时间后, 两部分气体达到热平衡, 求该过程中的总熵变

同样地, 有限温差的热传递过程为非静态 (不可逆) 过程, 不能直接计算熵变, 所以我们设计两个可逆的热传递过程, 使两部分气体分别由其初始温度缓慢地向它们的热平衡温度$T$过渡

**能量守恒**: $C_1\mathrm{d} T_1 + C_2 \mathrm{d} T_2 = 0 \implies C_1T_1 + C_2T_2 = \text{const} = (C_1+C_2)T$
其中$T$为平衡后系统温度
$$
T = \dfrac{C_1T_1+C_2T_2}{C_1+C_2}
$$
**熵的改变量**: 
$$
\mathrm{d} S = \mathrm{d} S_1 + \mathrm{d} S_2 = C_1 \dfrac{\mathrm{d} T_1}{T_1} + C_2 \dfrac{\mathrm{d} T_2}{T_2}
$$
则有
$$
\Delta S = C_1\ln \dfrac{T}{T_1} + C_2 \ln \dfrac{T}{T_2}
$$
## 理想气体混合过程
这是一个准静态过程, 可直接利用[[Entropy#理想气体的熵变|理想气体的熵变公式]], 由每个气体组分的体积有由$V_i$增大为$V$得到
$$
\Delta S= \sum_i \nu_i R \ln \dfrac{V}{V_i}
$$
## 理想气体可逆绝热过程
利用[[Processes of Ideal Gases#绝热过程|绝热过程公式]]和[[Entropy#理想气体的熵变|理想气体的熵变公式]]
$$
\Delta S = C_V \ln \dfrac{T}{T_0} + \nu R\ln \dfrac{V}{V_0} = C_V(1-\gamma) \ln \dfrac{V_2}{V_1} + \nu R \ln \dfrac{V_2}{V_1}
$$
# 和热力学第二定律的关系
## [[The Second Law of Thermodynamics#Clausius表述|Clausius表述]]
设某个时刻, 两个物体的温度分别为$T_1,T_2$, 并分别吸热$\mathrm{d} Q_1, \mathrm{d} Q_2$, 则有
$$
\mathrm{d} Q_1 + \mathrm{d} Q_2 = 0 
$$
于是系统的熵变
$$
\mathrm{d} S = \dfrac{\mathrm{d} Q_1}{T_1} + \dfrac{\mathrm{d} Q_2}{T_2} = \left( \dfrac{1}{T_1}-\dfrac{1}{T_2} \right)  \mathrm{d} Q_1
$$
令$\mathrm{d} S \ge 0$则得到若$\mathrm{d}Q_1$为正则必须有$T_1 < T_2$, 即为Clausius表述, 由Clausius表述也可推出$\mathrm{d} S \ge 0$, 故**两者等价**
## [[The Second Law of Thermodynamics#Kelvin表述|Kelvin表述]]
假设第二类永动机存在, 则每经过一个循环的能量转换效果是$Q_1\to W$, 这里热源放热$Q_1$即吸热$-Q_1$, 得到热源的熵变$\Delta S_1$
$$
\Delta S_1 = -\dfrac{Q_1}{T_1} = -\dfrac{W}{T}
$$
而因为工质需要复原, 其熵变为$\Delta S_2 = 0$；又因为热机装置中重物升高, 为有序运动, 则它的熵变为$\Delta S_3 =0$, 于是便有$\Delta S = \Delta S_1 +\Delta S_2 +\Delta S_3 < 0$

这和熵增加原理矛盾. 如果熵增加原理不成立, 则第二类永动机也可以存在, 所以这两者也是等价的
# 微观熵
回忆[[The Second Law of Thermodynamics#热力学第二定律的统计意义|热力学第二定律的统计意义]], 我们可以定义*微观熵*, 或*Boltzmann熵*, 其表达式为
$$
S_B = k_B \ln \Omega
$$
其中$\Omega$为*热力学概率*, 即**宏观态对应的微观态的数目**, $k_B$为[[Introduction to Molecular Dynamics Theory#温度的微观解释|Boltzmann常数]]

对于理想气体, $\Omega(A + B) = \Omega(A)\Omega(B)$, 熵是一个*广延量*

可以证明, **微观熵和宏观熵是等价的**, 由此可知, 孤立系统中的自发不可逆过程实质上是系统由一个概率较小的状态向概率较大状态过渡, 最终到达概率最大的终态平衡态；所以孤立系统的不可逆绝热过程中, 系统的熵增加. 

