# 形成Fraunhofer衍射场的条件
## 远场条件
**接收屏幕应该放得足够远**，由[[Representation of Electromagnetic Waves#傍轴条件和远场条件|电磁波的远场条件]]知道接收屏和衍射屏之间的距离$z$需要满足
$$
z \gg \dfrac{a^2}{\lambda}
$$
其中$a$为衍射屏的线度，可取为孔径大小
## 傍轴条件
接收屏幕上能形成Fraunhofer衍射图样的几何限度$\rho$也需要满足[[Representation of Electromagnetic Waves#傍轴条件和远场条件|电磁波的傍轴条件]]，也就是
$$
\rho \ll z
$$
# 实验现象
![[光学-Fraunhofer衍射装置.png]]一系列亮斑。中心为亮斑，亮度大于两侧的亮斑。中心亮斑宽度是两侧的二倍，亮斑的宽度随狭缝的变窄而展宽
# 单缝衍射
## 矢量图示
![[光学-单缝Fraunhofer衍射.png]]
类似地，可以用矢量图示法来分析屏上一点$P(\theta)$的振幅
![[光学-单缝衍射矢量图示.png]]
由此可知，如果光程差$\Delta L = a \sin \theta = k \lambda$，对应的相位差是$\Delta = 2k\pi$，对应的振幅是$0$，$P$点为暗点，**这和两束光干涉的情况恰好相反**

需要注意的是，当$k$不断增大的时候，振幅曲线的半径因为光的衰减会越来越多，故对$\Delta L = (k + \dfrac{1}{2})\lambda, \;k \ge 1$的点来说，虽然都是亮点，但随着$k$的增大，亮度会越来越低

> [!Note] 上面排除了$k = 0$的情况，这是因为
> 由于$\Delta L = 0$的时候是最亮的点，而$\Delta L= \lambda$的时候是第一个暗点，所以当$\Delta L = \dfrac{\lambda}{2}$的时候其亮度处于二者之间，不能算作暗点；但是对于$k \ge 1$的情况来说，由于其两侧光程差为$\lambda$整数倍的点都是暗点，故视其为亮点

## 定量分析
考虑$k$级暗纹，设$x$为定义在屏上的坐标
$$
\Delta L = a \sin \theta_k = k \lambda \implies \sin \theta_k = k \frac{\lambda}{a} \implies x_k = f \tan \theta_k
$$
其中$k = 1, 2, 3, \ldots$
如果$\theta_k \to 0$，则有
$$
|x_k| \approx f k \dfrac{\lambda}{a} = k \dfrac{\lambda}{a}f
$$
对于$k$级亮纹，类似地有
$$
\sin \theta_k = \left(k + \dfrac{1}{2}\right) \dfrac{\lambda}{a}
$$
其中$k = 1, 2, 3, \ldots$
如果$\theta_k \to 0$，则有
$$
|x_k| = \left(k + \dfrac{1}{2}\right) \dfrac{\lambda}{a} f
$$
特别地，$0$级亮条纹在$x = 0$的位置

## 条纹宽度
定义$k$级亮纹的*角宽度*为$\Delta \theta_k = \theta_k - \theta_k = \dfrac{\lambda}{a}$, 其中$k = 0$. 当$k = 0$时，$\Delta \theta_0 = \theta_{+1} - \theta_{-1} = 2 \dfrac{\lambda}{a}$
光斑的几何宽度$\Delta x_k = f \Delta \theta_k$，几何直径$D_k = 2f\Delta \theta_k$
## 单缝衍射因子
定义$\beta = \dfrac{\pi a}{\lambda} \sin \theta$, 通过解菲涅尔积分可以得到光强$I$关于$\beta$的分布
$$
\dfrac{I(\theta)}{I(0)} = \left(\dfrac{\sin\beta}{\beta}\right)^2
$$
解得$I(\theta)$的极大值满足$\beta = \tan \beta$
![[光学-单缝衍射因子的极大值.png]]
可以近似为极大值出现在$\beta = \pm \left(k + \dfrac{1}{2}\right)\pi$处，作$I\sim \beta$图像
![[光学-单缝衍射光强图像.png]]
## 矩孔衍射的强度公式
光程差
$$
\Delta L = -(x\sin \theta_1+y\sin \theta_2)
$$
有
$$
I(\theta_1,\theta_2) = I_0 \left(\dfrac{\sin\alpha}{\alpha}\right)^2  \left(\dfrac{\sin\beta}{\beta}\right)^2 
$$
## 衍射反比关系
将角宽度公式变形，有
$$
\Delta \theta \cdot a = \lambda
$$
这个反比关系有如下意义
- 当$a$足够大时，$\Delta \theta$足够小，对应于几何光学极限
- 参与干涉的波源数目越多，出现干涉极大的条件越苛刻，能量也越集中在某个特定的方向上
- 说明衍射具有放大作用，可以用于测量单缝或细丝的宽度或直径

## 斜入射情形
当平行光以$\theta_0$角斜入射在宽度为$a$的单缝上时
1. 强度公式基本不变
$$
I(\theta) = I(0) \left(\dfrac{\sin \alpha}{\alpha}\right)
$$
但是这里$\alpha$被定义为
$$
\alpha = \dfrac{\pi a}{\lambda} (\sin \theta - \sin\theta_0)
$$
2. 零级中心的位置仍然在几何光学像点处$\theta = \theta_0$
3. 零级斑的**半**角宽度为
$$
\sin (\theta_0 + \Delta \theta) - \sin(\theta_0) =  \dfrac{\lambda}{a} \implies \Delta \theta = \dfrac{\lambda}{a\cos\theta_0}
$$
4. 如果衍射屏前后两侧为不同介质，设前场照明空间折射率为$n_1$，后场衍射空间折射率为$n_2$，则强度公式为
$$
I(\theta) = I(0) \left(\dfrac{\sin \alpha}{\alpha}\right), \quad \alpha = \dfrac{\pi a}{\lambda} (n_2\sin \theta - n_1\sin\theta_0)
$$
类似地可以得到**半**角宽为
$$
\Delta \theta \approx \dfrac{\lambda_0}{n_2 a\cos \theta_0'} = \dfrac{\lambda_0}{a\sqrt{ n_2^2 - n_1^2\sin^2 \theta_0 }}
$$
# 光学仪器的分辨本领
## Frauhofer圆孔衍射
在极坐标系下，光程差为
$$
\Delta L = -r\cos\varphi \sin \theta
$$
于是
$$
\widetilde{U}(\theta)=c\int\limits_{0}^{a}\int\limits_{0}^{2\pi}e^{-ikr\cos\varphi\sin\theta}r\mathrm{d} r\mathrm{d}\varphi=c\frac{2J_{1}(\alpha)}{\alpha}
$$
得到
$$
I(\theta) = I_0 \left(\dfrac{2J_1(\alpha)}{\alpha}\right)^2, \quad \alpha = \dfrac{\pi a}{\lambda} \sin \theta
$$
可以解得对应的主极大半角宽
$$
\Delta \theta_0 = 0.61 \dfrac{\lambda}{a} = 1.22 \dfrac{\lambda}{D}
$$
这个主极大的光斑被称为*Airy斑*
> [!Note] 相机的光圈数
> 相机的光圈数定义为镜头焦距和最大光圈直径的比值，即$\dfrac{f}{D}$. 例如，如果镜头的最大光圈直径是$10$mm,焦距是$50$mm，那么光圈数就是$50/10 = 5$，通常记为$f/5$
> 
> 光圈数越小，表示光圈越大，进光量越多。光圈数越大，表示光圈越小，进光量越少
> 
> 标准的光圈级数为:$f/1, f/1.4, f/2, f/2.8, f/4, f/5.6, f/8, f/11, f/16, f/22, f/32$。这些数值是相邻级数的二倍关系

## Rayleigh判据
当一个圆斑像的中心刚好落在另一圆斑像的边缘（第一暗纹）上时，被认为刚刚能被分辨。由此定义的最小分辨角为：
$$
\Delta \theta_m = 1.22 \dfrac{\lambda}{D}
$$
由此可知，望远镜要提升分辨率，物镜的口径就必须要大
> [!Note] 望远镜的有效放大倍数
> $$
> M_m = \dfrac{\delta \theta_e}{\delta \theta_m}
> $$
> 选择目镜时，需要能使总放大率能将仪器的最小分辨角放大到人眼所能分辨的最小角度$1'\approx 2.9 \times 10^{-4}\;\mathrm{rad}$

### 显微镜的像分辨能力
显微镜的最小分辨距离为
$$
\delta y_m = \dfrac{0.61 \lambda}{n \sin u} = 0.61 \dfrac{\lambda}{\mathrm{N.A.}}
$$
其中$\mathrm{N.A.} = n \sin u$称为显微镜的[[Numerical Aperture|数值孔径]]
> [!Note] 显微镜的有效放大率
> 人眼可以分辨的最小距离
> $$
> \delta y_e = s_0 \delta \theta_e = 25 \mathrm{cm} \times \left( 2.9 \times 10^{-4} \mathrm{ rad} \right) = 72.5 \mathrm{\mu m}
> $$
> 由此定义显微镜的有效放大率
> $$
> M = \dfrac{\delta y_e}{\delta y_m}
> $$

> [!Tip] 回忆
> [[Optical Systems#显微镜|显微镜的放大率公式]]为
> $$
> M = V_O M_E = -\dfrac{\Delta}{f_O}\dfrac{s_0}{f_E}
> $$

![[光学-显微镜的分辨本领.png]]

- 可以通过油浸增大显微镜的数值孔径，从而提升它的分辨能力-
- 也可以通过使用短波长的光来提升分辨能力

# 多缝衍射
## 衍射图样
设$b$为缝宽，$a$是缝和缝之间间隔（以一条缝的中心到另一条缝的中心的距离为准）
![[光学-多缝衍射.png]]
![[光学-多缝衍射图样-2缝.png]]
![[光学-多缝衍射图样-4缝.png]]
![[光学-多缝衍射图样-8缝.png]]
## 强度分布
由
![[光学-多缝衍射强度公式推导.png]]
注意这里的$\alpha, \beta$和下文的意义恰好相反

有
$$
I(\theta)=\frac{I(0)}{N^2}\Bigg(\frac{\sin\beta}\beta\Bigg)^2\Bigg(\frac{\sin N\alpha}{\boxed{\sin\alpha}}\Bigg)^2
$$
其中$\left( \dfrac{\sin\beta}{\beta} \right)$为*单缝衍射因子*，$\left( \dfrac{\sin N\alpha}{\sin \alpha} \right)$为*缝间干涉因子*
且
$$
\beta = \dfrac{\pi b}{\lambda} \sin \theta,\quad \alpha = \dfrac{\pi a}{\lambda} \sin \theta
$$

它们的图像如下
![[光学-多缝衍射函数图像1.png]]
![[光学-多缝衍射函数图像2.png]]
> [!Tip] 总结
> 微观决定宏观 - 缝的大小决定图样的宏观结构（外包络）
> 宏观决定微观 - 缝和缝的间距决定图样的微观结构（每一个次极大）

### 主极大
$$
\sin \theta = k \dfrac{\lambda}{a}, \quad k = 0,\pm1,\pm 2,\ldots
$$
### 次极大
$$
\sin \theta = (k + \dfrac{m}{N}) \dfrac{\lambda}{d}, \quad m = 1, 2, \cdots N - 1
$$
### 缺级
$$
\sin \theta = k \dfrac{\lambda}{b} = k' \dfrac{\lambda}{a}
$$

