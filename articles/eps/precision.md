## Precision
The *mantissa* is what determines the *precision* of a number.  
In case the *mantissa* consists of `m` bits and we need `m+1` bits, precision is lost. Storing numbers with long *mantissa*s is handled in two distinct ways:
* Truncation:  
  > ![fl](/img/fl.png)
* Rounding:  
  > ![fl1](/img/fl1.png)
## Errors of representation
* **Absolute Error**  
![ea](/img/ea.png)
* **Relative Error**  
![er](/img/er.png)  
### Notes
The relative and absolute error can be expressed in terms of each other as:
```lua
absolute_error/abs(x) -- relative error
relative_error*abs(x) -- absolute error
```
The relative error is influenced by the *mantissa* and not by the exponent, while the absolute error by the *order of magnitude* (characteristic).
There exist upper bounds for precision both for truncation and rounding:  

![bound](/img/bound.png)  
The quantity on the right hand side is often refered to as *machine epsilon*.  
### Important Note
When performing operations on floating-point numbers, computers use **specialized registers** to hold temporary values. These register have more than the usual `m` bits the machine uses to store numbers in memory. This is to minimize any eventual errors.
## Floating-Point Operations
When performing operations on floating-point numbers, the result may not be a floating-point number. Hence, in finite arithmetic:  

![prop](/img/prop.png)  

### Sum
1. Rewrite the number with the least characteristic so that its characteristic is the same as the other's.
2. Sum the *mantissa*s.
3. Convert to float.
### Product/Division 
1. Multiply/divide the *mantissa*s.  
2. Sum/Substract the *characteristics*.  
3. Convert to float.
## Properties of Floating-Point Numbers (or lack thereof)
Let **S** be a set of *rational numbers* equipped with an operation `o`. Then:
* Generally, **associativity** does not hold.
* **Distributivity** does not hold either.
* **Commutativity** holds: `a ⊚ b = b ⊚ a`  

Finite arithmetic operations on floating-point numbers are one such commutative magma.  

Let **(B, m, A)** be a triple such that:
* **B** is a positive whole number;
* **m** is a nonnegative whole number;
* **A** is either `Trunc` or `Round,`  

then this triple defines the finite arithmetic in a given system, **B** acting as the base and **m** as the length of mantissa. `Trunc/Round` denote the mode of approximation.
## Equality
Due to lack of precision, the concept of **equality** is not the same in finite arithmetic as it is with real numbers:  

![equ](/img/equ.png)   
where `ε` is the *tolerance*, which depends on *machine precision* `β^(1-m)`.
## Considerations
The floating of a number can be expressed in terms of the real number as:  
```lua
fl(x) = x + δ = x(1 + ϵ)
-- this yields:
relative_error = |x - fl(x)|/|x| = |x - x(1 + ϵ)|/|x| = |xϵ|/|x| = |ϵ|
-- relative error is less than or equal to machine precision by definition
-- so |ϵ| is surely less than or equal to machine epsilon.
```
With that in mind, we can calculate the error in a given operation.  

![circ](/img/circ.png)  
### Product 

![product](/img/prod.png)
### Division 

![division](/img/div.png)
### Sum

![sum](/img/sum.png)
#### Note
Notice that the expression dictates that there exist arguments such that `x1 + x2 ≈ 0`. This implies the relative error is be greatly amplified.
### Loss of Significance (a.k.a. Numerical or Catastrophic Cancellation)
> Loss of significative figures caused by substraction of numbers similar in value.  

![example](/img/canc.png)
