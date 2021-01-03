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
* Manhatan Norm `L1(•) = |x| + |y| + |z| + ...`  
* Maximum `L_inf(•) = max(|•|)`  

The general form for a p-norm is:  
![p-norm](/img/norms/p-norm.png)
### Unit Graphs of different p-norms  
<img src='/img/norms/L0.png' width='256'></img>
<img src='/img/norms/L½.png' width='256'></img>
<img src='/img/norms/L1.png' width='256'></img>
<img src='/img/norms/L2.png' width='256'></img>
<img src='/img/norms/L4.png' width='256'></img>
<img src='/img/norms/L∞.png' width='256'></img>  
```python
""" Note that L0 is not a 'true' norm. It does not satisfy scalability. Additionally, it has no pth-root: """
    L0(x) = sum(x1^0 + x2^0 + ... + xn^0)
""" That is the number of nonzero elements in vector x. """
    v = [1 1]
    L0(2*v) = 2 -neq 2*L0(v) = 4
""" In general, any p-norm with p less than 1 is not considered a norm. """
```
## Matrix Norm  
In addition to the properties of vector norms, square matrix norms satisfy one more:  
`L(AB) -leq L(A)L(B)`
However matrix norms are not limited to square matrices in any way.  
Common matrix norms:
* Frobenius Norm *(generalization of L2 over matrices)* `LF(•) = sqrt(trace(A*A^-1))`  
* Spectral Norm *(square root of largest eigenvalue of A squared)* `L2(•) = sqrt(max(λ(A*A^T)))` 
* Sum over Absolute Row Maxima *(matrix p,q-norm with p = 1, q = ∞)* `L1(•)`
* Sum over Absolute Column Maxima *(same as above but with p = ∞, q = 1)* `L_inf(•)`
* Maximum Norm *(p = q = ∞)*  

In general:  
```python
Lp(A) := sup(Lp(Ax)/Lp(x)) with x not 0 = max(Lp(Ax)) with Lp(x)=1
```
#### Spectral Radius
```python
ρ(A) := max(|eigenvalues(A)|) """ -leq ||A|| 
 ||A|| being a given norm """
```
