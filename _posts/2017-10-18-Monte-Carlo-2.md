---
layout: post
title: Monte Carlo Estimation of e
category: ['Monte Carlo', ]
---
This blogpost provides a way to calculate the approximate value of e using the Monte Carlo method.

## Strategy

Calculating the value of e using this method requires us to perform an experiment multiple times. In each experiment, we keep generating random numbers in [0,1] till their sum exceeds one. The number of times we generated random numbers is a guess for e. 

This experiment is repeated n times (n is usually large) and we take the average of the guesses for e as our estimate.

## Proof

Let U be a random variable uniformly distributed in range (0,1) and Y be the minimum number of terms for U1+U2+⋯+UY>1, or expressed differently:

<p style="text-align:center;">
<img src="/images/im1.jpg" align="center">
</p>

If instead we looked for:
<p style="text-align:center;">
<img src="/images/im2.jpg" align="center">
</p>

for u∈[0,1], we define f(u)=E[Y(u)], expressing the expectation for the number of realizations of uniform draws that will exceed u when added.

We can apply the following general properties for continuous variables:

<p style="text-align: center;">
<img src="/images/im3.jpg" align="center">
</p>
to express f(u) conditionally on the outcome of the first uniform, and getting a manageable equation. This would be it:

<p style="text-align: center;">
<img src="/images/im4.jpg" align="center">
</p>
If the U1=x we are conditioning on is greater than u, i.e. x>u, E[Y(u)|U1=x]=1.
If, on the other hand, x<u,E[Y(u)|U1=x]=1+f(u−x), because we already have drawn 1 uniform random, and we still have the difference between x and u to cover. Going back to equation (1):

<p style="text-align: center;">
<img src="/images/im5.jpg" align="center">
</p>
, and with substituting w=u−x we would have
<p style="text-align: center;">
<img src="/images/im6.jpg" align="center">
</p>

If we differentiate both sides of this equation, we can see that:

<p style="text-align: center;">
<img src="/images/im7.jpg" align="center">
</p>
with one last integration we get:

<p style="text-align: center;">
<img src="/images/im8.jpg" align="center">
</p>
We know that the expectation that drawing a sample from the uniform distribution and surpassing 0 is 1, or f(0)=1. Hence, k=1, and f(u)=eu. Therefore f(1)=e.

## Code

Here's a simple python function to estimate value of e by sampling from uniform distributions:

```python
import random as r
num_iters = 1000000

def get_e_trial():
    count = 0
    tot = 0
    while tot <= 1:
        tot += r.random()
        count += 1
    return count

def get_e():
    results = (get_e_trial() for i in range(num_iters))
    return (sum(results) * 1.0) / num_iters

print "e = ", get_e()
```

## References:

1. Post on [Stack Exchange](https://stats.stackexchange.com/questions/194352/why-does-the-number-of-continuous-uniform-variables-on-0-1-needed-for-their-su)
