# 自由能
由[[Entropy#熵增加原理|熵增加原理]]和[[The First Law of Thermodynamics|热力学第一定律]]
$$
T \mathrm{d} S \ge \mathrm{d} Q = \mathrm{d} U - \mathrm{d} W
$$
由此定义*Helmholtz自由能*
$$
F = U-TS
$$
有
$$
\mathrm{d} F = \mathrm{d} U - T\mathrm{d} S - S\mathrm{d} T \le -S \mathrm{d} T + \mathrm{d} W
$$
> [!Tip] 最大功原理
> 在等温过程中，系统对外做功$W'=-W$有一个极限，该极限为过程中系统自由能的减小量

内能$U = F+TS$. 其中$F$是可以对外做功的*自由能*；另一部分能量 ($TS$) 则是不能向外输出的能量，即*束缚能*

$TS$为*贬值的能量*，即无用能；熵增加加剧能量的贬值。

## 等温等体条件下过程进行的方向
判据为
$$
\mathrm{d} F \le 0
$$
等温等体过程总是沿着自由能不增加的方向进行的，称为*自由能减少原理*。

# 自由焓
定义*Gibbs自由能*，又称*自由焓*为
$$
G = F + pV = U-TS + PV = H - TS
$$
其中$H$为[[The First Law of Thermodynamics#焓|焓]]
$$
\mathrm{d} F \le -S\mathrm{d} T + \mathrm{d} W \implies \mathrm{d} G\le -S\mathrm{d} T + V\mathrm{d} p + \mathrm{d} W
$$
> [!Tip] 最大非体积功
> 在等温等压过程中，系统对外所做的非体积功$W' = -W$有一个极限，该极限为过程中系统的自由焓的减小量

焓$H = G + TS$; 其中$G$是可以对外做非体积功的*自由焓*；另一部分能量 ($TS$) 则是不能向外输出的能量，即*束缚能*

## 等温等压条件下过程进行的方向
在系统温度和压强都固定，且除体积功外无其它形式的功的条件下，过程进行方向的判据为
$$
\mathrm{d} G \le 0
$$
称为*自由焓减少原理*
平衡的判据为$\mathrm{d} G = 0$, 即自由焓达到最小值