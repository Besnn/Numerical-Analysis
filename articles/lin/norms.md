# Norms
The concept of a *norm* is the generalization of the concept of 'length' or 'distance'.  
## Vector Norm
A *vector norm* is a function from a vector space to nonnegative real numbers. It has certain properties:
* Triangle Inequality `L(x+y) -leq L(x) + L(y)`  
* Absolute Scalability `L(a*x) = |a|*L(x)`  
* Positive-definiteness`L(x) = 0 iff x = 0`  

If only the first two points are satisfied, then the function is a *vector seminorm*.  
Common (vector) norms are:
* Absolute Value `|•|` (for scalars only)  
* Euclidian Norm `L2(•) = length(x, y, z, ...)`  
* Manhatan Norm `L1(•) = |x| + |y| + [z] + ...`  
* Maximum `L_inf(•) = max(|•|)`  

The general form for a p-norm is:  

![pn](https://quicklatex.com/cache3/97/ql_4e7ea26d61c4a75e9c65d3a843739897_l3.png)
## Matrix Norm  
In addition to the properties of vector norms, square matrix norms satisfy one more:  
`L(AB) -leq L(A)L(B)`
However matrix norms are not limited to square matrices in any way.  
Common matrix norms:
* Frobenius Norm *(generalization of L2 over matrices)* `LF(•) = sqrt(trace(A*A))`  
* Spectral Norm *(square root of largest eigenvalue of A squared)* `L2(•) = sqrt(max(λ(A*A^T)))` 
* Maximum Sum over Rows Norm *(matrix p,q-norm with q = ∞)* `L1(•)`
* Maximum Sum over Columns Norms *(same as above but with p = ∞)* `L_inf(•)`
* Maximum Norm *(p = q = ∞)*  

In general:  
```python
Lp(A) := sup(Lp(Ax)/Lp(x), x != 0)
```
#### Spectral Radius
```python
ρ(A) := max(|eigenvalues(A)|) <= ||A||
```
