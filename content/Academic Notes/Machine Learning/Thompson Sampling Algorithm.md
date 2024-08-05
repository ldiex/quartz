讨论TS算法、贪心算法和UCB算法的文章: [什么是汤普森采样 - 王腾云的回答](https://www.zhihu.com/question/37212823/answer/96392474)

用广告投放来做例子：

第一步：先将三个ads都投放一段时间，收集一部分数据. 在每一回合，对于每个$\text{ad}_i$, 如果用户点击一次，那么${N}_{i}^{1} += 1$， 如果没有点击${N}_{i}^{0} += 1$

第二步：对于收集到的每个$\text{ad}_i$ 的数据，random sample from:

${\theta}_{i}(n) = \beta({N}_{i}^{1}+1, {N}_{i}^{0}+1)$

第三步：选取有最高 ${\theta}_{i}(n)$ score 的 ad 展示出来

第四步：不断重复2-3步，直至收敛，或者reward足够好.

![[概率统计-beta分布图.webp]]
对于$B(\alpha, \beta)$, 如果$\alpha > \beta$, 曲线就越向1倾斜，得到靠近1的几率较大，score偏大
如果$\alpha < \beta$, 曲线就越向0倾斜，得到靠近0的几率比较大，score偏小


