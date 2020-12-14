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
```ocaml
h := 1 " Initialization of the pivot row "
k := 1 " Initialization of the pivot column "

while h ≤ m and k ≤ n
    " Find the k-th pivot: "
    i_max := argmax (i = h ... m, abs(A[i, k]))
    if A[i_max, k] = 0
        " No pivot in this column, pass to next column "
        k := k+1
    else
         swap rows(h, i_max)
         " Do for all rows below pivot: "
         for i = h + 1 ... m:
             f := A[i, k] / A[h, k]
             " Fill with zeros the lower part of pivot column: "
             A[i, k] := 0
             " Do for all remaining elements in current row: "
             for j = k + 1 ... n:
                 A[i, j] := A[i, j] - A[h, j] * f
         " Increase pivot row and column "
         h := h + 1
         k := k + 1
```
