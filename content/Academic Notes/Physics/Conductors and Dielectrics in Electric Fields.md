## 导体
1. 导体体内没有自由电荷, 导体是一个等势体, 体内电场强度恒为$\boldsymbol 0$
2. 导体以外靠近其表面的地方的电场强度和表面垂直, 大小为$E_n = \dfrac{\sigma_e}{\varepsilon_0}$
3. 导体表面尖锐的地方（曲率$>0$）电荷密度大, 平坦的地方（曲率$\approx 0$）电荷密度较小, 而内凹的地方（曲率$<0$）电荷密度最小
### 导体腔
1. 导体腔内有其他带电体时, 在静电平衡的状态下, 导体壳的内表面所带电荷与腔内电荷的代数和为$0$
2. 导体壳内的带电体不受导体壳外的电场影响, 也就是说如果导体壳内有一个点电荷, 那么它在导体腔内的电场分布和在真空中的电场分布是一致的
3. 导体壳外的电场不受导体壳内的带电体的位置影响, 只和导体壳的几何形状和导体壳内带电体的总电荷量有关
4. 如果导体壳接地, 那么无论导体壳内的带电体的电荷量和位置如何, 导体壳外的电场均不受其影响
## 电容
### 平行板电容器
$$
C = \frac{\varepsilon_0S}{d}
$$
### 同心球形电容器
$$
C = \frac{4\pi\varepsilon_0 R_A R_B}{R_B - R_A}
$$
### 同轴圆柱形电容器
$$
C = \frac{2\pi\varepsilon_0 L}{\ln \dfrac{R_B}{R_A}}
$$
### 电容器储能
$$
W_e =\frac{1}{2}QU = \frac{1}{2}CU^2 = \frac{Q^2}{2C}
$$
## 电介质
### 电极化强度
$$
\boldsymbol P = \frac{N \boldsymbol p}{V}
$$
电极化强度的通量
$$
\oint_S \boldsymbol P \cdot \mathrm{d} {\boldsymbol S} = - \sum_{\text{enclosed}} q' 
$$
和表面极化电荷面密度的关系
$$
\sigma_e^{'} = \boldsymbol P \cdot \hat{\boldsymbol n} = P_n 
$$
### 线性介质
$$
\boldsymbol P = \chi_e \varepsilon_0 \boldsymbol E = \chi_e \varepsilon_0 (\boldsymbol E_0 + \boldsymbol E')
$$
其中$\chi_e$为**极化率**
### 电位移矢量
由
$$
\begin{aligned}
\oint_S \boldsymbol P \cdot \mathrm{d} {\boldsymbol S} &= -\sum q' \\
\oint_S \boldsymbol E \cdot \mathrm{d} {\boldsymbol S} &= \frac{1}{\varepsilon_0} \sum(q + q')
\end{aligned}
$$
得到
$$
\oint (\varepsilon_0 \boldsymbol{E} + \boldsymbol P) \cdot \mathrm{d} {\boldsymbol S} = \sum q
$$
令$\boldsymbol D:=\varepsilon_0 \boldsymbol E + \boldsymbol P$, 则有
$$
\oint \boldsymbol D \cdot \mathrm{d} {\boldsymbol S} = \sum q
$$
$\boldsymbol D$也可以写为
$$
\boldsymbol D = (1 + \chi_e) \varepsilon_0 \boldsymbol E = \varepsilon_r \varepsilon_0 \boldsymbol E
$$
**解题思路**
$$
\text{边界条件} \to \boldsymbol D \to \boldsymbol E \to \boldsymbol P \to \begin{cases}
\sigma' = P_{1n} - P_{2n} & \text{极化电荷} \\
\sigma_0 = D_{1n} - D_{2n} = 0 & \text{自由电荷} \\
\sigma = \varepsilon_0 (E_{1n} - E_{2n}) & \text{总电荷}
\end{cases}
$$

