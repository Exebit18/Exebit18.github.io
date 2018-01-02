---
layout: post
title: Monte Carlo Estimation of Pi
category: ['Python One Liners', 'Monte Carlo']
---

## Computation of Pi
If you don’t know what 'π' is, it is that number which has something to do with circles. More precisely, the area of the disk with the radius 'r' is equal to 'π * r^2'.

![The area of the disk]({{"/images/area_circle.jpg"}})

If the radius of the circle is equal to one, then the area of the disk is equal to 'π'.

Further, let’s inscribe a circle in a square. If the length of the side of the square is equal to two, then the radius of the inscribed circle is equal to one.

![Inscribed circle in the square]({{"/images/inscribed_circle.jpg"}})

Now, we divide the area of the circle with the area of the square

![The fraction]({{"/images/rowhammerimg1.jpg"}})

If we multiply this fraction by four, we get the value of 'π'.

A simple way to compute the fraction is to generate the points in the square and count the number of points which lie in the inside of the circle.

![Points in the square]({{"/images/generate_points_pi.jpg"}})

The approximation of the 'π' is

![Approximation of Pi]({{"/images/approximation_pi.jpg"}})

## Monte Carlo method for Pi
The Monte Carlo method uses the previous idea to compute the value of 'π'. The method randomly generates points in the square '[-1, 1] x [-1, 1]' and counts the number of points in the inside of the unit circle. The result is four times the fraction between the number of points which lie in the inside of the circle and the number of all generated points.

Here's a simple python function to estimate value of pi by sampling from uniform distributions:

```python
import random as r
num_iters = 1000000

def get_pi():
    results = ( (r.random()**2 + r.random()**2)**0.5 < 1 for i in range(num_iters) )
    return (sum(results) * 4.0) / num_iters

print "Pi = ", get_pi()
```
