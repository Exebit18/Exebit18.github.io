---
layout: post
title: Monte Carlo Simulations in Python - Pi Estimation!
category: [PythonOneLiners, MonteCarlo]
---

Here's a simple python function to estimate value of pi by sampling from uniform distributions:

```python
num_iters = 1000000

def get_pi():
    results = ( ((r.random()**2 + r.random()**2)**0.5)<1 for i in range(num_iters) )
    return (sum(results) * 4.0) / num_iters

print "Pi = ", get_pi()
```