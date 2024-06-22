# 薄膜干涉
薄膜干涉存在于折射光和反射光交迭的所有区域，但有实际意义的主要有两种，分别定位于薄膜表面和无限远

- 等厚条纹：厚度不均匀薄膜表面的干涉场
- 等倾条纹：厚度均匀薄膜无穷远处的干涉场

## 等厚条纹
### 光程差
![[光学-等厚条纹.png]]
$$
\begin{aligned}
\Delta L(P)& =(QABP)-(QP)=(QA)-(QP)+(ABP)  \\
&=(ABP)-(CP)\thickapprox(ABP)-2h\tan i\sin i_1 \\
&\approx2nh/\cos i-2nh\sin^2i/\cos i \\
&\approx2nh\cos i
\end{aligned}
$$
### 干涉条纹
$$
\begin{cases}h=\dfrac{k\lambda}{2n\cos i} & 极大 \\\\h=\dfrac{(2k+1)\lambda}{4n\cos i}& 极小\end{cases}
$$
**薄膜表面沿等厚线分布的干涉条纹称为等厚干涉条纹**
相邻条纹的厚度差$h = \dfrac{\lambda}{2n}$

## Newton 环
![[光学-Newton环.png]]
由圆幂定理
$$
r_k^2 = h_k(2R-h_k) \approx 2Rh_k
$$
又光程差
$$
\Delta = 2\times 1 \times h_k = k\lambda
$$
故
$$
r_k^2 = kR\lambda \implies r_k = \sqrt{kR\lambda}
$$
因为存在半波损失，上面的$r_k$给出的是暗条纹，Newton环的中心是暗条纹
## 等厚干涉条纹的观测方法
严格的等厚干涉要求点光源、正入射。但扩展光源、斜入射，用眼睛也能观察到干涉现象。主要是眼睛的瞳孔对光束进行了限制，只是干涉的结果会受到一定的影响

### 条纹偏离等厚线
![[光学-等厚条纹偏移.png]]
### 反衬度降低
眼睛瞳孔限制扩展光源参与干涉的区域。光源不同处的$i$不同， $h$越大，反衬度越低。

## 薄膜的颜色、增透膜和高反膜
### 薄膜的颜色
干涉导致不同波长光的反射率不同
### 增透膜
![[光学-增透膜.png]]
要求$n_1 < n < n_2$
当$n = \sqrt{n_1n_2}$时完全消除反射光
### 高反膜
$n_1 < n > n_2$

## 等倾条纹
$h$固定，但是$i$变化
![[光学-等倾干涉.png]]

光程差
$$
\Delta = 2nh\cos i =k\lambda
$$
故
$$
\cos i_k = \dfrac{k\lambda}{2nh}
$$
### 等倾干涉条纹

由薄膜表面等倾角光线形成的干涉条纹称为*等倾干涉条纹*

倾角相等的条纹会形成一个锥，在无穷远的光屏上（即某个凸透镜的焦平面）就是同心圆

中心级次高、边缘级次低。$h$增大，条纹从中心生出并向外扩展；$h$减小，条纹向中心会聚并消失于中心
### 观察等倾条纹时扩展光源的作用
光源上各点形成完全一样的干涉图样（强度相加而不是振幅相加），其效果是**提高干涉图样的亮度，有益无害**。但是拓展光源对观察等厚条纹会有影响

## 薄膜干涉的定域问题
### 点光源照明
上下两束光交迭的任何区域都有干涉条纹存在，干涉条纹是非定域的
### 扩展光源照明
只在上下表面反射的两束光交迭的部分区域内可看到干涉条纹，这种条纹称为*定域干涉条纹*

定域条纹的范围称为*定域深度*，定域深度内有一曲面， 在此曲面上干涉条纹的反衬度最大。该曲面称为*定域中心*

干涉条纹的反衬度随偏离定域中心而逐步下降，直至超出定域范围，反衬度降为$0$而无法辨认

厚度均匀的薄膜，定域中心在无限远； 厚度不均匀的薄膜，定域中心在上下表面附近。 **只要对光源宽度有一定的限制**（如肉眼观察时眼睛的瞳孔），即可使薄膜表面进入定域深度之内

无论是等厚干涉，还是等倾干涉，既可在薄膜的上方，也可在薄膜的下方观察到干涉条纹，只是反衬度不同（ 通常为互补）

# Michelson 干涉仪
## 结构
![[光学-Michelson干涉仪.png]]
一种分振幅干涉装置，其中光源、两个反射镜和接收器四者完全分开，各据一方，便于在光路中安插其它器件。可以实现等厚干涉、等倾干涉及观察条纹的变动情况，同时可方便地进行各种精密测量。迈克尔孙干涉仪几乎是所有现代干涉仪器的原型。

## 干涉条纹
### 等倾条纹
较远：密而弱，中心斑点较小 
较近：疏而强，中心斑点较大
重合：中心斑点扩大到整个视场
向下：条纹不断缩进中心
向上：条纹不断由中心生出

![[光学-Michelson-等倾条纹.png]]
### 等厚条纹
较远：几乎看不到条纹
较近：弯曲的条纹 
相交：直的条纹

朝曲率小的方向移动，反衬度不断变大 
朝曲率大的方向移动，反衬度不断降低
![[光学-Michelson-等厚条纹.png]]
#### 白光照明
用于判断两臂是否等光程

重合：$0$级暗纹不色散，旁边为对称排列的明暗不同的彩色条纹，此时两臂无光程差

## 光源非单色性对干涉条纹的影响
### 如钠黄光这样的双线结构
$$
\gamma(\Delta L)=\left|\cos\!\left(\frac{\Delta k\Delta L}2\right)\right|
$$
其中$\Delta L$为光程差，$\Delta k$为波数差

条纹的反衬度随光程差作周期振动

### 单色线宽

# 光场的时间相干性
时间相干性是指光源同一点在不同时刻发出的光波之间的相干性

时间相干性可以用*相干时间*或*相干长度*来表示。相干时间是指光源原子的平均发光时间间隔, 相干长度是在相干时间内光波在真空中传播的距离

时间相干性越好,意味着光源发出的光波在不同时刻的相位关系越稳定,相干时间和相干长度越长

相干时间和频率差的乘积约等于$1$

$$
\tau_0 \Delta \nu \approx 1
$$
这是*时间相干性的反比公式*
由此可以得到相干长度
$$
l_0 = c\tau_0 = \dfrac{1}{\Delta \nu} = \dfrac{\lambda_2\lambda_1}{\lambda_2 - \lambda_1} = \dfrac{{\bar \lambda}^2}{\Delta \lambda}
$$

![[光学-时间相干性.png]]

理想的单色点光源具有完全的时间相干性,而实际光源由于有限的线宽和谱宽, 只能表现出部分时间相干性。即光源的单色性越高,其时间相干性越好

## 光场相干性小结
### 产生原因
空间相干性来源于扩展光源不同部分发光的独立性
时间相干性来源于光源发光过程在时间上的断续性
### 结果
空间相干性主要表现在波场的横向（波前）上，集中体现在分波前干涉装置中；
时间相干性主要表现在波场的纵向（波线）上，集中体现在分振幅干涉装置中

### 反比公式
空间相干性 $\Delta \theta b \sim \lambda$
时间相干性 $\tau_0 \Delta \nu \sim 1$

相干区域和相干时间都不是一个绝对的界限，实际上相干区域和相干时间内也有非相干的成分，而相干区域和相干时间之外，也有相干的成分，只是主导地位的不同，部分相干是最为普遍的，而反衬度则是相干程度的一种度量

