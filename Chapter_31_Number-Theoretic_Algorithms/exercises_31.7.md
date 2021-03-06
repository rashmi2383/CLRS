## 31.7 The RSA public-key cryptosystem

### 31.7-1

> Consider an RSA key set with $$p = 11$$, $$q = 29$$, $$n = 319$$, and $$e = 3$$. What value of $$d$$ should be used in the secret key? What is the encryption of the message $$M = 100$$?

$$\phi(n) = (p - 1) \cdot (q - 1) = 280$$.

$$d = e^{-1} ~\text{mod}~ \phi(n) = 187$$.

$$P(M) = M^e ~\text{mod}~ n = 254$$.

$$S(C) = C^d ~\text{mod}~ n = 254^{187} ~\text{mod}~ n =  100$$.

### 31.7-2

> Prove that if Alice's public exponent $$e$$ is $$3$$ and an adversary obtains Alice's secret exponent $$d$$, where $$0 < d < \phi(n)$$, then the adversary can factor Alice's modulus $$n$$ in time polynomial in the number of bits in $$n$$. (Although you are not asked to prove it, you may be interested to know that this result remains true even if the condition $$e = 3$$ is removed. See Miller [255].)

$$ed \equiv 1 ~\text{mod}~ \phi(n)$$

$$ed - 1 = 3d - 1 = k \phi(n)$$

If $$p, q < n / 4$$, then $$\phi(n) = n - (p + q) + 1 > n - n / 2 + 1 = n / 2 + 1 > n / 2$$.

$$kn / 2 < 3d - 1 < 3d < 3n$$, then $$k < 6$$, then we can solve $$3d - 1 = n - p - n / p + 1$$.

### 31.7-3 $$\star$$

> Prove that RSA is multiplicative in the sense that
> 
> $$P_A(M_1) P_A(M_2) \equiv P_A(M_1, M_2) ~(\text{mod}~n)$$.
> 
> Use this fact to prove that if an adversary had a procedure that could efficiently decrypt $$1$$ percent of messages from $$\mathbb{Z}_n$$ encrypted with $$P_A$$, then he could employ a probabilistic algorithm to decrypt every message encrypted with $$P_A$$ with high probability.

Multiplicative:
$$e$$ is relatively prime to $$n$$.

Decrypt:
In each iteration randomly choose a prime number $$m$$ that $$m$$ is relatively prime to $$n$$, if we can decrypt $$m \cdot M$$, then we can return $$m^{-1} M$$ since $$m^{-1} = m^{n - 2}$$.