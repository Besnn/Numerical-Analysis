# Epsilon macchina vs Minimum Positive Number
What Machine Epsilon is:
* The *maximum relative error* between two numbers in a given system (by definition of IEEE754 it is the absolute difference between 1 and the next number).
* *Exponent-agnostic* (it expresses the maximum relative error for every two numbers you perform operations on).

In contrast, The Minimum Positive Number:
* Is the *minimum number* that can be expressed in a particular system.
* As such, it must have **both** *the least exponent possible*, **and** *the machine epsilon* in its mantissa.

Difference in algorithm:  
**Machine Epsilon**
```python
ε = 1.0
b = 2 # base - since computers use binary numbers b = 2
while 1.0 + ε/b != 1.0:
    ε = ε/b
print(ε)
```
**Minimum Value**
```javascript
mv = 1.0
b = 2 // same logic as before
while (mv/2 != 0) mv = mv/2
console.log(mv)
```
