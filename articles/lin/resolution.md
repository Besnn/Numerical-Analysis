## Cramer's Rule
Given a linear system `Ax=b` and `A` square and nonsingular, the value of `x` is unique. More specifically,  
```python
x = A^-1 * b
" and by Cramer's Rule "
x[i] = det(A[i])/det(A)
```
The problem with this algorithm is that it is very costly computationally to calculate determinants *(factorial if using 
[Cofactor Expansion](https://www.wikiwand.com/en/Laplace_expansion))*.
## Types of Numerical Methods
There are 2 types of *numerical methods* for resolving a given linear system:  
* **Direct Methods**: In the absence of numerical errors, direct methods yield the exact solution within a finite number of steps.  
* **Iterative Methods**: Such methods approximate the solution from a starting vector, and are often equipped with a [terminating condition](/articles/alg/def.md#terminating-condition).  
#### Note
*Direct Methods* are more suited to **dense** matrices of **minor** order.  
*Iterative Methods* are more suited to **sparse** but **vast** matrices.  
#### Random Tip
When possible, use `\` and `/` *(left and right division respectively)* instead of `inv()` in **MATLAB**. They are both more efficient and accurate compared to inversion.  
## Gaussian Elimination
```python
"""
Ax = b
A is m×n, x is size n and b is size m
since pivots are in a diagonal, n in the range should be min(m, n)
"""
for i in range(min(m,n)):
    if A[i][i] == 0.0:
        raise ZeroDivisionError

    for j in range(i+1, m):
        ratio = A[j][i]/A[i][i]
        
        for k in range(n):
            A[j][k] = A[j][k] - ratio * A[i][k]
        b[j] = b[j] - ratio * b[i]

```
**Gaussian Elimination** can be used to calculate *inverse matrices*. Remember that by applying gaussian elimination to the *augmented matrix* `A|I` of `A * A' = I`, we can arrive to `I|A'`. More specifically, this equation can be split into `n` systems, one for each column, such that they are of the form `Ax = e`. Solving for `x` we get the **n**__*th*__ column of the `A'` matrix.  
## Resolution of an Upper Triangular Matrix
```python
""" Backward Substitution """
if A[n][n] == 0:
    raise ZeroDivisionError
x[n] = b[n]/A[n][n]
for i in range(n-1, 1):
    x[i] = (b - sum([ x[k]A[i][k] for k in range(i+1, n)])

```

## Swapping Rows
```applescript
Given 2 rows labeled α and β, exchange of rows can be performed as follows:
> substract from β row α
> add row β to α
> substract row α from β
> multiply β by -1

Analogous for columns
Useful when leading pivot is zero (null)
```
## Applicability and Determinants
```applescript
Given the following postulates:
> swapping two rows multiplies the determinant by −1,
> multiplying a row by a nonzero scalar multiplies the determinant by the same scalar,
> adding to one row a scalar multiple of another does not change the determinant;
Let R be the row echelon form for matrix A.
Let c be the coefficient by which the determinant is multiplied according to the postulates.
Then:   det(A) = 1/c * product(diag(R))

Moreover, let A(k) be the principal minor of A of order k.
If det(A(k)) is nonzero for all k then "Gaussian Elimination" is applicable.
```
## Instability and Pivoting
![gauss_ins](/img/resolution/gauss-ins.png)  
### Partial and Complete Pivoting
```applescript
Swapping rows such that the pivot is the maximum element
in that particular column is called "Partial Pivoting".    
This approach tries to mitigate division by small values,
which is inaccurate in finite-precision relative to the field of real numbers.
Sometimes it is necessary to utilize "Complete Pivoting",
which exchanges columns too.
```
