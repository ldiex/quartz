# 表格积分法
## 终止于$0$

求解$\displaystyle \int (x^2 + x) e^x \mathrm{d} x$
将上面的两个部分写成两行，对第一行**求导**，另一行**积分**，直到第一行变为$0$

| $x^2 + x$ | $2x +1$ | $2$   | $0$   |
| --------- | ------- | ----- | ----- |
| $e^x$     | $e^x$   | $e^x$ | $e^x$ |

第一行第一列与第二行**第二列**相乘，第一行第二列与第二行第三列相乘，第一行第三列与第二行第四列相乘. **要注意的是，这里的交叉相乘还需要带符号，依次为正负正负正…以此类推**. 最后，将相乘结果相加，整理即可得到最终的解
$$
+\left ( \left ( x^{2}+x \right )\cdot e^{x} \right )-\left ( \left ( 2x+1 \right )\cdot e^{x} \right )+\left ( 2\cdot e^{x} \right )=\left ( x^{2}-x+1 \right )\cdot e^{x}+C
$$
## 终止于某列的乘积为第一列的常数倍
求解$\displaystyle \int e^{3x} \sin 2x \mathrm{d} x$

| $e^{3x}$  | $3e^{3x}$             | $9e^{3x}$             |
| --------- | --------------------- | --------------------- |
| $\sin 2x$ | $-\dfrac{\cos 2x}{2}$ | $-\dfrac{\sin 2x}{4}$ |
于是有
$$
\int e^{3x}\sin2x\mathrm{d} x=e^{3x}(-\frac{\cos2x}{2})-3e^{3x}(-\frac{\sin2x}{4})+9(-\frac{1}{4})\int e^{3x}\sin 2x\mathrm{d} x
$$
即
$$
\int e^{3x}\sin2x\mathrm{d} x=\frac{1}{13}e^{3x}(3\sin2x-2\cos2x)+C
$$


