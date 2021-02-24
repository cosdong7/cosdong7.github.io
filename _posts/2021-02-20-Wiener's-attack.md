---
title: Wiener's attack
description: A cryptanalytic attack on the use of short RSA secret exponent (small d).
categories:
 - cryptanalysis
tags: [RSA, Python, small_d, continued fraction]



---



> A cryptanalytic attack on the use of short RSA secret exponent (small $d$).

<div style="text-align: right"> cosdong7 </div>



## <center>What is Continued Fractions?</center>

A continued fraction is an expression of the form 

$a_1/(q_1+a_2/(q_2+a_3/(\cdots / (q_{m-1}+a_m/q_m)\cdots))) = \frac{a_1}{q_1+\frac{a_2}{q_2+\frac{a_3}{\cdots \frac{}{q_{m-1} + \frac{a_m}{q_m} }}}}$

Define notation $\langle q_0,\, q_1,\, \cdots\, ,\, q_m\rangle = 1/(q_1+1/(q_2+1/(\cdots / (q_{m-1}+1/q_m)\cdots)))$



A continued fraction expansion of a positive rational number $f$ can be formed by subtracting away the integer part of $f$ and repeatedly inverting the remainder and subtracting away the integer part until the remainder is zero. ($q_i$: the integer quotient at step $i$, $r_i$: the remainder at step $i$, $m$: the number of inversion steps)

$q_0 = \lfloor f \rfloor, \qquad r_0 = f-q_0 \qquad and$

$q_i = \lfloor \frac{1}{r_{i-1}} \rfloor, \qquad r_i = \frac{1}{r_{i-1}} - q_i, \quad for\; i = 1,\, 2,\, \cdots,\,m.$



<br>

<br>

## <center>How to reconstruct $f$ from its continued fraction expansion ($q_0 \rightarrow q_m\; direction$ )?</center>

Let $n_i$ and $d_i$, $i = 0,1,\cdots,m$ be a sequence of numerators and denominators defined as follows: 

$\frac{n_i}{d_i} = \langle q_0,\, q_1,\, \cdots ,\,q_i\rangle, \qquad GCD(n_i,\, d_i)=1 \qquad for\;i=0,\, 1,\, \cdots,\, m.$

It can be shown that,

$$\begin{aligned} n_0 = q_0, &\qquad d_0=1,\\ n_1 = q_0q_1+1, &\qquad d_1=q_1,\\ &\quad \vdots\\ n_i = q_in_{i-1}+n_{i-2}, &\qquad d_i=q_id_{i-1}+d_{i-2},\\  \end{aligned}$$  for $i = 2,\, 3,\, \cdots, \, m.$

Then, $\;f = n_m/d_m.$



<br>

<br>

## <center>Continued Fraction Algorithm</center>

Let $f'$ be an underestimate of $f$ :

$$f'=f(1-\delta),\qquad for\; some\; \delta \ge 0.$$

Let $\;q_i$, $r_i$ and $q'_i$, $r'_i$ be the $i$th quotients and remainders of $f$ and $f'$ respectively.

<br>

If $\delta$ is small enough, then the numerator and denominator of $f$ can be found using the following algorithm:

1. Generate the next quotient ($q'_i$) of the continued fraction expansion of $f'$.

2. Construct the fraction equal to 
   $$
   \begin{aligned} &\langle q'_0,\, q'_1,\, \cdots ,\, q'_{i-1},\, q'_i+1\rangle, \qquad &if\;i\;is\;even,\\&\langle q'_0,\, q'_1,\, \cdots ,\, q'_{i-1},\, q'_i\rangle, \qquad &if\;i\;is\;odd.\end{aligned}
   $$
   

3. If the constructed fraction is not equal to $f$, go to 1.

Time complexiity: polynomial in $log(max(n_m, \, d_m)).$



<br>

<br>



## <center>How small should the $\delta$ be?</center>

The continued fraction algorithm will succeed if:


$$
\begin{aligned} &\langle q_0,\, q_1,\, \cdots ,\, q_{m-1},\, q_m-1\rangle <f'\le \langle q_0,\, q_1,\, \cdots ,\, q_m\rangle(=f), \qquad &if\;m\;is\;even,\\&\langle q_0,\, q_1,\, \cdots ,\, q_{m-1},\, q_m+1\rangle <f'\le \langle q_0,\, q_1,\, \cdots ,\, q_m\rangle(=f),  &if\;m\;is\;odd. \end{aligned}
$$


$\delta\; (=1-\frac{f'}{f})<\frac{1}{\frac{3}{2}n_md_m}$ is sufficient to guarantee the inequality above. 



s<br>

<br>



## <center>Continued Fraction Algorithm applied to RSA</center>

Let ($e, \; N$) be public key and ($d, \;N$) be private key while $N = pq$ 

$ed \equiv 1 \bmod \varphi(N) $

$\Rightarrow ed = k\varphi(N)+1\; for\; some\; integer\;k.$

$\frac{e}{\varphi(N)} = \frac{k}{d}+\frac{1}{d\varphi(N)}$

If $N$ is large enough, 

$\qquad \bullet\; N$ is slightly larger than $\varphi(N)$.

$\qquad \bullet\; \frac{1}{d\varphi(N)} \approx 0$.

$\therefore$ we can apply continued fraction algorithm with $f' = \frac{e}{N}$  $f = \frac{k}{d}$.



<br>

<br>

## <center>Breaking RSA with Wiener's theorem </center>

$f' = \frac{e}{N}$ .



Notice $(x-p)(x-q) = 0$ 

$\Rightarrow x^2 -(N-\varphi(N)+1)x+N = 0$ 

$\Rightarrow  x = \frac{(N-\varphi(N)+1)\pm \sqrt{(N-\varphi(N)+1)^2-4N}}{2}$



1. Generate the next numerator and denominator ($n'_i,\, d'_i$) of the continued fraction expansion of $f'$. 
2. Assign $k = n'_i,\; d = d'_i,\; \varphi(N)=\frac{ed-1}{k}$ .
   1. If $d$ is even or $\varphi(N) \notin \mathbb{Z}$, go to 1.
3. Assign $p,\, q = \frac{(N-\varphi(N)+1)\pm \sqrt{(N-\varphi(N)+1)^2-4N}}{2}$
   1. If $p,\, q \notin \mathbb{Z}$ or $pq = N$, go to 1.
4. return $d$.



<br>

<br>

## <center>Breif implementation</center>

```python
import gmpy2

def rational_to_contfrac(n, d): #construct continued fraction expasion from n/d
    q0 = n//d
    quotients = [q0]
    q = q0
    while q * d != n:
        n,d = d,n%d
        q = n//d
        quotients.append(q)
    return quotients

def contfrac_to_tmpfracs(quotients):	#construct numerators and denominators from continued fraction expansion
    numerators = [quotients[0], quotients[0]*quotients[1]+1]
    denominators = [1, quotients[1]]
    for i in range(2, len(quotients)):
        numerators.append(quotients[i]*numerators[i-1]+numerators[i-2])
        denominators.append(quotients[i]*denominators[i-1]+denominators[i-2])
    return numerators, denominators

def wiener_attack(e, N):	#apply wiener's attack
    numerators, denominators = contfrac_to_tmpfracs(rational_to_contfrac(e, N))
    m = len(numerators)
    for i in range(m):
        k, d = numerators[i], denominators[i]
        if d%2 == 0 or k==0 or (e*d-1)%k != 0:
            continue
        phi = (e*d-1)//k
        discriminant = (N-phi+1)**2-4*N 
        root, is_perfect_root = gmpy2.iroot(discriminant, 2)
        if not is_perfect_root:
            continue
        if ((N-phi+1)+root)%2!=0:
            continue
        if N != ((N-phi+1)**2-discriminant)//4:
            continue
        return d

```



<br>

<br>



## <center>Reference</center>

[Wiener, M. J. (1990). Cryptanalysis of short RSA secret exponents. *IEEE Transactions on Information theory*, *36*(3), 553-558.](https://ieeexplore.ieee.org/abstract/document/54902?casa_token=HXFOf7_nzMAAAAAA:EK0EuMVoh6MCd2i27TowXexGgsMg_acsQdV4NRGPeh57uh22Mun9d1F0sQWEFNOR8wt_fsWxOQ)

