电路的转移函数$\boldsymbol H (\omega)= \dfrac{\boldsymbol Y (\omega)}{\boldsymbol X (\omega)}$，这里的$\boldsymbol X (\omega), \boldsymbol Y (\omega)$是电路的有关相量
## $Q$值的第一种意义
### LCR串联电路
在一个LCR串联电路中，$\boldsymbol H (\omega)= \dfrac{\boldsymbol U (\omega)}{\boldsymbol I (\omega)} = \boldsymbol Z (\omega) = j\omega L -\dfrac{j}{\omega C} + R$，当$\omega = \omega_0 = \sqrt{LC}$时，$\boldsymbol H(\omega)$的振幅是最小的，也就意味着电路是纯电阻电路且损耗最小，这是一种谐振状态

此时，电路的品质因数被定义为

$$
Q := 2\pi \frac{电路存储的峰值能量}{电路在一个周期内消耗的总能量} = 2\pi\frac{\dfrac{1}{2}LI_0^2}{(\frac{I_0}{\sqrt{2}})^2 R \cdot \dfrac{2\pi}{\omega_0}} = \frac{\omega_0 L}{R}
$$

其中$I_0$是电路中的峰值电流；由谐振条件，$Q$也可以被写为$\dfrac{1}{\omega_0 CR}$
### LCR并联电路
这时候为了方便，可以定义$\boldsymbol H(\omega) = \dfrac{\boldsymbol I(\omega)}{\boldsymbol U(\omega)} = \boldsymbol Y(\omega) = - \dfrac{j}{\omega L} + \dfrac{\omega C}{j} + \dfrac{1}{R}$, 也在$\omega = \omega_0 = \sqrt{LC}$时，电路的导纳的振幅最小，电路是纯电阻电路且损耗最大，达到谐振状态

同样地，这时候电路的品质因数是
$$
Q = 2\pi \frac{电路存储的峰值能量}{电路在一个周期内消耗的总能量} = 2\pi\frac{\dfrac{1}{2}CU^2}{\dfrac{(\frac{U}{\sqrt{2}})^2}{R} \cdot \dfrac{2\pi}{\omega_0}} = \omega_0CR
$$

### 元件$Q$值

元件的$Q$值$:=\dfrac{P_{无功}}{P_{有功}}$, 在电路的品质因数$Q_r$中由$R = r_C + r_R$知对于串联电路有
$$
\frac{1}{Q_r} = \frac{r_C + r_L}{\omega_0 L} = \frac{r_L}{\omega_0 L} + r_C \omega_0 C = \frac{1}{Q_L} + \frac{1}{Q_C} 
$$
同时，我们定义**耗散因数**
$$
\tan \delta = \frac{P_{有功}}{P_{无功}} = \frac{1}{Q}
$$
其中$\delta$称为**损耗角**
## $Q$值的第二种意义
**半功率频率：** 在频率$\omega = \omega_1, \; \omega_2$时，电路消耗的功率是最大功率的一半，可以通过设置$Z = \sqrt{2} R$得到. 定义**带宽**为两个半功率频率之差$B = \omega_2 - \omega_1$，经过计算可以得到
$$
	\boxed{B = \frac{R}{L} = \frac{\omega_0}{Q}}
$$
也就是说，电路的$Q$值越大，谐振电路的带宽更窄、频率选择性更好

在$Q\ge 10$时，可以认为$\omega_1, \; \omega_2$关于$\omega_0$对称，此时可以有

$$
	\omega_1 \approx \omega_0 - \frac{B}{2}; \; \omega_2 \approx \omega_0 + \frac{B}{2}
$$
## $Q$值的第三种意义
在串联LCR谐振电路中考虑用转移函数表示电压增益
$$
	H(\omega) =  \frac{Z_C}{0 + R} = \frac{1}{\omega_0 C R} = \frac{Z_L}{0 + R} = \frac{\omega_0 L}{R} = Q
$$
这里的$Q$表示了电压的增益


