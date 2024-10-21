# Recursive Version
```python
def extended_gcd(a, b):
    if b == 0:
        return a, 1, 0
    else:
        gcd, x1, y1 = extended_gcd(b, a % b)
        x = y1
        y = x1 - (a // b) * y1
        return gcd, x, y
```

# Non-recursive Version
``` python
def ex_gcd(a, b):
    x, y = 1, 0
    x1, y1 = 0, 1
    a1, b1 = a, b

    while b1 != 0:
        q = a1 // b1
        a1, b1 = b1, a1 - q * b1
        x, x1 = x1, x - q * x1
        y, y1 = y1, y - q * y1

    return a1, x, y
```

# Calculation by Hand
For example, calculate $\mathrm{exgcd}(108, 68)$

| $a\ (r_i)$ | $b$ | $x_i = x_{i -2} - x_{i-1}q_{i-1}$ | $y_i = y_{i-2} - y_{i-1}q_{i-1}$ |     |
| ---------- | --- | --------------------------------- | -------------------------------- | --- |
| 0          | 108 | 1                                 | 0                                |     |
| 108        | 68  | 0                                 | 1                                |     |
| 68         | 40  | 1                                 | -1                               |     |
| 40         | 28  | -1                                | 2                                |     |
| 28         | 12  | 2                                 | -3                               |     |
| 12         | 4   | -5                                | 8                                |     |
| 4          | 0   |                                   |                                  |     |
this gives
$$
- 5 \times 108 + 8 \times 68 = \mathrm{gcd}(108, 8) = 4
$$
