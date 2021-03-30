---
title: Gram–Schmidt process
description: Python implementation of Gram–Schmidt process.
categories:
 - linear_algebra
tags: [Lattice, Python]



---



> A breif implementation of the Gram–Schmidt process

<div style="text-align: right"> cosdong7 </div>

```python
#vector subtract
def sub(v,u):
    return [v[i]-u[i] for i in range(len(v))]
  
#dot product
def inner_product(v, u):
    return sum([v[i]*u[i] for i in range(len(v))])

#project v on u
def projection(u, v):
    return [ui*(inner_product(u,v)/inner_product(u,u)) for ui in u]

#Gram–Schmidt process
def gram_schmidt(bv):	#returns orthogonal basis bu such that spans the same space with bv
    bu = [bv[0]]
    for i in range(1,len(bv)):
        bu.append(bv[i])
        for j in range(len(bu)-1):
            bu[i] = sub(bu[i], projection(bu[j],bv[i]))
    return bu

v1 = [4,1,3,-1]
v2 = [2,1,-3,4]
v3 = [1,0,-2,7]
v4 = [6, 2, 9, -5]

bv = [v1,v2,v3,v4]

print(gram_schmidt(bv))
```

