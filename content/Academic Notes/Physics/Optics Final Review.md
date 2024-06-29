# 干涉
振幅的叠加 + 3个相干条件 $\to$ 强度的变化
反衬度
$$
\gamma = \dfrac{I_M - I_m}{I_M + I_m},\quad 0 \le \gamma \le 1
$$
## Young氏双缝和它的各种变种(Fresnel 双棱镜, H.Lloyd镜 etc.)
都变换为Young的情况，利用公式
$$
\Delta x = \dfrac{D}{d} \lambda
$$
## 薄膜干涉
光程差
$$
\Delta L = 2nh\cos i + \dfrac{\Delta \phi}{2\pi} \lambda
$$
其中$\Delta \phi=0，\pm \pi$表示潜在的*半波损失*。当波从波疏介质($n$小的)垂直入射到波密介质（$n$大的）并从分界面反射回波疏介质时，会产生半波损失。对于三层两分界面的薄膜模型，“汉堡包”式的情况会产生半波损失

## 等厚条纹
厚度不均匀薄膜表面的干涉场，取$i \to0$
条状干涉条纹
### Newton环
利用圆幂定理求出某一半径$r$处空气膜的厚度$h$，可解得
$$
r_k = \sqrt{ kR\lambda }
$$
### 光学膜
增透膜要求从上到下三层介质的折射率$n_1,n,n_2$满足$n_1 < n < n_2$，当$n = \sqrt{ n_1n_2 }$时完全消除反射光

高反膜则要求$n_1 < n > n_2$
## 等倾条纹
厚度均匀薄膜**无穷远处**的干涉场，取$h = \mathrm{const}$而改变$i$

倾角相等的条纹会形成一个锥，在无穷远的光屏上（即某个凸透镜的焦平面）就是同心圆

因为$2nh\cos i = k\lambda \implies \cos i_k =\dfrac{k\lambda}{2nh} \propto k$，所以条纹中心（$i$小）级次高、边缘（$i$大）级次低。$h$增大，条纹从中心生出并向外扩展；$h$减小，条纹向中心会聚并消失于中心

采用拓展光源的好处：光源上各点形成完全一样的干涉图样（强度相加而不是振幅相加），其效果是**提高干涉图样的亮度，有益无害**。但是拓展光源对观察等厚条纹会有影响

## Michelson 干涉仪
![[光学-Michelson干涉仪.png|500]]

![[光学-Michelson-等倾条纹.png]]
等倾条纹：厚度越大级数越多，条纹越多、越密
![[光学-Michelson-等厚条纹.png]]
等厚条纹：厚度越小反衬度越高，厚度大了条纹过密反而看不清
## 光源非单色性对干涉条纹的影响
以双线结构为例子
$$
\gamma(\Delta L)=\left|\cos\!\left(\frac{\Delta k\Delta L}2\right)\right|
$$
其中$\Delta L$为光程差，$\Delta k$为波数差

条纹的反衬度随光程差作周期振动，振动的角频率为$\dfrac{\Delta k}{2}$
## 光场的相干性
### 产生原因
空间相干性来源于扩展光源不同部分发光的独立性
时间相干性来源于光源发光过程在时间上的断续性
### 结果
空间相干性主要表现在波场的横向（波前）上，集中体现在分波前干涉装置中；
时间相干性主要表现在波场的纵向（波线）上，集中体现在分振幅干涉装置中

### 反比公式
空间相干性 $\Delta \theta b \sim \lambda$，即要提升干涉场相对光源的角宽度，就必须减小光源尺度
时间相干性 $\tau_0 \Delta \nu \sim 1$，即要提升相干的有效时间，就必须改善光源的单色性

相干区域和相干时间都不是一个绝对的界限，实际上相干区域和相干时间内也有非相干的成分，而相干区域和相干时间之外，也有相干的成分，只是主导地位的不同，部分相干是最为普遍的，而反衬度则是相干程度的一种度量
## Fabry Perot 干涉仪
多光束干涉可以产生非常细窄的干涉条纹。这是因为多次反射会增强干涉条纹的清晰度和对比度，**薄膜的反射率越高，条纹越尖锐**

Fabry Perot干涉仪由两块平行的高反射率玻璃板组成,在两块玻璃板之间形成一个空气间隙， 当光束以一定角度入射到这个系统时,会在玻璃板之间发生多次反射,产生多个相干的光束， 通过调节两块玻璃板之间的间距,可以选择特定波长的光进行传输或反射,从而实现高分辨率的光谱分析

它的光程仍然是
$$
\Delta L = 2nh \cos i
$$
其中$h$是谐振腔宽度，$i$是入射倾角，由此可以推出相位差
$$
\delta = \dfrac{\Delta L}{\lambda}\cdot 2\pi = \dfrac{4\pi n h \cos i}{\lambda}
$$

下面考虑两种情况
### 光源为单色拓展光源
此时$\lambda$固定，但是有各种可能的倾角$i$，因为只有在特定的方向$i_k$上出现干涉极强，我们关心某一级极大条纹的半角宽$\Delta \theta_k$

我们从相位差公式中可以得到
$$
\delta = \dfrac{4\pi n h \cos i}{\lambda} = 2k\pi \implies \cos i_k = \dfrac{k\lambda}{2nh}
$$
两边对$k$求导即有
$$
-\sin i_k\cdot \dfrac{\delta i_k}{\delta k} = \dfrac{\lambda}{2nh} \implies \Delta i_k = \dfrac{\lambda}{2nh\sin i_k}
$$
实际上由于衬比度的原因，对于实际可见的$\Delta \theta_k$需要作出一个修正
$$
\Delta \theta_k = \dfrac{\lambda}{2nh \sin \theta_k}\cdot F
$$
其中修正因子和反射率$R$有关
$$
F = \dfrac{1 - R}{\pi\sqrt{R}}
$$
### 光源为非单色平行光
此时$i$固定且接近于$0$，由于多光束干涉，使得在很宽的光谱范围内只有某些特定的波长$\lambda_k$附近出现极大，这些$\lambda_k$满足下式
$$
2nh = k\lambda_k
$$
对于$\lambda_k$附近波长光线的分辨能力，设光波长为$\lambda$的$k$级可分辨的最小波长间隔为$\Delta \lambda$，则有
$$
\Delta \lambda_k = \Delta \left( \dfrac{2nh}{k} \right) = -\dfrac{1}{k} \lambda_k 
$$
于是$\dfrac{\Delta \lambda_k}{\lambda_k}$可以修正为
$$
\dfrac{\Delta \lambda_k}{\lambda_k} = \dfrac{F}{k} = \dfrac{1}{\pi k}\dfrac{1-R}{\sqrt{R}}
$$
换成频率，则有$\Delta \nu_k \propto \Delta(\dfrac{1}{\lambda}) \propto \Delta \left( \dfrac{k}{2nh} \right) = \dfrac{1}{2nh} \propto \dfrac{\nu_k}{k}$，故也有
$$
\dfrac{\Delta \nu_k}{\nu_k} = \dfrac{F}{k} = \dfrac{1}{\pi k} \dfrac{1- R}{\sqrt{R}}
$$
对于波长范围$\lambda_l \sim \lambda_r$的非单色光，出现极大的间隔（又称*为纵模频率间隔*）为$\Delta \nu = \dfrac{c}{2nh}$，于是可以出现的谱线（又称为*纵模*）数目为$(\dfrac{c}{\lambda_l} - \dfrac{c}{\lambda_r}) / \Delta \nu$，其中每条谱线分别对应的宽度就是$\Delta \nu_k$，换成波长宽就是$\Delta \lambda_k$

换言之，公式$2nh = k\lambda_k = \dfrac{ck}{\nu_k}$确定了每一个极大条纹出现的位置和总的条纹数目（和$F$无关），而$\Delta \nu_k$和$\Delta \lambda_k$确定了每一条亮纹对应的衬比度意义上的频率宽度和波长宽度（需要$F$修正）
# 衍射
衍射的本质可以看作多光束干涉，只是这个“多”趋于无穷大
## Huggens-Fresnel原理
空间某点的振动可看作波前上所有面元所发次波在该点的相干叠加 ，数学上表述为
$$
\widetilde U(p) = \underset{(\Sigma)}{{\iint}} \mathrm{d} {\widetilde U}(p)
$$
## Babinet原理
互补屏衍射场的复振幅之和等于自由传播波场
![[光学-Babinet原理.png]]
## Fresnel衍射
定义：光源或接收屏与衍射屏的距离为有限远
### 半波带法

![[光学-Fresnel衍射.png]]
把波面分割成一个个的*半波带*，相邻半波带**到像点的距离逐个相差半个波长**（名字的来源）

在这种情况下，相邻半波带贡献的复振幅$\tilde{E}_1, \tilde{E}_2, \ldots$的相位差为$\pi$，它们可以相互抵消。

在**自由传播**时，可以通过积分得出**整个波前在像点产生的振幅是第一个半波带的效果之半**，即
$$
E_0 = \dfrac{E_1}{2}
$$
### 矢量图解法
我们再把每个**半波带**分成$N$个子区域
$$
r_0 + \dfrac{\lambda}{2N}, r_0 + \dfrac{\lambda}{N}, r_0 + \dfrac{3\lambda}{2N}, \ldots, r_0 + \dfrac{\lambda}{2}
$$

把它们用矢量来表示，合成的振幅是$E_1=2E_0$（$E_0$是自由传播时中心点的振幅），矢量形成的类圆弧称为*振动曲线*
![[光学-半波带法矢量图解.png|500]]
对于每一个半波带，振动曲线绕半圈，直到最后终于某一个半波带的某一个位置
![[光学-半波带法矢量图解2.png|500]]
对于一个球面波，考虑圆孔衍射，光屏上轴点$P$能接收到的光线是波前的一部分，这个点接受到的振幅和孔（光阑）的大小有关，我们的*振动曲线*将终止于一个半径为$r$的位置带，这个圆环位置上的点发出的次波恰好不能通过圆孔
![[光学-半波带法矢量图解3.png]]
当圆孔的大小合适时，合成的振幅能够取到最大值$E_1$，振幅为自由传播时的两倍。这告诉我们，在屏和光源之间加上阻碍后，轴点$P$的振幅将可能变成原来的**两倍**，光强变成原来的**四倍**；由能量守恒可知其他地方的光强必然会降低。

如果我们构造一个光阑，令奇数半波带透光，而偶数半波带都涂黑（*Fresnel波带片*），就可以极大地增大$P$处的光强

上面是对光屏上中心点的分析，现在考虑每一个点，每一个点能对应的贡献振幅的半波带是不同的
![[光学-半波带法矢量图解4.png]]
孔径的区域内的半波带数量取决于点$P$到点$O$的距离$r_0$。当点$P$沿着中心轴的任一方向移动时，半波带的数量无论增加还是减少都在奇数和偶数之间振荡。因此，光强将经历一系列最大值和最小值，形成的衍射条纹
### Fresnel 透镜
> [!Note] Fresnel透镜
> 光源$S$通过Fresnel波带片形成了一个光斑$P$, 如果把$S, P$分别看成物点、像点，则构成了Fresnel透镜，考虑通过第$m$个半波带（半径为$\rho_m$）的光路的光程和直射光路的光程的差
> $$
> \Delta L = \sqrt{ s^{2}+\rho_m^{2} } + \sqrt{ s'^{2} + \rho_m^{2} } - s - s' = \dfrac{\rho_m^{2}}{2s} + \dfrac{\rho_m^{2}}{2s'}
> $$
> 故其物象关系为
> $$
> \Delta L = m\lambda \implies \dfrac{1}{s} + \dfrac{1}{s'} = \dfrac{m\lambda}{\rho_m^{2}} = \dfrac{\lambda}{\rho_1^{2}}
> $$
> 此我们可以给出Fresnel透镜的焦距（即该**波带片的焦距**）为
> $$
> f = \dfrac{\rho_1^2}{\lambda}
> $$
### 直边衍射
用直刀口将点光源的波前遮住一半，相当于每一个半波带都损失一半，但是相对的相位关系仍然不变，对应的像点的振幅变成原来的一半，亮度变成自由传播时的四分之一（因为没有有圆孔完全遮挡一部分半波带所以直边衍射不能带来中心振幅的增益）
## Fraunhofer衍射
### 形成衍射场的条件
**接收屏幕应该放得足够远**，由[[Representation of Electromagnetic Waves#傍轴条件和远场条件|电磁波的远场条件]]知道接收屏和衍射屏之间的距离$z$需要满足
$$
z \gg \dfrac{a^2}{\lambda}
$$
其中$a$为衍射屏的线度，可取为孔径大小

接收屏幕上能形成Fraunhofer衍射图样的几何限度$\rho$也需要满足[[Representation of Electromagnetic Waves#傍轴条件和远场条件|电磁波的傍轴条件]]，也就是
$$
\rho \ll z
$$
### 单缝的矢量图解法
![[光学-单缝Fraunhofer衍射.png]]
用矢量图解法来分析屏上一点$P(\theta)$的振幅，该点对应的光程差为
$$
\Delta L = a \sin \theta
$$
对应的相位差为
$$
\Delta \phi = \dfrac{\Delta L}{\lambda}\cdot2\pi= \dfrac{2\pi a}{\lambda} \sin \theta
$$
下图中的(b)和(c)(d)展现了$\Delta \phi = 0$和$\Delta \phi = \pi$的情况，前者振幅矢量均同向，合成的振幅最大；后者振幅矢量会形成一个半圆，合成的振幅大小为这个半圆的直径

![[光学-单缝衍射矢量图示.png]]
再考虑$\Delta \phi = 2k\pi$的点，它们的振幅矢量合成为一个完整的圆，对应的振幅大小为零，相应的$P$点为暗点。这和两束光干涉的情况完全相反，原因在于双缝干涉是离散的两束光波的合成，而在衍射的情况下有无数连续的光束参与了合成

需要注意的是，当$k$不断增大的时候，振幅曲线的半径因为光的衰减会越来越多，故对$\Delta \phi = (2k + 1)\pi, \;k \ge 1$也就是$\Delta L = (k + \dfrac{1}{2})$的点来说，虽然都是亮点，但随着$k$的增大，亮度会越来越低

> [!Note] 上面排除了$k = 0$的情况，这是因为
> 由于$\Delta L = 0$的时候是最亮的点，而$\Delta L= \lambda$的时候是第一个暗点，所以当$\Delta L = \dfrac{\lambda}{2}$的时候其亮度处于二者之间，不能算作暗点；但是对于$k \ge 1$的情况来说，由于其两侧光程差为$\lambda$整数倍的点都是暗点，故视其为亮点
### 单缝衍射的定量分析
#### 光斑位置
考虑$k$级暗纹
$$
\Delta L = a \sin \theta_k = k \lambda \implies \sin \theta_k = k \frac{\lambda}{a} 
$$
设$x$为定义在屏上的坐标，则
$$
x_k = f \tan \theta_k 
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
#### 光斑宽度
定义$k$级亮纹的*角宽度*为$\Delta \theta_k =  \dfrac{\lambda}{a}$, 其中$k \neq 0$. 当$k = 0$时，定义$\Delta \theta_0 = \theta_{+1} - \theta_{-1} = 2 \dfrac{\lambda}{a}$

光斑的几何宽度$\Delta x_k = f \Delta \theta_k$，几何直径$D_k = 2f\Delta \theta_k$

### 单缝衍射因子
定义$\beta = \dfrac{\pi a}{\lambda} \sin \theta$（即$\theta$处相位差的一半）, 通过解Fresnel积分可以得到光强$I$关于$\beta$的分布
$$
\dfrac{I(\theta)}{I(0)} = \left(\dfrac{\sin\beta}{\beta}\right)^2
$$
解得$I(\theta)$的极大值满足$\beta = \tan \beta$
![[光学-单缝衍射因子的极大值.png|500]]
可以近似为极大值出现在$\beta = \pm \left(k + \dfrac{1}{2}\right)\pi$处，作$I\sim \beta$图像
![[光学-单缝衍射光强图像.png|500]]
#### 矩孔衍射的情况
光程差
$$
\Delta L = -(x\sin \theta_1+y\sin \theta_2)
$$
有
$$
I(\theta_1,\theta_2) = I_0 \left(\dfrac{\sin\alpha}{\alpha}\right)^2  \left(\dfrac{\sin\beta}{\beta}\right)^2 
$$
### 衍射反比关系
将角宽度公式$\Delta \theta_k = \Delta \theta =  \dfrac{\lambda}{a}$变形，有
$$
\Delta \theta \cdot a = \lambda
$$
这个反比和[[Wavefront-splitting Interferometer#光场的空间相干性|空间相干性的反比公式]]相似，有如下意义
- 当$a$足够大时，$\Delta \theta$足够小，对应于几何光学极限
- 参与干涉的波源数目越多，出现干涉极大的条件越苛刻，能量也越集中在某个特定的方向上
- 说明衍射具有放大作用，可以用于测量单缝或细丝的宽度或直径

### 斜入射的情况
当平行光以$\theta_0$角斜入射在宽度为$a$的单缝上时，考虑光屏上角位置为$\theta$的点，其光程差由经过单缝前后的两段路径分别贡献
$$
\Delta L = \Delta L_0 + \Delta L_1 = -a\sin \theta_0 + a\sin \theta = a\left( \sin \theta - \sin \theta_0 \right) 
$$
这时候
1. 强度公式基本不变
$$
I(\theta) = I(0) \left(\dfrac{\sin \alpha}{\alpha}\right)
$$
只需要我们修正$\alpha$的定义为
$$
\alpha = \dfrac{\pi a}{\lambda} (\sin \theta - \sin\theta_0)
$$
2. 所以零级中心的位置仍然在几何光学像点处$\theta = \theta_0$，而对于$k$级亮纹则有
$$
\sin \theta_k -\sin \theta_0 = \left( k + \dfrac{1}{2} \right) \dfrac{\lambda}{a}\implies \sin \theta_k = \sin \theta_0 + \left( k + \dfrac{1}{2} \right)  \dfrac{\lambda}{a}
$$
3. 于是可以计算$k$级亮纹的角宽度（注意由于$\theta_0$的存在我们无法假设$\theta \to0$）
$$
\dfrac{\lambda}{a} = \Delta(\sin \theta_k) = \cos \theta_k \Delta \theta_k \implies \Delta \theta_k = \dfrac{\lambda}{a \cos \theta_k} \quad(k\neq0)
$$
特别地当$k = 0$时，$\Delta \theta_0  = \dfrac{2\lambda}{a\cos \theta_0}$，其对于的**半**角宽就是$\dfrac{\lambda}{a\cos \theta_0}$

如果衍射屏前后两侧为不同介质，设前场照明空间折射率为$n_1$，后场衍射空间折射率为$n_2$，则光程差变为$\Delta L = a(n_2\sin \theta - n_1 \sin \theta_0)$，从而有强度公式
$$
I(\theta) = I(0) \left(\dfrac{\sin \alpha}{\alpha}\right), \quad \alpha = \dfrac{\pi a}{\lambda_0} (n_2\sin \theta - n_1\sin\theta_0)
$$
其中$\lambda_0$表示衍射光在真空中的波长，注意这里零级亮纹的位置$\theta_0'$需要满足
$$
\alpha = 0 \implies n_2\sin \theta_0' - n_1\sin \theta_0 = 0
$$
即$\theta_0'$为斜入射光源通过衍射屏后的折射角，而其他级亮条纹的位置为
$$
n_2\sin \theta_k - n_1 \sin \theta_0 = \left( k + \dfrac{1}{2} \right)  \dfrac{\lambda_0}{a} \implies \sin \theta_k = \dfrac{n_1}{n_2} \sin \theta_0 + \left( k + \dfrac{1}{2} \right) \dfrac{\lambda_0}{n_2a} 
$$
它们的角宽度
$$
\Delta \theta_k = \dfrac{\lambda_0}{n_2a\cos \theta_k} \quad (k \neq 0)
$$
特别地对于零级条纹，其角宽度
$$
\Delta \theta_0' = \dfrac{2\lambda_0}{n_2 a\cos \theta_0'} = \dfrac{2\lambda_0}{a\sqrt{ n_2^2 - n_1^2\sin^2 \theta_0 }}
$$
只有它**半**角宽才和其他的条纹有一样的形式，即$\dfrac{\lambda_0}{a\sqrt{ n_2^2 - n_1^2\sin^2 \theta_0 }}$
### 光学仪器的分辨本领
#### Airy斑
通过求解Fresnel积分我们可以得到Frauhofer圆孔衍射下（前面讨论的都是二维的情况）主极大的**半**角宽
$$
\Delta \theta_0 = 0.61 \dfrac{\lambda}{a} = 1.22 \dfrac{\lambda}{D}
$$
这个主极大的光斑被称为*Airy斑*，其中$D$为衍射孔的直径
> [!Note] 相机的光圈数
> 相机的光圈数定义为镜头焦距和最大光圈直径的比值，即$\dfrac{f}{D}$. 例如，如果镜头的最大光圈直径是$10$mm,焦距是$50$mm，那么光圈数就是$50/10 = 5$，通常记为$f/5$
> 
> 光圈数越小，表示光圈越大，进光量越多。光圈数越大，表示光圈越小，进光量越少
> 
> 标准的光圈级数为:$f/1, f/1.4, f/2, f/2.8, f/4, f/5.6, f/8, f/11, f/16, f/22, f/32$。这些数值是相邻级数的二倍关系
#### Rayleigh判据
##### 望远镜的像分辨能力
当一个圆斑像的中心刚好落在另一圆斑像的边缘（第一暗纹）上时，被认为刚刚能被分辨。由此定义的最小分辨角为：
$$
\delta \theta_m = 1.22 \dfrac{\lambda}{D}
$$
由此可知，如果要提高望远镜的分辨本领，光提升它的放大率是无效的，因为它在放大像的同时把衍射光斑也一起放大了。所以要提升望远镜的分辨率，最有效的方法是增大它物镜的口径

另一方面，望远镜的放大率太小显然也是不行的，因为这将无法最大地利用它的分辨本领。因此，我们在选择目镜时，需要能使总放大率能将仪器的最小分辨角放大到人眼所能分辨的最小角度$1'\approx 2.9 \times 10^{-4}\;\mathrm{rad}$，由此我们可以定义望远镜的有效视角放大率
$$
M_m = \dfrac{\delta \theta_e}{\delta \theta_m}
$$
> [!Tip] 回忆
> [[Optical Systems#望远镜|望远镜的放大率公式]]为
> $$
> M = \dfrac{f_O}{f_E}
> $$
##### 显微镜的像分辨能力
![[光学-显微镜的分辨本领.png]]
显微镜的最小分辨距离为
$$
\delta y_m = \dfrac{0.61 \lambda}{n \sin u} = 0.61 \dfrac{\lambda}{\mathrm{N.A.}}
$$
其中$\mathrm{N.A.} = n \sin u$称为显微镜的[[Numerical Aperture|数值孔径]]，这里不取$1.22$而取$0.61$是因为$y$表示某处像点和中心点的距离，对应于Airy斑的半径。由此我们可以给出提升显微镜分辨本领的方法
- 可以通过油浸增大显微镜的数值孔径，从而提升它的分辨能力
- 也可以通过使用短波长的光来提升分辨能力

由于人眼可以分辨的最小距离
$$
\delta y_e = s_0 \delta \theta_e = 25 \mathrm{cm} \times \left( 2.9 \times 10^{-4} \mathrm{ rad} \right) = 72.5 \mathrm{\mu m}
$$
故我们也可以定义*显微镜的有效放大率*
$$
M = \dfrac{\delta y_e}{\delta y_m}
$$
> [!Tip] 回忆
> [[Optical Systems#显微镜|显微镜的放大率公式]]为
> $$
> M = V_O M_E = -\dfrac{\Delta}{f_O}\dfrac{s_0}{f_E}
> $$

### 多缝衍射，$\alpha,\beta$的定义，在特殊情况下（不均匀间距）
定义$d$为缝和缝之间的距离（即缝的空间周期），每个缝的宽度为$a$，考虑$\theta$处的衍射
![[光学-多缝衍射强度公式推导.png]]
设$\alpha = \dfrac{\pi a}{\lambda} \sin \theta$，则每一个缝贡献的振幅为$a_\theta = a_0 \left( \dfrac{\sin \alpha}{\alpha} \right)$，而每相邻两个缝之间的的光程差为$\Delta L = d \sin \theta$，对应的相位差就是$\delta = \dfrac{2\pi d}{\lambda} \sin \theta$，再设$\beta = \dfrac{\delta}{2} = \dfrac{\pi d}{\lambda}\sin \theta$，则我们可以作出上面的振幅矢量合成图（假设一共有$N$个缝）

设半径$R = \overline{CO} = \overline{CB_N}$，则有
$$
a_{\theta} = 2R\sin \beta,\quad A_\theta = 2R\sin N\beta \implies A_\theta = a_\theta \dfrac{\sin N \beta}{\sin \beta}
$$
得到光强公式
$$
I_\theta = A_\theta^2  =a_0^{2} \left( \dfrac{\sin \alpha}{\alpha} \right)^{2}  \left( \dfrac{\sin N \beta}{\beta} \right) ^{2}
$$
其中$\left( \dfrac{\sin \alpha}{\alpha} \right)$为*单缝衍射因子*，$\left( \dfrac{\sin N\beta}{\sin \beta} \right)$为*缝间干涉因子*，它们的图像分别如下面的(a),(b)所示，(c)是它们合成后的图像
![[光学-多缝衍射强度.png]]
一个对(c)图像的描述是
- 微观决定宏观 - 缝的大小决定图样的宏观结构（外包络）
- 宏观决定微观 - 缝和缝的间距决定图样的微观结构（每一个次极大）

类似于多缝干涉，多缝衍射的图样存在*主极大*（所以$\Delta L=k\lambda$的时候对应得是干涉的极大，而不是衍射的极小）
$$
d\sin \theta = k \lambda \implies \sin \theta = k \dfrac{\lambda}{a},\quad k = 0, \pm1, \pm2, \ldots 
$$
考虑图样的暗点，也就是缝间衍射因子的零点，我们可以解得
$$
\dfrac{\sin N \beta}{\sin \beta}=0 \implies N \beta = m\pi, \beta \neq n\pi
$$
又因为$\beta = \dfrac{\pi d}{\lambda}\sin \theta$，所以我们得到零点的位置
$$
\sin \theta = \left( k + \dfrac{m}{N} \right)  \dfrac{\lambda}{d},\quad k = 0,\pm1,\pm2, \ldots ;m = 1,2, \ldots ,N-1
$$
其中$m=N$的情况恰好对应于主极大，每两个主极大之间有$N-1$个暗点，而每两个相邻的暗线之间都有一个*次极大*，也就是说每两个主极大之间都有$N-2$个次极大

当某一个主极大恰好被单缝衍射因子调制为$0$的时候，我们称这种情况为*缺级*，它满足
$$
\sin \theta = k \dfrac{\lambda}{a} = k' \dfrac{\lambda}{d}
$$
### 光栅方程
### 光栅光谱仪（一般会给公式，除了能直接用光栅方程给出来的）
# Fourier光学
### 概念题：哪些是衍射屏，哪些不是
### 理解概念为主
### 写衍射屏函数
### Abbe成像原理

# 晶体光学
## 旋光
## 光物质作用
### 除了公式之外的基本原理
# 量子光学
## 黑体辐射
## 光电效应
## 激光的基本概念