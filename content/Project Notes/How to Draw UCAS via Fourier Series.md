> [!summary] 致谢
> - 灵感源自3Blue1Brown的制作的关于Fourier变换的[科普视频](https://www.youtube.com/watch?v=r6sGWTCMz2k)
> - 在生成级数的过程中有参考[Reddit](https://www.reddit.com/r/3Blue1Brown/comments/cvpdn7/make_your_own_fourier_circle_drawings/)论坛上给出的部分Golang代码

> [!info] 声明
> 本网页和整个基于[Quartz](https://quartz.jzhao.xyz/)的[笔记仓库](https://ldiex.github.io/quartz)均为作者自己的部分[Obsidian](https://obsidian.md/)笔记在云端的一个备份，并不包含在这次计算机科学导论的作业中，而仅用来对此作业的数学原理作出一个简单说明

考虑[[Fourier Transformation#Fourier 级数的复数形式|Fourier级数的复数形式]]，我们总可以把一个周期函数写成
$$
f(x) = \sum_{n =-\infty}^{+\infty} d_n \mathrm{e}^{\mathrm{i}n\omega_0x},\text{ where }d_n = \dfrac{1}{T} \int_0^{T}\mathrm{e}^{-\mathrm{i}n\omega_0x} f(x) \mathrm{d} x
$$
在二维的情况下，我们把$f(x)$矢量化
$$
\boldsymbol f(x) = \sum_{n =-\infty}^{+\infty} \boldsymbol d_n \mathrm{e}^{\mathrm{i}n\omega_0x},\text{ where }\boldsymbol d_n = \dfrac{1}{T} \int_0^{T}\mathrm{e}^{-\mathrm{i}n\omega_0x} \boldsymbol f(x) \mathrm{d} x
$$
我们的目标是通过待绘制的图样来得到$d_n$，由于点阵图样分辨率低、描述需要的参数多，并不适合用Fourier级数来拟合，所以我们采用图样更加光滑、需要参数少且可以无损放大的SVG格式来表示图样（[有人](https://www.reddit.com/r/3Blue1Brown/comments/fjxfvk/b%C3%A9zier_curves_and_fourier_transforms/)也是这样想的）。在SVG格式的[文档](https://developer.mozilla.org/en-US/docs/Web/SVG/Tutorial/Paths)中，一条曲线路径`Path`是用[Bézier曲线](https://en.wikipedia.org/wiki/B%C3%A9zier_curve)描述的：

> The cubic curve, `C`, is the slightly more complex curve. Cubic Béziers take in two control points for each point. Therefore, to create a cubic Bézier, three sets of coordinates need to be specified.
> ```
> C x1 y1, x2 y2, x y
> (or)
> c dx1 dy1, dx2 dy2, dx dy
> ```
> The last set of coordinates here (`x`, `y`) specify where the line should end. The other two are control points. (`x1`, `y1`) is the control point for the start of the curve, and (`x2`, `y2`) is the control point for the end. The control points essentially describe the slope of the line starting at each point. The Bézier function then creates a smooth curve that transfers from the slope established at the beginning of the line, to the slope at the other end.
> 

故考虑一条三阶Bézier曲线
$$
\boldsymbol {B} (t)=(1-t)^{3}\boldsymbol {P} _{0}+3(1-t)^{2}t\boldsymbol {P} _{1}+3(1-t)t^{2}\boldsymbol {P} _{2}+t^{3}\boldsymbol {P} _{3},\ 0\leq t\leq 1
$$
写成关于$t$的函数
$$
\boldsymbol {B}(t) = (-\boldsymbol P_1 + 3 \boldsymbol P_2 -3\boldsymbol P_3+\boldsymbol P_4) t^3 + 3(\boldsymbol P_1-2\boldsymbol P_2 + \boldsymbol P_3) t^{2} + 3(-\boldsymbol P_1 + \boldsymbol P_2)t
$$
我们可以把待绘制的图案切成一条条的Bézier曲线前后连接，在时域上就是每一条Bézier曲线对应一个起始时间$t_{i,k}$和$t_{f,k}$，其中$k = 1,2, \ldots ,K$，此时就有
$$
\mathscr F\left\{ t_m^n \right\}  =   \sum_{k =1}^K\dfrac{1}{2\pi(t_{f,n}-t_{i,n})^m}\int_{t_{i,n}}^{t_{f,n} } (t-t_{i,n})^m e^{-\mathrm{i}nt} \mathrm{d}t
$$
从而得到
$$
\boldsymbol d_m = (-\boldsymbol P_1 + 3 \boldsymbol P_2 -3\boldsymbol P_3+\boldsymbol P_4) \mathscr F\left\{ t_m^3 \right\} + 3(\boldsymbol P_1-2\boldsymbol P_2 + \boldsymbol P_3) \mathscr F\left\{ t_m^2 \right\} + 3(-\boldsymbol P_1 + \boldsymbol P_2) \mathscr F\left\{ t_m^1 \right\}
$$
由此我们成功从SVG图像中获得了绘图所需的Fourier系数