---
title: Extended Euclidean Algorithm
description: Python implementation of Extended Euclidean Algorithm
categories:
 - number_theory
tags: [RSA, Python]


---



> Breif implementation of Extended Euclidean Algorithm

<div style="text-align: right"> cosdong7 </div>

```python
#Extended Euclidean Algorithm

def eea(a, b):          #returns r, s, t such that s*a+t*b=r
    r1 = a if a>b else b
    r2 = a+b-r1
    r = 0
    s1, s2, s = 1, 0, 0
    t1, t2, t = 0, 1, 0
    q = 0
    while(r2>0):
        q = r1 // r2
        r = r1 - q*r2
        r1, r2 = r2, r
        s = s1 - q*s2
        s1, s2 = s2, s
        t = t1 - q*t2
        t1, t2 = t2, t
    return r1, s1, t1

#Let a = e, b = phi(n) to find d(multiplicative inverse of e modulo phi(n))
```

