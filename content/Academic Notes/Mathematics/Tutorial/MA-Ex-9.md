# 高阶偏导数练习
## T1
$$
u = f(w),\quad w=x^2 + y^2 + z^2
$$
求
$$
\dfrac{\partial^2 {u}}{\partial {x}^2}, \dfrac{\partial {u}}{\partial {x}}{y}
$$
**解**：
$$
\begin{aligned}
\dfrac{\partial {u}}{\partial {z}} &= 2f'x \\
\dfrac{\partial^2 {u}}{\partial {x}^2} &= \dfrac{\partial}{\partial {x}}\left(2x\dfrac{\partial {f}}{\partial {w}}\right) = 2\dfrac{\partial {f}}{\partial {w}} + 2x \dfrac{\partial}{\partial {w}}\;\left(\dfrac{\partial {f}}{\partial {w}}\right)\dfrac{\partial {w}}{\partial {x}} = 2f'+ \boxed{4x^2f''} \\
\dfrac{\partial {u}}{\partial {x}}{y} &= \dfrac{\partial}{\partial {y}}\left(2x\dfrac{\partial {f}}{\partial {w}}\right) = 2x \dfrac{\partial}{\partial {w}}\left(\dfrac{\partial {f}}{\partial {w}}\right)\dfrac{\partial {w}}{\partial {y}} = 4xyf''
\end{aligned}
$$
## T2
$$
z = f(u, v, w);\;u = x + y; v = xy; z = \dfrac{x}{y}
$$
求
$$
z_{xx}, z_{xy}
$$
**解**：
$$
\begin{aligned}
z_x & = \dfrac{\partial {f}}{\partial {u}} + y \dfrac{\partial {f}}{\partial {v}} + \dfrac{1}{y} \dfrac{\partial {f}}{\partial {w}}  \\ 
z_{xx} & = \dfrac{\partial}{\partial {x}} \left( \dfrac{\partial {f}}{\partial {u}} + y \dfrac{\partial {f}}{\partial {v}} + \dfrac{1}{y} \dfrac{\partial {f}}{\partial {w}} \right)   \\
 & = \left[ \dfrac{\partial^2 {f}}{\partial {u}^2} + y\dfrac{\partial {f}}{\partial {u}}{v} + \dfrac{1}{y} \dfrac{\partial {f}}{\partial {u}}{w} \right]  \\
 & + y\left[ \dfrac{\partial {f}}{\partial {v}}{u} + y\dfrac{\partial^2 {f}}{\partial {v}^2} + \dfrac{1}{y} \dfrac{\partial {f}}{\partial {v}}{w} \right] \\
 & + \dfrac{1}{y} \left[ \dfrac{\partial {f}}{\partial {w}}{u} + y\dfrac{\partial {f}}{\partial {w}}{v} + \dfrac{1}{y} \dfrac{\partial^2 {f}}{\partial {w}^2} \right]   \\
 & = \dfrac{\partial^2 {f}}{\partial {u}^2} + 2y \dfrac{\partial {f}}{\partial {u}}{v} + \dfrac{2}{y} \dfrac{\partial {f}}{\partial {u}}{w} + y^2 \dfrac{\partial^2 {f}}{\partial {v}^2}+2\dfrac{\partial {f}}{\partial {v}}{w} + \dfrac{1}{y^2} \dfrac{\partial^2 {f}}{\partial {w}^2} \\
z_{xy} & = \dfrac{\partial}{\partial {y}} \left( \dfrac{\partial {f}}{\partial {u}} + y \dfrac{\partial {f}}{\partial {v}} + \dfrac{1}{y} \dfrac{\partial {f}}{\partial {w}} \right)   \\
 & = \left[ \dfrac{\partial^2 {f}}{\partial {u}^2} + x\dfrac{\partial {f}}{\partial {u}}{v} - \dfrac{x}{y^2} \dfrac{\partial {f}}{\partial {u}}{w} \right]  \\
 & + y\left[ \dfrac{\partial {f}}{\partial {v}}{u} + x\dfrac{\partial^2 {f}}{\partial {v}^2} - \dfrac{x}{y^2} \dfrac{\partial {f}}{\partial {v}}{w} \right] \\
 & + \dfrac{1}{y} \left[ \dfrac{\partial {f}}{\partial {w}}{u} + x\dfrac{\partial {f}}{\partial {w}}{v} - \dfrac{x}{y^2} \dfrac{\partial^2 {f}}{\partial {w}^2} \right] \\
 & + \boxed{\dfrac{\partial {f}}{\partial {v}} \dfrac{\partial}{\partial {y}} \left( y \right)  + \dfrac{\partial {f}}{\partial {w}} \dfrac{\partial}{\partial {y}} \left( \dfrac{x}{y} \right) } \\
 & = \dfrac{\partial^2 {f}}{\partial {u}^2} + (x + y) \dfrac{\partial {f}}{\partial {u}}{v} + \left( \dfrac{1}{y} -\dfrac{x}{y^2} \right) \dfrac{\partial {f}}{\partial {u}}{w} + xy \dfrac{\partial^2 {f}}{\partial {v}^2} - \dfrac{x}{y^3}\dfrac{\partial^2 {f}}{\partial {w}^2}  \\& + \boxed{\dfrac{\partial {f}}{\partial {v}} -\dfrac{1}{y^2}\dfrac{\partial {f}}{\partial {w}}} 
\end{aligned}
$$

# 总结
要写成
$$z = f(u, v, w);\;u = x + y; v = xy; z = \dfrac{x}{y}$$
的形式，而不是直接
$$
z = f(x + y, xy, \dfrac{x}{y})
$$
