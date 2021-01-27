---
title: Euler's theorem
description: Proof of Euler's theorem.
categories:
 - number_theory
tags: RSA

---

<script type="text/javascript" async
 src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-MML-AM_CHTML">
  </script>

<center><h1>Euler's theorem</h1></center>

<div style="text-align: right"> cosdong7 </div>

$$
a^{\varphi(n)}\equiv 1\; (mod\, n)\; if\; gcd(a,\, n)=1
$$

$$
where\; \varphi(n) =\vert \{1\leq k\leq n\, \vert \, gcd(k, n)=1\,,\,k\in\mathbb{Z} \}\vert
$$





$Proof. $

$Let\; S = \{1\leq k\leq n\,\vert \,gcd(k, n)=1\,,\,k\in\mathbb{Z} \}.$ 

$\vert S\vert = \varphi(n)\;by\;def\;of\;\varphi()$

$S = \{b_1,\, b_2,\, ...\,,b_{\varphi(n)}\}$

$Let\; S^{'}=\{a\cdot b\,\vert \,\forall b\in S\} = \{ab_1,\, ab_2,\, ...\,,ab_{\varphi(n)}\}$.

$gcd(e,\,n)=1\; for\; all\; e\in S^{'}\;since\;gcd(a,\,n)=1\;\and \; gcd(b,\,n)=1\;for\; all\; b\in S$

$for\; all\; e,\, g \in S^{'}\,(e \neq g),\;e\not\equiv g\;(mod\,n)\;by\;lemma\,A.$

$\therefore\; ab_1\cdot ab_2\cdot\, ...\,\cdot ab_{\varphi(n)} \equiv b_1\cdot b_2\cdot\, ...\,\cdot b_{\varphi(n)}\;(mod\,n)$

$\Longrightarrow a^{\varphi{(n)}}\equiv 1\; (mod\, n)\;since\; gcd(n,\,b_1\cdot b_2\cdot\, ...\,\cdot b_{\varphi(n)}) = 1$.



<br>

<br>

$Lemma\,A.\; For\; all\; e,\, g \in S^{'}\,(e \neq g),\;e\not\equiv g\;(mod\,n)$

$Proof.$

$Assume\;there\; exist\; ab_i,\,ab_j\in S^{'}\;such\; that\; 1\leq i<j<\varphi (n)\;and\; ab_i \equiv ab_j \;(mod\,n) $

$a(b_i-b_j) = ab_i-ab_j = k\cdot n\; (k\in \mathbb{Z}-\{0\})$

$n\vert (b_i-b_j)\; since\; gcd(a,\,n)=1$

$-(n-1)\leq b_i-b_j \leq(n-1)\;since\;1\leq b_i,\, b_j\leq n$

$\bot $

$\therefore\; for\; all\; e,\, g \in S^{'}\,(e \neq g),\;e\not\equiv g\;(mod\,n)$

