# Nernst 定理
实验观察发现，凝聚系的熵在等温过程中的改变在当这个过程的温度趋于绝对零度时趋于$0$, 即凝聚系在绝对零度进行的任何热力学过程中熵保持不变。

等温条件下化学反应的[[Free Energy#自由焓|Gibbs自由能变]]$\Delta G$和[[The First Law of Thermodynamics#焓|焓变]]$\Delta H$随着温度逐渐趋于$0$而趋于$0$

而对等温过程有
$$
G = H -TS\implies \Delta G = \Delta H - T \Delta S
$$
于是
$$
\lim_{T\to 0} \dfrac{\partial {(\Delta G-\Delta H)_T}}{\partial {T}} = \lim_{T \to 0} \dfrac{\partial {T(\Delta S)_T}}{\partial {T}} =0\implies \boxed{\lim_{T\to 0}(\Delta S)_T =0}
$$
即为*Nernst定理*

# 热力学第三定律
Nernst根据他的定理提出了*绝对零度不能达到原理*：**不可能通过有限多的步骤使得物体温度降低到绝对零度**

在绝对零度时，等温线与等熵线 (绝热线) 重合，又因为两条绝热线不相交，所以不可能通过可逆绝热过程使一个物体从$T≠ 0 \mathrm{K}$ 的状态达到绝对零度

绝对零度不能达到原理和Nernst定理是等效的，**它们是热力第三定律的两种不同表达**

## 热三定律的一些推论
- 温度趋于绝对零度时，热容趋于零
$$
C_y = \left( \dfrac{\mathrm{d} {Q}}{\mathrm{d} {T}} \right)_y = T\left( \dfrac{\partial {S}}{\partial {T}} \right)_y\to0  
$$
- 温度趋于绝对零度时，体膨胀系数趋于零(利用[[Maxwell Relationship]])
$$
\alpha =\dfrac{1}{V} \left( \dfrac{\partial {V}}{\partial {T}} \right)_p = -\dfrac{1}{V}\left( \dfrac{\partial {S}}{\partial {p}} \right)_T\to0  
$$
- 温度趋于绝对零度时，压强系数趋于零 
$$
\beta = \dfrac{1}{p}\left( \dfrac{\partial {p}}{\partial {T}} \right)_V = \dfrac{1}{p}\left( \dfrac{\partial {S}}{\partial {V}} \right)_T \to 0  
$$