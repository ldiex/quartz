```python
def exgcd(a, b):
    x, y, u,v = 0, 1, 1, 0
    while a != 0:
        q, r = b // a,  b % a
		b, a = a, r
		x, y = u, v
	    u, v = x - u * q, y - v * q
    gcd = b
    return gcd, x, y
```

