---
title: FizzBuzz Extended
tags: [cs,math]
---

*Generalizing FizzBuzz problem and extending it to more than 2 numbers*
<!--more--> 

A FizzBuzz problem is a classic problem is CS. When printing numbers from 1 to n, when the number is a multiple of (say) 3, print 'Fizz'. For a number that is multiple of 5, print 'Buzz'. For a number that is a multple of both, print 'FizzBuzz'  

An interesting post that generalizes the FizzBuzz problem to more than 2 numbers is described [here](http://philcrissman.net/posts/eulers-fizzbuzz/). The code below is an implementation of the same. Steps involved are  
- Verify if the input numbers are co-prime  
- Find the power by calculating lcm of totient of input numbers  
- Find divisor by multiplying all numbers  
- Create a dictionary that maps the result of modulo operation to the output string  


```python
# Python Ver.3.8.8
# pip install oeis
from oeis import A000010 # Euler Totient function
import math
from functools import reduce
import itertools
import collections
import sys

# Return the value of Totient function from array
def phi(x):
    return A000010[x]

# Find lcm of two numbers
def lcm(a, b):
    return abs(a*b) // math.gcd(a, b)

# Check co-prime
def co_prime(a, b):
    return(math.gcd(a, b) == 1)

# Input
inp = {3:"Fizz",5:"Buzz",7:"Tazz"}
N = 105 # Print results till this number

# Co-prime check
if not all(co_prime(i[0],i[1]) for i in list(itertools.combinations(inp.keys(),2))):
    print("Inputs not co-prime. Execution stopped")
    sys.exit()

# Find power to which the number is raised before modulus
p = 1
for n in inp.keys():
    p = lcm(p,phi(n))
print('Power:',p)

# Find divisor for modulo operation
divisor = reduce((lambda x, y: x * y), inp.keys())
print('Divisor:',divisor)

# Map results of modulo to words in dict()
d = collections.defaultdict(str) # Default dict()
# d = collections.defaultdict(lambda: 'initial') # For initialization
for i in range(1,len(inp)+1): # Pick i numbers
    for tup in list(itertools.combinations(inp.keys(),i)): # For combinations of i numbers
        x = reduce((lambda x, y: x * y), tup) # 
        for num in tup:
            d[pow(x,p,divisor)] += inp[num]
print('Dictionary:',dict(d))

# Execute program
for n in range(1,N+1):
    a = (lambda n:{**{1:n},**d}[pow(n,p,divisor)])(n)
    print(a)
```