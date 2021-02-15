---
title: Birthday Paradox
description: An introduction to Birthday Paradox.
categories:
 - probability_theory
tags: [probability, Hash]



---





> An introduction to Birthday Paradox

<div style="text-align: right"> cosdong7 </div>

<br>

### <em>Statement</em>

<center> The probability that, in a set of n randomly chosen people, some pair of them will have the same birthday.</center>

$$
(1\,year=365\,days)
$$



<br>

<br>

### <em>Calculating it</em>

$Let\; \bar{P}(n)\; be\; a\;probability\; that\; n\; randomly\; chosen\; people\; all\; have\; distinct\; birthdays.$ 

$Then,\; \bar{P}(n)=\frac{365}{365} \times \frac{365-1}{365} \times \frac{365-2}{365} \times \cdots \times \frac{365-(n-1)}{365} = \frac{365!}{(365-n)!\times365^n}$

$\therefore The\; Birthday\; Paradox\; probability\; P(n) = 1 - P(n)=1- \frac{365!}{(365-n)!\times365^n}$



|  *n*  |             *P*(*n*)             |
| :---: | :------------------------------: |
|   1   |               0.0%               |
|   5   |               2.7%               |
|  10   |              11.7%               |
|  20   |              41.1%               |
|  23   |              50.7%               |
|  30   |              70.6%               |
|  40   |              89.1%               |
|  50   |              97.0%               |
|  60   |              99.4%               |
|  70   |              99.9%               |
|  75   |              99.97%              |
|  100  |            99.99997%             |
|  200  | 99.9999999999999999999999999998% |
|  300  |         (100 − 6×10−80)%         |
|  350  |        (100 − 3×10−129)%         |
|  365  |       (100 − 1.45×10−155)%       |
| ≥ 366 |               100%               |

<br>

<br>

### <em>Generalization</em>

<center> The probability that, in a set of n randomly chosen people, some pair of them will have the same birthday.</center>

$$
(1\,year=d\,days)
$$



$The\;generalized\; Birthday\; Paradox\; probability\; P(n) =1- \frac{d!}{(d-n)!\times d^n}$



<br>

<br>

### 

### <em>Reverse problem</em>

<center> For a fixed probability p, find the smallest n for which the probability p(n) is greater than the given p</center>

$$
n(p)\approx {\sqrt {730\ln \left({\frac {1}{1-p}}\right)}} \;for\, d=365
$$







### <em>Reference </em>

[Abramson, M., & Moser, W. (1970). More Birthday Surprises. *The American Mathematical Monthly,* *77*(8), 856-858. doi:10.2307/2317022](https://www.jstor.org/stable/2317022?origin=crossref&seq=1)

