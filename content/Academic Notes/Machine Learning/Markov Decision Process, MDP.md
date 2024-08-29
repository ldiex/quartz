# Markov 过程
## 随机过程
在*随机过程*中，随机现象在某时刻$t$的取值是一个向量随机变量，用$S_t$表示，所有可能的状态组成*状态集合* $\mathcal S$ . 我们将已知历史信息$(S_1, \cdots, S_n)$时下一个时刻状态为$S_{t + 1}$的概率表示为$P(S_{t + 1} \mid S_1, \cdots, S_t)$

## Markov 性质
我们称一个随机过程具有*Markov 性质* 当且仅当 某时刻的状态只取决于上一时刻的状态. 也就是说，当前状态是未来的充分统计量. 但是，由于当前状态也由前一个状态决定，所以*Markov 性质*也包含了历史的影响，只是这种影响不是显式的. 

见 [[Markov Property]]

## Markov 过程
*Markov 过程* 指具有Markov 性质的随机过程，也称为*Markov 链*. 我们通常用元组$(\mathcal S, \mathcal P)$描述一个Markov 过程， 其中$\mathcal S$是有限数量的状态集合，$\mathcal P$是*状态转移矩阵*. 假设一共有$n$个状态，此时$\mathcal S = \{s_1, s_2, \cdots, s_n\}$. 状态转移矩阵$\mathcal P$定义了所有状态对之间的转移概率
$$
\mathcal P = \begin{pmatrix}
P(s_1 | s_1) & \cdots & P(s_n | s_1) \\
\vdots & \ddots & \vdots \\
P(s_1, |s_n) & \cdots & P(s_n | s_n)
\end{pmatrix}
$$
称矩阵中的每一个元素$P(s_j | s_i)  = P(S_{t + 1} = s_j | S_t = s_i)$为状态转移函数，状态转移矩阵中的每一行的和为$1$, 如果不能转移则定义概率为$0$. 如果一个状态不能转移到任何一个状态，则称这个状态为*终止状态*

给定一个Markov 过程，我们可以从某个状态出发，根据它的状态转移矩阵生成一个*状态序列 (episode)*，这个步骤也被叫做*采样 (sampling)*

# Markov 奖励过程
含有奖励函数$r$和折扣因子$\gamma$的Markov 过程称为*Markov 奖励过程*，用四元组$(\mathcal S, \mathcal P, r, \gamma)$表示，其中
- 某个状态$s$的奖励$r(s)$指转移到该状态时可以获得的奖励的期望
- $\gamma$为*折扣因子*，范围是$[0, 1)$ . 引入折扣因子的理由为远期利益具有一定不确定性，有时我们更希望能够尽快获得一些奖励，所以我们需要对远期利益打一些折扣. 接近$1$的$\gamma$更关注长期的累计奖励，接近$0$的更考虑短期奖励

## 回报
在马尔可夫奖励过程中，一个状态的期望回报（即从这个状态出发的未来累积奖励的期望）被称为这个状态的*价值  (value)*. 所有状态的价值就组成了*价值函数 (value function)*. 价值函数的输入为某个状态，输出为这个状态的价值. 我们将价值函数写成
$$
\begin{aligned}
V(s)& =\mathbb{E}[G_t|S_t=s]  \\
&=\mathbb{E}[R_t+\gamma R_{t+1}+\gamma^2R_{t+2}+\ldots|S_t=s] \\
&=\mathbb{E}[R_t+\gamma(R_{t+1}+\gamma R_{t+2}+\ldots)|S_t=s] \\
&=\mathbb{E}[R_t+\gamma G_{t+1}|S_t=s] \\
&=\mathbb{E}[R_t+\gamma V(S_{t+1})|S_t=s]
\end{aligned}
$$
这里$R_t$表示时刻$t$获得的奖励. 

注意到$r(s) = \mathbb E[R_t|S_t = s]$和
$$
\mathbb E [\gamma V(S_{t + 1})| S_t = s] = \gamma \sum_{s' \in \mathcal S} p(s'|s) V(s')
$$
于是
$$
V(s) = r(s) + \gamma \sum_{s' \in \mathcal S} p(s'|s) V(s')
$$
上式便是*Bellman 方程*, 对每一个状态都成立. 我们可以把一个$n$个过程的Markov 奖励过程中的所有状态的价值表示为一个列向量$\mathcal V = [V(s_1), V(s_2), \cdots, V(s+n)]^T$，同理也可以把奖励函数写成$\mathcal R = [r(s_1), r(s_2), \cdots, r(s_n)]^T$，由此把Bellman 方程写为
$$
\mathcal V = \mathcal R + \gamma \mathcal P \mathcal V
$$
也就是
$$
\begin{bmatrix}V(s_1)\\V(s_2)\\\vdots\\V(s_n)\end{bmatrix}=\begin{bmatrix}r(s_1)\\r(s_2)\\\vdots\\r(s_n)\end{bmatrix}+\gamma\begin{bmatrix}P(s_1|s_1)&P(s_2|s_1)&\ldots&P(s_n|s_1)\\P(s_1|s_2)&P(s_2|s_2)&\ldots&P(s_n|s_2)\\\vdots\\P(s_1|s_n)&P(s_2|s_n)&\ldots&P(s_n|s_n)\end{bmatrix}\begin{bmatrix}V(s_1)\\V(s_2)\\\vdots\\V(s_n)\end{bmatrix}
$$
计算得
$$
\begin{aligned}\mathcal{V}&=\mathcal{R}+\gamma\mathcal{P}\mathcal{V}\\(I-\gamma\mathcal{P})\mathcal{V}&=\mathcal{R}\\\mathcal{V}&=(I-\gamma\mathcal{P})^{-1}\mathcal{R}\end{aligned}
$$
这个算法的时间复杂度是$O(n^3)$，其中$n$是状态个数，因此这种方法只适用很小的马尔可夫奖励过程. 求解较大规模的马尔可夫奖励过程中的价值函数时，可以使用*动态规划（dynamic programming）* 算法、*蒙特卡洛方法（Monte-Carlo method）* 和*时序差分（temporal difference）*
# Markov 决策过程
*Markov 决策过程  (MDP)* 在 Markov 奖励过程的基础上加上了*动作 (action)* , 其集合为$\mathcal A$, 故一个MDP可以由元组$(\mathcal S, \mathcal A, P, r, \gamma)$构成

注意MDP中的状态转移函数$P$由转移矩阵拓展为了更一般的状态转移函数$P(s'|s, a)$，表示在状态$s$执行动作$a$后到达状态$s'$的概率. 在状态和动作离散的情况下，$P$可用一个*三维张量*来表示

## 策略

不同于马尔可夫奖励过程，在马尔可夫决策过程中，通常存在一个智能体来执行动作. 马尔可夫决策过程是一个与时间相关的不断进行的过程，在智能体和环境 MDP 之间存在一个不断交互的过程：智能体根据当前状态$S_t$选择动作$A_t$; MDP 根据奖励函数和状态转移函数得到$S_{t + 1}$和$R_t$并反馈给智能体. 智能体的目标是**最大化得到的累计奖励**. 智能体根据当前状态从动作的集合中选择一个动作的函数，被称为*策略*. 

策略通常用$\pi(a | s) = P(A_t = a | S_t = s)$, 表示在输入状态$s$时采取动作$a$的概率. 当一个策略是*确定性策略（deterministic policy）* 时，它在每个状态时只输出一个确定性的动作，即只有该动作的概率为$1$，其他动作的概率为 $0$；当一个策略是*随机性策略（stochastic policy）* 时，它在每个状态时输出的是关于动作的概率分布，然后根据该分布进行采样就可以得到一个动作. 

在MDP中的状态价值函数和策略$\pi$有关，定义为
$$
V^{\pi} (s) = \mathbb E_\pi [G_t | S_t = s]
$$
同时再定义一个*动作价值函数 (action-value function)* 
$$
Q^\pi (s, a) = \mathbb E_\pi [G_t | S_t = s, A_t = a]
$$
由此可以推出两个价值函数之间的关系
$$
V^\pi (s) = \sum_{a \in A} \pi(a | s)Q^\pi(s, a)
$$
## Bellman 期望方程
两个状态函数的 *Bellman 期望方程*
$$
\begin{aligned}
V^{\pi}(s)& =\mathbb{E}_\pi[R_t+\gamma V^\pi(S_{t+1})|S_t=s]  \\
&=\sum_{a\in A}\pi(a|s)\left(r(s,a)+\gamma\sum_{s^{\prime}\in S}p(s^{\prime}|s,a)V^\pi(s^{\prime})\right) \\
Q^{\pi}(s,a)& =\mathbb{E}_\pi[R_t+\gamma Q^\pi(S_{t+1},A_{t+1})|S_t=s,A_t=a]  \\
&=r(s,a)+\gamma\sum_{s^{\prime}\in S}p(s^{\prime}|s,a)\sum_{a^{\prime}\in A}\pi(a^{\prime}|s^{\prime})Q^{\pi}(s^{\prime},a^{\prime})
\end{aligned}
$$
## 求解MDP
为了求解MDP中的各个状态的价值函数，可以对策略的动作选择进行*边缘化 (marginalization)* 

定义
$$
r'(s) = \sum_{a \in \mathcal A} \pi(a | s) r(s, a)
$$
和
$$
P'(s'|s) = \sum_{a \in \mathcal A} \pi(a | s)P(s'|s, a)
$$
这构建了一个MRP $: (\mathcal S, P', r', \gamma)$. **也就是说，当策略$\pi$函数确定时，一个MDP可以退化为MRP来求解****
**
# Monte-Carlo 方法
*Monte-Carlo 方法*使用重复随机抽样，然后运用概率统计方法来从抽样结果中归纳出我们想求的目标的数值估计

求解一个状态的价值，也就是求解它的期望回报，这时候就可以根据策略在MDP上采样很多条序列，然后计算从这个状态出发的回报再求其期望
$$
V^\pi(s) = \mathbb E_\pi[G_t |S_t = s] \approx \frac{1}{N}\sum_{i = 1}^N G_t^{(i)}
$$
采样次数越多，Monte-Carlo 方法估计的期望值越精确

# 占用度量
定义MDP的*初始状态分布*为$\nu_0 (s)$,  用$P^\pi_t(s)$表示采取策略$\pi$时智能体在$t$时刻处于状态$s$的概率, 则有$P_0^\pi (s) = \nu_0(s)$. 由此定义策略的*状态访问分布 (state visitation distribution)*
$$
\nu^\pi(s) = (1 - \gamma) \sum_{t = 0}^\infty \gamma^t P_t^\pi(s)
$$
其中$1-\gamma$是用来使得概率加和为$1$的归一化因子. 状态访问概率表示一个策略和 MDP 交互会访问到的状态的分布, 它的一个转移方程是
$$
\nu^\pi(s') = (1 - \gamma)\nu_0(s') + \gamma \int P(s' | s, a)\pi(a | s)\nu^\pi(s) \mathrm{d} s \mathrm{d} a
$$
此外，我们还可以定义策略的*占用度量 (occupancy measure)*
$$
\rho^\pi (s, a) = (1 - \gamma) \sum_{t = 0}^\infty \gamma^t P_t^\pi (s) \pi (a | s)
$$
它表示动作状态对$(s, a)$被访问到的概率，二者之间存在如下关系
$$
\rho^\pi(s, a) = \nu^\pi (s) \pi(a|s)
$$
进一步得出
## 定理1
智能体分别以策略$\pi_1, \pi_2$和同一个MDP交互得到的占用度量$\rho^{\pi_1}, \rho^{\pi_2}$满足
$$
\rho^{\pi_1} = \rho^{\pi_2} \iff \pi_1 = \pi_2
$$
## 定理2
给定一合法占用度量$\rho$，可生成该占用度量的唯一策略是
$$
\pi_p = \dfrac{\rho(s, a)}{\sum_{a'} \rho(s, a')}
$$
以上提到的 *“合法”占用度量* 是指存在一个策略使智能体与 MDP 交互产生的状态动作对被访问到的概率. 

# 最优策略
定义*最优状态价值函数*
$$
V^*(s) = \max_{\pi} V^\pi (s)$$
和*最优动作价值函数*
$$
Q^*(s, a) = \max_{\pi}Q^\pi(s, a)
$$
它们之间的关系
$$
Q^*(s,a)=r(s,a)+\gamma\sum_{s^{\prime}\in S}P(s^{\prime}|s,a)V^*(s^{\prime})
$$
另一方面
$$
V^*(s) = \max_{a \in \mathcal A}Q^*(s,a)
$$
由此可以构造出*最优策略*
$$
\pi^* (a|s) = 
\begin{cases}
1 & \text{if } a = \underset{a \in \mathcal A}{\operatorname{argmax} Q^*(s,a)} \\ 0 & \text{otherwise}
\end{cases}
$$
最优策略满足
$$
\forall s \in \mathcal S,\forall \pi,\; V^{\pi^*}(s) \ge V^\pi(s)
$$
# Bellman 最优方程
即最优价值函数的转移方程
$$
\begin{gathered}V^*(s)=\max_{a\in\mathcal{A}}\{r(s,a)+\gamma\sum_{s^{\prime}\in\mathcal{S}}p(s^{\prime}|s,a)V^*(s^{\prime})\}\\Q^*(s,a)=r(s,a)+\gamma\sum_{s^{\prime}\in\mathcal{S}}p(s^{\prime}|s,a)\max_{a^{\prime}\in\mathcal{A}}Q^*(s^{\prime},a^{\prime})\end{gathered}
$$


