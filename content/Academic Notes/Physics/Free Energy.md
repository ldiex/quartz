# 自由能
由[[Entropy#熵增加原理|熵增加原理]]和[[The First Law of Thermodynamics|热力学第一定律]]，对于任意过程我们有
$$
T \mathrm{d} S \ge \mathrm{d} Q = \mathrm{d} U - \mathrm{d} W
$$
其中等号在过程可逆时取到

由此我们定义*Helmholtz自由能*
$$
F = U-TS
$$
有
$$
\mathrm{d} F = \mathrm{d} U - T\mathrm{d} S - S\mathrm{d} T \le -S \mathrm{d} T + \mathrm{d} W
$$
> [!Tip] 最大功原理
> 在等温过程中，根据上述不等式我们得到系统对外做功$W'=-W \leq -\Delta F$**有一个极限**，该极限为过程中系统自由能的减小量

这说明了系统对外做功的能量只能从Helmholtz自由能$F$中来，故我们考虑内能$U = F+TS$. 定义其中$F$是可以对外做功的*自由能*；另一部分能量 ($TS$) 则是不能向外输出的能量，即*束缚能*

$TS$为*贬值的能量*，即**无用能**；**熵增加加剧能量的贬值**。

## 等温等体条件下过程进行的方向
此时有$\mathrm{d}T = \mathrm{d}W = 0$，于是我们有
$$
\mathrm{d} F \le 0
$$
这说明了**等温等体过程总是沿着自由能不增加的方向进行的**，称为*自由能减少原理*。

# 自由焓
定义*Gibbs自由能*，又称*自由焓*为
$$
G = F + pV = U-TS + PV = H - TS
$$
其中$H$为[[The First Law of Thermodynamics#焓|焓]]，由于$\mathrm{d} F \le -S\mathrm{d} T + \mathrm{d} W$，故我们有
$$
\begin{aligned}
\mathrm{d} G = \mathrm{d}(F+pV) = \mathrm{d}F + p \mathrm{d}V + V \mathrm{d}p\le -S\mathrm{d} T + V\mathrm{d} p + \mathrm{d} W +p\mathrm{d}V
\end{aligned}
$$
把外界对系统做的功$\mathrm{d}W$分成体积功$-p\mathrm{d}V$和非体积功$\mathrm{d}\widetilde{W}$，即$\mathrm{d} W = -p\mathrm{d}V + \mathrm{d}\widetilde{W}$，我们有
$$
\mathrm{d}G \leq -S \mathrm{d}T + V \mathrm{d}p + \mathrm{d}\widetilde{W}
$$
> [!Tip] 最大非体积功
> 在等温等压过程中，系统对外所做的非体积功$\widetilde{W}' = -\widetilde{W} = -\Delta G$**有一个极限**，该极限为过程中系统的自由焓的减小量

考虑焓$H = G + TS$; 其中$G$是可以对外做非体积功的*自由焓*；另一部分能量 ($TS$) 则是不能向外输出的能量，即*束缚能*

## 等温等压条件下过程进行的方向
在系统温度和压强都固定，且除体积功外无其它形式的功的条件下，过程进行方向的判据为
$$
\mathrm{d} G \le 0
$$
称为*自由焓减少原理*，过程达到平衡的判据为$\mathrm{d} G = 0$， 即自由焓达到最小值

> [!Summary] 小结
> - 自由能又称*Helmholtz自由能*，表示**等温过程中**系统对外**做功**的能力，**等温等体过程**总是朝着它**减小**的方向进行的
> - 自由焓又称*Gibbs自由能*，表示**等温等压过程**中系统对外**做非体积功**的能力，**等温等压过程**总是朝着它**减小**的方向进行的

