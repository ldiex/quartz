交流电源以相同的频率，不同的相位工作的电路或者系统被称为**多相系统**. 三相系统中的发电机包括三个幅度和频率都相同但是相位彼此相差$120^{\circ}$的绕组，我们先只考虑对称的三相电压

## 对称三相电压
考虑对称的通过$Y$形联结的三个电压源，电压$\boldsymbol V_{an}, \boldsymbol V_{bn}, \boldsymbol V_{cn}$分别表示线路$a,b,c$和中性线$n$之间的电压，这些电压被称为**相电压**. 对称的三相电压意味着
$$
\begin{aligned}
\boldsymbol V_{an} + \boldsymbol V_{bn} + \boldsymbol V_{cn} = 0 \\
\left|{\boldsymbol V_{an}}\right| = \left|{\boldsymbol V_{bn}}\right| = \left|{\boldsymbol V_{cn}}\right|
\end{aligned}
$$
而输电线和输电线之间的电压被定义为**线电压**
### 三相电流
**相电流**: 电源或负载的各相电流
**线电流**: 输电线上的电流

在$Y$形联结的情况下，可以推导得到
$$	
\boxed{V_L = \sqrt{3} V_P,\;I_L = I_P}
$$
**且线电压的辐角超过相电压的辐角$30^{\circ}$**
对于$\Delta$形联结的三相电压也是类似的，但是在这种情况下拓扑上我们无法连出一条中性线. 此时也有
$$
\boxed{V_L = V_P,\;I_L = \sqrt{3}I_P}
$$
**且线电流的辐角落后相电流的辐角$30^{\circ}$**

## 对称三相负载
连接方式和对称三相电压类似，设$\boldsymbol Z_{Y}, \boldsymbol Z_{\Delta}$为两种联结方式中每一相的负载阻抗，那么可以通过如下等式实现两种联结方式的等效相互转换
$$
\boldsymbol Z_{Y} = \frac{1}{3} \boldsymbol Z_{\Delta} ;\; \boldsymbol Z_{\Delta} = 3 \boldsymbol Z_{Y}
$$
## 计算说明
欧姆定律: **相电压**$=$**相电流**$\times$负载阻抗 （计算是在**某一相**上进行的）
**每相功率**（平均功率）: $P_p = V_p I_p \cos(\theta_v - \theta_i)$
**总功率**: $P = 3P_p$

