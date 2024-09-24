# Idea
*Convolution* is designed to calculate the remaining volume of a system with instable input and stable output.

For example, imagine a person who keeps taking in food all over a day, we define $f(t)$ as the amount of food he takes during period $t \sim t + \mathrm{d}t$, which varies during the day. Besides, we can also define $g(t)$ as the ratio of remaining food in the person's stomach after time $t$, that is, if the person takes $\mathrm{d}m$ food at time $t_0$, then $\mathrm{d}m\cdot g(t)$ would be the remaining amount of this $\mathrm{d}m$ food at time $t_0 + t$.

Now we can easily calculate the total remaining amount of food at time $t$ by the following integration:
$$
\text{food-left-in-stomach}(t) = \int_0^t f(x)g(t-x) \mathrm{d}x
$$
To generalize, convolution can be interpreted as a measure of overlap between 
$f(t)$ and a time-reversed and shifted version of $g(t)$. It provides the accumulated effect of the input function $f(t)$ on the system characterized by $g(t)$
# Topics
[[Convolution (Discrete)]]
[[Convolution (Continuous)]]
[[Convolution Algebra]]
