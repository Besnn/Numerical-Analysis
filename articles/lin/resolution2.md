### Essence of Iterative Methods
Iterative methods converge to a correct *(approximate)* solution of a linear system from a starting vector. That is:  
> The method generates a sequence of vectors {`x`⁽ᵏ⁾} 
such that the limit for `x tends to infinity` of {`x`⁽ᵏ⁾} is the correct solution (`x`).  

A particular iteration of the sequence is denoted as `x`⁽ⁱ⁾
### The Jacobi ⅋ Gauss-Seidel Method
#### Jacobi Method
For an upper triangular matrix, the solution can be expressed as:  
```python
x[i]⁽ᵏ⁺¹⁾ = 1/a[i][i] * (b - sum([ x[k]⁽ᵏ⁾A[i][k] for k in range(i+1, n)]))
```
This can be generalized for a given matrix as:
```python
x[i]⁽ᵏ⁺¹⁾ = 1/a[i][i] * (b
            - sum([ x[k]⁽ᵏ⁾A[i][k] for k in range(i-1)]) - sum([ x[k]⁽ᵏ⁾A[i][k] for k in range(i+1, n)]))
```
#### Gauss-Seidel Method
The Gauss-Seidel Method is a modification of the Jacobi Method.  
The difference between the two methods is that new values of {`x`⁽ᵏ⁾} are used as soon as they become available.  
For example, the new values of `x₁` can be used in the calculation of `x₂`, the new values of the previous two  
can be used to calculate `x₃` and so on.

### Matrix Formulation of Jacobi Method
> Let `A` be expressed as the sum of 3 matrices. Let those matrices be marked `L`, `D` and `U`, 
representing respectively the lower triangular, the diagonal matrix and the upper triangular matrix.  

Then:
```python
" The formula for Jacobi/Gauss-Seidel "
a[i][i] * x[i]⁽ᵏ⁺¹⁾ = (b - sum([ x[k]⁽ᵏ⁾A[i][k] for k in range(i-1)])
                         - sum([ x[k]⁽ᵏ⁾A[i][k] for k in range(i+1, n)]))
```
can be rewritten as
```typescript
Dx⁽ᵏ⁺¹⁾ = b - Lx⁽ᵏ⁾ - Ux⁽ᵏ⁾

or

x⁽ᵏ⁺¹⁾ = D \ (b - Lx⁽ᵏ⁾ - Ux⁽ᵏ⁾) if using MATLAB or some other dumb language

or even

Dx⁽ᵏ⁺¹⁾ = b - Lx⁽ᵏ⁾ - Ux⁽ᵏ⁾ => (D + L)x = b - Ux⁽ᵏ⁾
x⁽ᵏ⁺¹⁾ =  (D + L)⁻¹(b - Ux⁽ᵏ⁾)
```
