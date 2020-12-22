## Cramer's Rule
Given a linear system `Ax=b` and `A` square and nonsingular, the value of `x` is unique. More specifically,  
```python
x = A^-1 * b
" and by Cramer's Rule "
x[i] = det(A[i])/det(A)
```
The problem with this algorithm is that it is very costly computationally to calculate determinants *(factorial complexity if using 
[Cofactor Expansion](https://www.wikiwand.com/en/Laplace_expansion))*.
## Types of Numerical Methods
There are 2 types of *numerical methods* for resolving a given linear system:  
* **Direct Methods**: In the absence of numerical errors, direct methods yield the exact solution within a finite number of steps.  
* **Iterative Methods**: Such methods approximate the solution from a starting vector, and are often equipped with a [terminating condition](/articles/alg/def.md#terminating-condition).  
### Note
*Direct Methods* are more suited to **dense** matrices of **minor** order.  
*Iterative Methods* are more suited to **sparse** but **vast** matrices.  
#### Random Tip
When possible, use `\` and `/` *(left and right division respectively)* instead of `inv()` in **MATLAB**. They are both more efficient and accurate compared to inversion.  
## Gaussian Elimination
```python
# Ax = b
# A is m×n, x is size n and b is size m
# since pivots are in a diagonal, n in the range should be min(m, n)
for i in range(n):
    if A[i][i] == 0.0:
        raise ZeroDivisionError

    for j in range(i+1, n):
        ratio = A[j][i]/A[i][i]
        
        for k in range(n+1):
            A[j][k] = A[j][k] - ratio * A[i][k]
        b[j] = b[j] - ratio * b[i]

```
