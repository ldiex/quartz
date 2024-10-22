# 分波前干涉装置
利用光具组将同一列波分解, 使它们经过不同的途径后重新相遇, 由于这样的两列波由同一列波分解而来, 它们频率相同, 位相差稳定, 振动方向也可做到基本平行, 因而满足相干条件, 能产生干涉图样. 实际的干涉装置按分解波列的方法不同分为两种: 

- **分波前法**: 将点光源的波前分割为两部分的波列分解法称为分波前法, 杨氏双缝是分波前法的典型代表
- **分振幅法**: 利用两种媒质的界面将振幅分解为反射和透射两部分的波列分解法称为分振幅法. 分振幅法的典型代表是薄膜干涉和迈克尔逊干涉仪 见[[Amplitude-splitting Interferometer | 分振幅干涉装置]]
## 各种分波前干涉装置
### 杨氏双缝
![[光学-杨氏双缝-2.png]]

### Fresnel 双面镜
![[光学-Fresnel双面镜.png]]
### Fresnel 双棱镜
![[光学-Fresnel双棱镜.png]]
### H.Lloyd 镜
![[光学-Lloyd镜.png]]
## 条纹的形状和间距
均为近似的一组平行直线, 间距都可以转化为杨氏双缝的公式
$$
\Delta x = \dfrac{D}{d}\lambda
$$
## 干涉条纹的移动
关键是确定零级亮条纹的位置（相位差为$0$的点）
![[光学-中心条纹的移动.png]]
中心条纹移动的距离$\delta x' = \dfrac{D}{R}\delta x$
## 光源宽度对干涉条纹反衬度的影响
由[[Interference of Waves#杨氏（T. Young, 1801）双缝实验| 杨氏双缝实验]] , 对于点光源, 条纹的亮度分布为
$$
I(x') = I_0 \left[1 + \cos \dfrac{kd}{D}x'\right]
$$
对于拓展光源, 上面的每一个点都独立形成干涉条纹, 由于它们之间并不相干, 所以最终的亮度分布就是各个点光源的亮度分布的叠加
$$
\begin{gathered}
I(x^{\prime}) \begin{aligned}=I_0\int_{-b/2}^{b/2}\bigg[1+\cos\frac{kd}{D}\bigg(\left.x'-\frac{D}{R}x\right)\bigg]dx\end{aligned} \\
=I_0b{\left[1+\frac{\sin\mu}\mu\cos\frac{kd}Dx^{\prime}\right]} 
\end{gathered}
$$
其中
$$
\mu= \dfrac{kd}{R}\dfrac{b}{2}
$$
于是
$$
I_M=I_0b{\left[1+\left|\frac{\sin\mu}\mu\right|\right]}\quad I_m=I_0b{\left[1-\left|\frac{\sin\mu}\mu\right|\right]}
$$
可计算反衬度为
$$
\gamma = \left|{\dfrac{I_M - I_m}{I_M + I_m}}\right| = \left|{\dfrac{\sin \mu}{\mu}}\right|
$$
![[光学-拓展光源反衬度.png]]
$\gamma$的第一极小出现在$\mu = \pi$处, 对应的光源宽度为$b = R \lambda / d$, 定义为光源的*极限宽度*. 此时有$\gamma = 0$

# 光场的空间相干性
![[光学-空间相关性.png]]
固定光源的宽度$b$不变, 考虑相干场的横向线度（把两个缝看作两个探针）, 最大线度约为
$$
d \approx \dfrac{R\lambda}{b}
$$
最大角宽度约为
$$
\Delta \theta \approx \dfrac{d}{R} = \dfrac{\lambda}{b}
$$
由此得到空间相干性的反比公式
$$
\Delta \theta b \sim \lambda
$$
即**相干场对光源的角宽度反比于光源的宽度, 二者的乘积与波长相当**

