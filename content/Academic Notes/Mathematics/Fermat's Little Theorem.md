# Fermat's Little Theorem
*Fermat's Little Theorem* states that if $p$ is a prime number and $a$ is an integer not divisible by $p$, then 
$$
a^{p-1} \equiv 1 \,(\text{mod}\, p)
$$This means that raising $a$ to the power of $p-1$ will result in a number that, when divided by $p$, leaves a remainder of 1. 

The theorem is foundational in number theory and has applications in fields such as cryptography, particularly in algorithms like [[RSA Encryption|RSA]], where it helps ensure the security of data transmission. Additionally, the theorem serves as a basis for proofs regarding properties of prime numbers.

# Pseudo-prime
Let $b$ be a positive integer. If $n$ is a composite positive integer, and $b^{n-1} \equiv 1 \pmod{n}$, then $n$ is called a *pseudo-prime* to be base $b$

Among the positive integer not exceeding $x$, where $x$ is a positive real number, compared to primes there are relatively few pseudo-primes to the base $b$. So determining  whether $b^{n-1} \equiv 1 \pmod{n}$ is a useful test that provides some evidence concerning whether $n$ is prime.

However, there are some composite $n$ that satisfies the congruence $b^{n-1} \equiv 1 \pmod{n}$ for all positive integers $b$ with $\mathrm{gcd}(b,n) = 1$ is called a *Carmichael number*. For example, the integer $561$ is a Carmichael number.