---
title: Playing pool with pi
tags: [physics]
---

*Computing the value of $$\pi$$ by simulating elastic collisions between balls, following Galperin's paper (2003)*
<!--more-->

The paper ["Playing Pool with $$\pi$$" by Galperin (2003)](https://www.maths.tcd.ie/~lebed/Galperin.%20Playing%20pool%20with%20pi.pdf) explains a very interesting approach to calculating the value of pi to a required precision. This method involves counting the collisions of billiard balls in an elastic setting. As a ball 1 of mass M approaches a ball 2 of smaller mass m that is at rest, it imparts momentum to the the smaller ball. We assume ideal elastic collisions. So, the total momentum and the total energy are conserved. Now, the ball 2 collides with a wall and returns back to collide again with ball 1. This happens for N number of times before ball 1 recedes with a higher velocity than ball 2, so that no more collisions are possible. Interestingly enough, if we count the total number of collisions of ball 2 with ball 1 and ball 2 with the wall, this gives the value of pi. Now, the precision of the value depends on the ratio of the masses of two balls. Let's assume the mass of ball 2 is 1 and the mass of ball 1 is M. For this particular case, the number of decimal points of pi that can be calculated is given by $$(log_{10} M)/2$$. So, the values of M are generally taken to be $$100^N$$ for some $$N$$ and increasing the value of M increases the precision. The reason behind this is beautifully explained in [this 3blue1brown video](https://www.youtube.com/watch?v=jsYwFizhncE){:target="_blank"}

Now, we use python to put this algorithm in practice and try to obtain the value of $$\pi$$ to 8 decimal places. The code counts the number of collisions until the bigger ball recedes with a velocity higher than that of the smaller ball. In an elastic collision with initial masses $$M$$ & $$m$$ with respective initial velocities $$u_1$$ & $$u_2$$, the final velocities are given by  

$$v_1 = \frac{M - m}{M + m} u_1 + \frac{2m}{M + m} u_2$$

$$v_2 = \frac{2m}{M + m} u_1 + \frac{M - m}{M + m} u_2$$  

```python
import time
start = time.time()

M = 10000000000000000
u1 = 1
u2 = 0

collisions = 0

while(True):
  v1 = u1*(M-1)/(M+1) + u2*(2)/(M+1)
  v2 = u1*(2*M)/(M+1) + u2*(1-M)/(M+1)
  collisions += 1 #The balls collide with one another changing velocities
  if(abs(v2) < abs(v1)): 
    if(v2 > 0): collisions += 1 #If the smaller ball is moving towards the wall
    break
  collisions += 1 #Collision of the smaller ball with the wall before reversing direction
  u1, u2 = v1, -v2

print(collisions)
print(time.time()-start)
```

This gives a value of **314159265** in 15 min!