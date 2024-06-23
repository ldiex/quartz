# 实际气体
- 微观粒子不是点粒子，而具有一定的大小
- 微观粒子之间存在相互作用
# 分子相互作用的经验模型
## 分子力(Van der Waals Force)的半经验公式
$$
F(r) = \dfrac{\alpha}{r^s} - \dfrac{\beta}{r^t}
$$
## 分子势能
![[热学-Van Der Walls Force.png]]
当两个分子从足够远距离开始碰撞的时候，先是由于分子间吸引力相互加速靠近，然后变成排斥力减速接近，直到相对速度为零，设此时分子间间距为$d$, 称其为*分子的有效直径*

整个过程可以看作有效直径$d$的分子的一种“弹性碰撞”
## 经验模型的进一步简化
### 钢球模型
$$
E_p = \begin{cases}
\infty, & r \le d \\ 0, & r > d
\end{cases}
$$
### Sutherland 模型
$$
E_p = \begin{cases}
\infty, &r \le d \\ -\dfrac{\beta}{r^{t - 1}}, & r>d
\end{cases}
$$
# Van der Waals 方程
对理想气体状态方程作出两个修正
$$
(p + \dfrac{a}{V_m^2}) (V_m - b) = RT
$$
其中$b$源自气体分子占有的体积（分子间排斥力），因此分子自由活动的空间小于气体的体积，可以证明$b$是一摩尔气体所占有的体积的四倍，也就是$b = 4N_AV_0 = 4N_A \cdot \dfrac{4}{3} \pi \left( \dfrac{d}{2} \right)^2$
$$
p = \dfrac{\nu RT}{V - b\nu} = \dfrac{RT}{V_m - b}
$$
而$a$源自气体分子间吸引力，因此分子对器壁的冲量会比较小，由此修正$p$
$$
p = \dfrac{RT}{V_m - b} - \Delta p
$$

