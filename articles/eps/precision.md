## Precision
The *mantissa* is what determines the *precision* of a number.  
In case the *mantissa* consists of `m` bits and we need `m+1` bits, precision is lost. Storing numbers with long *mantissa*s is handled in two distinct ways:
* Truncation:  
  > ![fl](https://quicklatex.com/cache3/69/ql_660438d7646477c7c309332d722a8169_l3.png)
* Rounding:  
  > ![fl1](https://quicklatex.com/cache3/df/ql_988e33490913988e8372ec76fbfd0ddf_l3.png)
## Errors of representation
* **Absolute Error**  
![ea](https://quicklatex.com/cache3/9a/ql_3ed0f78b02494a69c82ca7e129c4589a_l3.png)
* **Relative Error**  
![er](https://quicklatex.com/cache3/33/ql_c4dda07c10655666947dc1838e9e9533_l3.png)  
### Notes
The relative and absolute error can be expressed in terms of each other as:
```lua
absolute_error/abs(x) -- relative error
relative_error*abs(x) -- absolute error
```
The relative error is influenced by the *mantissa* and not by the exponent, while the absolute error by the *order of magnitude* (characteristic).
There exist upper bounds for both errors:  

![bound](https://quicklatex.com/cache3/1e/ql_1ef9a053628f1f016f95dfc326c7171e_l3.png)  
The quantity on the right hand side is often refered to as *machine epsilon*.  
### Important Note
When performing operations on floating-point numbers, computers use **specialized registers** to hold temporary values. These register have more than the usual `m` bits the machine uses to store numbers in memory. This is to minimize any eventual errors.
## Floating-Point Operations
When performing operations on floating-point numbers, the result may not be a floating-point number. Hence by definition in finite arithmetic:
```lua
-- [○] denotes operation ○ in floating-point arithmetic
x [○] y := fl(fl(x) ○ fl(y))
```
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
* **Commutativity** holds: `a + b = b + a`  

Finite arithmetic operations on floating-point numbers are one such commutative magma.  

Let **(B, m, A)** be a triple such that:
* **B** is a positive whole number;
* **m** is a non negative whole number;
* **A** is either `Trunc` or `Round,`  

then this triple defines the finite arithmetic on Rational Numbers in a given system, **B** acting as the base and **m** as the length of mantissa. `Trunc/Round` denote the mode of approximation.
## Equality
Due to lack of precision, the concept of **equality** is not the same in finite arithmetic as it is with real numbers:  
![equ](https://quicklatex.com/cache3/7a/ql_79bbfc0dd9681010ae5c79dfaca07c7a_l3.png)   
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
#### Product
For `x1 [●] x2`:  

![product](https://quicklatex.com/cache3/1e/ql_a6ab36d90fb4802838c258f6831b7b1e_l3.png)
#### Division
