*RSA* is an encryption algorithm, used to securely transmit messages over the internet. It is based on the principle that it is easy to multiply large numbers, but factoring large numbers is very difficult.

The algorithm is implemented as follows:
1. The receiver chooses two large prime numbers $p$ and $q$. Let $n = pq$
2. The receiver calculates $\phi(pq) = (p-1)(q-1)$ and choose a number $e$ relatively prime to $\phi(pq)$. In practice, $e$ is often chosen to be $2^{16}+1 = 65537$
3. The receiver calculates the [[Modular Inverse|modular inverse]] $d$ of $e$ modulo $\phi(n)$, that is, $de \equiv 1 \pmod{ \phi(n)}$
4. The receiver distributes the *public key* $(n,e)$ and keep secret the *private key* $d$

Now that the public and private keys have been generated, they can be reused as often as wanted. To transmit a message, follow these steps:
1. First, the sender converts his message into a number $m$. One common conversion process uses the [[Data Representation#ASCII Table|ASCII alphabet]]. For example, the message "HELLO" could be encoded as $7269767679$. It is important that $m < n$, as otherwise the message will be lost when taken modulo $n$, **so if $n$ is smaller than the message, it will be sent in pieces.**
2. The sender then calculates $c \equiv m^e \pmod{n}$. $c$ is the *ciphertext*, or the encrypted message. Besides the public key, this is the only information an attacker will be able to steal.
3. The receiver computes $c^d \equiv m\pmod{n}$, by [[Euler's Theorem]] retrieving the original number
4. The receiver translates $m$ back into letters, retrieving the original message.

> [!Tip] Proof of step 3
> By the definition of $d$, there exists $k\in \mathbb{N}$ satisfying $de = k\phi(n) + 1$. Then we have
> 
> $$m^{de} \equiv m^{k\phi(n) + 1} \equiv m^{k\phi(n)}\cdot m \equiv \left( m^{\phi(n)} \right)^k\cdot m \equiv 1^k\cdot m \equiv m \pmod{n} $$

