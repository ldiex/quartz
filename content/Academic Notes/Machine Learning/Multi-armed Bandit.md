多臂老虎机问题可以被看作简化版的强化学习问题. 与强化学习不同, 多臂老虎机不存在状态信息, 只有动作和奖励, 算是最简单的“和环境交互中的学习”的一种形式. 

# 问题介绍
## 问题定义
在多臂老虎机(MAB)问题, 有一个拥有$K$根拉杆的老虎机, 拉动每一根拉杆都对应一个关于奖励的概率分布$\mathcal R$. 我们每次拉动其中一根拉杆, 就可以从该拉杆对应的奖励概率分布中获得一个奖励$r$. 们在各根拉杆的奖励概率分布未知的情况下, 从头开始尝试, 目标是在操作 $T$次拉杆后获得尽可能高的累积奖励. 

## 形式化描述
表示为一个元组$\langle \mathcal A, \mathcal R \rangle$, 其中: 
- $\mathcal A$为动作集合, 其中一个动作表示拉动一个拉杆. 若多臂老虎机一共有$K$根拉杆, 那动作空间就是集合$\{a_1, \cdots, a_K\}$, 其中$a_t \in A$表示一个动作
- $\mathcal R$为奖励概率分布, 拉动每一根拉杆的动作$a_t$都对应一个奖励概率分布$\mathcal R(r | a_t)$, 不同拉杆的奖励分布通常是不同的. 
假设每个时间步只能拉动一个拉杆, 多臂老虎机的目标为最大化一段时间步$T$内累积的奖励:
$$
\max \sum_{t = 1}^{T} r_t,\; r_t \sim \mathcal R(\cdot | a_t)
$$
这里$\cdot$是占位符, 表示任何和任意

## 累计懊悔
对于每一个动作$a$, 我们定义其期望奖励为
$$
Q(a) = \mathbb E_{r \sim \mathcal R(\cdot | a)}[r]
$$
且至少存在一根拉杆, 它的期望奖励不小于拉动其他任意一根拉杆, 我们将该最优期望奖励表示为
$$
Q^* = \max_{a \in \mathcal A} Q(a)
$$
为了更加直观、方便地观察拉动一根拉杆的期望奖励离最优拉杆期望奖励的差距, 引入*懊悔(regret)*, 定义为拉动当前拉杆的动作$a$与最优拉杆的期望奖励差: 
$$
R(a) = Q^* - Q(a)
$$
*累计懊悔(cumulative regret)* 即操作$T$次拉杆后累积的懊悔总量, 对于一次完整的$T$步决策, 累计懊悔为
$$
\sigma_R = \sum_{t = 1}^T R(a_t)
$$
MAB 问题的目标为最大化累积奖励, **等价于最小化累积懊悔**

## 估计期望奖励
为了知道拉动哪一根拉杆能获得更高的奖励, 我们需要估计拉动这根拉杆的期望奖励. 由于只拉动一次拉杆获得的奖励存在随机性, 所以需要多次拉动一根拉杆, 然后计算得到的多次奖励的期望, 其算法流程如下所示. 

$$
\begin{aligned}
&\forall a \in \mathcal A, \text{计数器} N(a) = 0 \; \text{期望奖励估值} \hat Q(a) = 0 \\
&\textbf{For } t = 1 \to T \textbf{ do:} \\
&\quad \text{选取某根拉杆, 该动作记为}a_t \\
&\quad \text{得到奖励} r_t \\
&\quad N(a_t) = N(a_t) + 1 \\
&\quad \hat Q(a_t) = \hat Q(a_t) + \dfrac{1}{N(a_t)} \left[ r_t - \hat Q(a_t) \right] \\
&\textbf{end for}
\end{aligned} 
$$
其中对于循环的第四行
$$
\begin{aligned}
Q_k &= \frac{1}{k} \sum_{i = 1}^k r_i \\
&= \frac{1}{k} \left( r_k + \sum_{i = 1}^{k - 1} r_i \right) \\
&= \frac{1}{k} \left( r_k + (k - 1)Q_{k-1} \right) \\
&= \frac{1}{k} \left( r_k + kQ_{k-1} - Q_{k -1}\right) \\
&= Q_{k - 1} + \frac{1}{k} \left[r_k - Q_{k -1}\right]
\end{aligned}
$$
采用这种增量式更新可以把时间复杂度和空间复杂度均优化到$O(1)$

下实现一个拉杆数为$10$的多臂老虎机. 其中拉动每根拉杆的奖励服从*伯努利分布（Bernoulli distribution）*, 即每次拉下拉杆有的概率获得的奖励为$1$, 有$1-p$的概率获得的奖励为 $0$. 奖励为$1$代表获奖, 奖励为$0$代表没有获奖. 

# 探索和利用的平衡
在多臂老虎机问题中, 一个经典的问题就是探索与利用的平衡问题. *探索（exploration）* 是指尝试拉动更多可能的拉杆, 这根拉杆不一定会获得最大的奖励, 但这种方案能够摸清楚所有拉杆的获奖情况. 例如, 对于一个 $10$ 臂老虎机, 我们要把所有的拉杆都拉动一下才知道哪根拉杆可能获得最大的奖励. *利用（exploitation）* 是指拉动已知期望奖励最大的那根拉杆, 由于已知的信息仅仅来自有限次的交互观测, 所以当前的最优拉杆不一定是全局最优的

于是在多臂老虎机问题中, 设计策略时就需要**平衡探索和利用的次数, 使得累积奖励最大化** 一个比较常用的思路是在开始时做比较多的探索, 在对每根拉杆都有比较准确的估计后, 再进行利用. 目前已有一些比较经典的算法来解决这个问题, 例如 *$\varepsilon$-贪婪算法*、*上置信界算法*和*汤普森采样算法*等

# $\varepsilon$-贪心算法
完全贪婪算法即在每一时刻采取期望奖励估值最大的动作（拉动拉杆）, 这就是纯粹的利用, 而没有探索, 所以我们通常需要对完全贪婪算法进行一些修改, 其中比较经典的一种方法为 [[Epsilon-Greedy Algorithm ]], 它完全贪婪算法的基础上添加了噪声, 每次以$1 - \varepsilon$ 的概率选择以往经验中期望奖励估值最大的那根拉杆（利用）, 以概率$\varepsilon$随机选择一根拉杆（探索）

随着探索次数的不断增加, 我们对各个动作的奖励估计得越来越准, 此时我们就没必要继续花大力气进行探索. 所以在$\varepsilon$-贪婪算法的具体实现中, 我们可以令$\varepsilon$随时间衰减, 即探索的概率将会不断降低

# 上置信界算法
设想这样一种情况: 对于一台双臂老虎机, 其中第一根拉杆只被拉动过一次, 得到的奖励为$0$；第二根拉杆被拉动过很多次, 我们对它的奖励分布已经有了大致的把握. 这时你会怎么做? 或许你会进一步尝试拉动第一根拉杆, 从而更加确定其奖励分布. 这种思路主要是基于不确定性, 因为此时第一根拉杆只被拉动过一次, 它的不确定性很高. 一根拉杆的不确定性越大, 它就越具有探索的价值, 因为探索之后我们可能发现它的期望奖励很大. 我们在此引入不确定性度量$U(a)$ , 它会随着一个动作被尝试次数的增加而减小. 我们可以使用一种基于不确定性的策略来综合考虑现有的期望奖励估值和不确定性, 其核心问题是如何估计不确定性. 

对于一个$K$臂老虎机, 设$X_i(t)$表示在第$t$步拉杆$i$被拉下所获得的奖励, 并设$I(t) \in \{1, \cdots, K\}$表示第$t$步选择的老虎机编号, 这里的$I(t)$和之前选择的拉杆编号和其相应的奖励有关, 同时也包含一定随机性（玩家可能会在其选择策略中加入随机因子）

现在定义$N_i(t)$表示拉杆$i$在前$t$轮被拉下的次数
$$
N_i (t) =\sum_{s = 1}^t \mathbf{1}(I(s) = i)
$$
和$S_i(t)$为在前$t$轮从拉杆$i$上获得的奖励总和
$$
S_i(t) = \sum_{s = 1}^n X_i(s) \mathbf{1} (I(s) = i)
$$
这里的$\mathbf{1}$表示[[Indicator Function | 指示函数]]
再定义$\hat \mu_{i,n}$为在拉杆$i$被拉动$n$次后得到的平均奖励
$$
\hat \mu_{i, N_i(t)} = \dfrac{S_i(t)}{N_i(t)}
$$
假设经过$t$轮拉动拉杆后, 每一个拉杆都被拉过了, 最平凡的策略就是假设我们估计的$\bar \mu_{i, N_i(t)}$就是该拉杆实际的奖励期望$\mu_i$, 然后选择估计值最高的拉杆拉动, 但是这显然不是最优解. 

因此我们要通过某种方式来知道我们当前估计的置信程度. 也即是说, 对于一个小量$\delta > 0$, 利用[[Hoeffding's Inequality]] 我们有
$$
\mathbb{P} (\mu_i - \hat \mu_{i, n} > x) \le \mathbb{P}\left(\left|{\sum_{i = 1}^n X_i(t) - n\mu_i}\right| > nx \right) \le e^{-2nx^2}
$$
于是
$$
x = \sqrt{\dfrac{1}{2n} \log\left(\dfrac{1}{\delta}\right)} \implies \mathbb{P}(\mu_i - \hat \mu_{i, n} < x) > 1 - \delta
$$
于是对$\mu_i$的估计便有*置信上界*$\hat \mu_{i, n} + \sqrt{\log(1/\delta) /2n}$

由此给出*UCB算法*
1. 在前$K$轮按顺序把每个拉杆都拉一遍
2. 对$t > K$, 选择
$$
I(t + 1) \in \underset{i \in [K]}{\arg \max} \left\{ \hat \mu_{i, N_i(t)} + \sqrt{\dfrac{\alpha \log t}{2N_i(t)}}\right\}
$$
也可以一开始先不把所有拉杆都拉一遍, 而选用
$$
I(t + 1) \in \underset{i \in [K]}{\arg \max} \left\{ \hat \mu_{i, N_i(t)} + \sqrt{\dfrac{\alpha \log t}{2(N_i(t) + 1)}}\right\}
$$
其中的$\alpha$是我们可以调整的系数

# Thompson 采样
先假设拉动每根拉杆的奖励服从一个特定的概率分布, 然后根据拉动每根拉杆的期望奖励来进行选择. 但是由于计算所有拉杆的期望奖励的代价比较高, 汤普森采样算法使用采样的方式, 即根据当前每个动作$a_i$的奖励概率分布进行一轮采样, 得到一组各根拉杆的奖励样本, 再选择样本中奖励最大的动作. 可以看出, 汤普森采样是一种计算所有拉杆的最高奖励概率的蒙特卡洛采样方法. 

在实际情况中, 我们通常用 Beta分布对当前每个动作的奖励概率分布进行建模. 具体来说, 若某拉杆被选择了$k$次, 其中$m_1$次奖励为 $1$,  $m_0$次奖励为 $0$, 则该拉杆的奖励服从Beta 分布$\beta (m_1 + 1, m_0 + 1)$

每次对每个拉杆进行一次采样, 对其采样的值进行排序, 然后贪心第选择值最大的作为下一次的动作

见[[Thompson Sampling Algorithm]]


