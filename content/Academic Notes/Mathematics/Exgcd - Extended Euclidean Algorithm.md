# Pseudocode
```
function extended_gcd(a, b)
	(old_r, r) := (a, b)
	(old_s, s) := (1, 0)
	(old_t, t) := (0, 1)

	while r != 0 do 
		quo := old_r div r
		(old_r, r) := r, old_r - quo * r
		(old_s, s) := (s, old_s - quo * s)
		(old_t, t) := (t, old_t - quo * t)

	output "Bezout cofficients: ", (old_s, old_t)
	output "Greatest common divisor: ", old_r
```
A trick to memorize the initial values:
Bézout's relationship:
$$
as + bt = \gcd(a, b) \implies \text{a * old\_s + b * old\_t = old\_r = a}
$$
then we have `old_s = 1, old_t = 0`


