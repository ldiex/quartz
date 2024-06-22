## Faraday 定律
$$
\mathcal{E} = -\dfrac{\mathrm{d} {\Psi}}{\mathrm{d} {t}} = -N \dfrac{\mathrm{d} {\Phi}}{\mathrm{d} {t}}
$$
## 互感和自感
### 互感
$$
\mathcal{E}_1 = -M_{21} \dfrac{\mathrm{d} {I_2}}{\mathrm{d} {t}} ; \; \mathcal{E}_2 = -M_{12} \dfrac{\mathrm{d} {I_1}}{\mathrm{d} {t}} ;
$$
其中
$$
M_{12} = M_{21} = M
$$
为**互感系数**

### 自感
$$
\mathcal{E} = -L\dfrac{\mathrm{d} {I}}{\mathrm{d} {t}} 
$$
其中$L$为**自感系数**

### 关系
在没有漏磁的情况下
$$
M = \sqrt{L_1L_2}
$$
### 线圈串联
顺接
$$
L = L_1 + L_2 + 2M = L_1 + L_2 + 2\sqrt{L_1L_2}
$$
反接
$$
L = L_1 + L_2 + 2M = L_1 + L_2 - 2\sqrt{L_1L_2}
$$
### 感应磁能
$$
\begin{aligned}
W_m& = \frac{1}{2}L_1I_1^2 + \frac{1}{2}L_2I_2^2 +\frac{1}{2}M_{12}I_1I_2 + \frac{1}{2}M_{21}I_2I_1 \\
&= \frac{1}{2}L_1I_1^2 + \frac{1}{2}L_2I_2^2 + MI_1I_2
\end{aligned}
$$
## 暂态过程
### LR 电路
$$
i = \frac{\mathcal{E}}{R} (1 - \exp(-\frac{R}{L}t)),\; \tau = \frac{L}{R}
$$
### RC 电路
$$
\begin{cases}
q = C\mathcal{E} (1 - \exp(-\frac{1}{RC}t)) &,\text{充电} \\
q = C\mathcal{E}\exp(-\frac{1}{RC}t) &,\text{放电}
\end{cases};\;
\tau = RC
$$
 
