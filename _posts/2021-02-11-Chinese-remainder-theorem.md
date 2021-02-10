---
title: Chinese remainder theorem
description: Proof of Chinese remainder theorem and how to use it.
categories:
 - number_theory
tags: RSA



---

> Proof of Chinese remainder theorem and how to use it

<div style="text-align: right"> cosdong7 </div>



### <em>Statement</em>

Given pairwise coprime positive integers $n_1, n_2, \ldots, n_k$ and arbitrary integers $a_1, a_2, \ldots, a_k$, the system of simultaneous congruences 

$$\begin{aligned} x &\equiv a_1 \pmod{n_1}\\ x &\equiv a_2 \pmod{n_2}\\ & \vdots\\ x &\equiv a_k \pmod{n_k} \end{aligned}$$

has a solution, and the solution is unique modulo $N = n_1n_2\cdots n_k$.



<br>

<br>

### <em>Proof</em>

$Existence$



$Let\; m_{i} = N/n_{i}.$ 

$gcd(n_{i}, m_{i}) = 1\;\Rightarrow\;there\; exist\;integers\;  s_{i},\,t_{i}\;such\;that\; s_{i}\cdot n_{i}\,+\, t_{i}\cdot m_{i}\, = 1\;(\because\, Bézout's\; identity)$

$s_{i}\cdot n_{i}\,+\, t_{i}\cdot m_{i}\, \equiv\, t_{i}\cdot m_{i}\, \equiv\, 1\; mod\,n_{i}$

$Let\; x\, =\, a_{1}\cdot t_{1}\cdot m_{1}+a_{2}\cdot t_{2}\cdot m_{2}+⋯+a_{k}\cdot t_{k}\cdot m_{k}$

$x\equiv a_{1}\cdot t_{1}\cdot m_{1}+a_{2}\cdot t_{2}\cdot m_{2}+⋯+a_{k}\cdot t_{k}\cdot m_{k} \equiv  a_{i}\cdot t_{i}\cdot m_{i} \equiv a_{i}\cdot 1 \equiv a_{i} \; mod\,n_{i}$

$\therefore x\;is\;a\;solution\;for\; $ $$\begin{aligned} x &\equiv a_1 \pmod{n_1}\\ x &\equiv a_2 \pmod{n_2}\\ & \vdots\\ x &\equiv a_k \pmod{n_k} \end{aligned}$$



<br>



$Uniqueness$

$Assume\; x\,,y\,(x \not\equiv y\; mod\,N)\; be\; the\; solutions\; to\; the\; $ $\begin{aligned} x &\equiv a_1 \pmod{n_1}\\ x &\equiv a_2 \pmod{n_2}\\ & \vdots\\ x &\equiv a_k \pmod{n_k} \end{aligned}$

$$\begin{aligned} x-y &\equiv 0 \pmod{n_1}\\ x-y &\equiv 0 \pmod{n_2}\\ & \vdots\\ x-y &\equiv 0 \pmod{n_k} \end{aligned}$$

$since\;n_1, n_2, \ldots, n_k\;are\;pairwise\;coprime\;and\; n_i\mid (x-y)\;for \; 1\leq i \leq k\; \Rightarrow \; N\mid (x-y)$

$x-y\equiv 0\; mod\,N$

$x\equiv y\; mod\,N$

$\bot $

$\begin{aligned}\\ \\ \\ \end{aligned}$$\therefore\;\;$$\begin{aligned} x &\equiv a_1 \pmod{n_1}\\ x &\equiv a_2 \pmod{n_2}\\ & \vdots\\ x &\equiv a_k \pmod{n_k} \end{aligned}\;\;$ $has \; unique\; solution. $

<br>

<br>

### <em>Use</em>

$$Gaussian Method$$

1. Find $N = n_1 × n_2 × \cdots × n_k$. 

2. Find $m_1 =N/n_1,\;m_2 =N/n_2,\,\cdots,\;m_k =N/n_k$.

3. Find the multiplicative inverse of $m_1,\, m_2,\, \cdots,\, m_k$ using the corresponding moduli ($n_1,\, n_2 ,\, \cdots,\, n_k$). Call the inverses $m_1^{-1},\, m_2^{-1},\, \cdots,\, m_k^{-1}$. ([Extended Euclidean Algorithm](https://cosdong7.github.io/number_theory/2021/01/29/Extended-Euclidean-Algorithm))
4. $x \equiv (a_1m_1m_1^{-1}+a_2m_2m_2^{-1}+\cdots +a_km_km_k^{-1})\; mod\, N$

