## Interpolation of Data
Let `S = {(xᵢ, yᵢ) | x ∈ [a, b]; xᵢ ≠ xⱼ if i ≠ j}` represent the set of points on the graph and 
`V = {φ₀, φ₁, ...,φₙ}` be a set of approximating functions defined on `[a, b]` and linearly independent [†](/articles/nonlin/interp.md#notes).  
We want to define `g ∈ [a, b]; g(x) = sum([ αᵢ * φᵢ for φᵢ in V]); g(xᵢ) = yᵢ`.  

### Polynomial Interpolation
If the class of functions is chosen to be a polynomial, then the coefficient of the polynomial can be concluded
by solving the [appropriate linear system](/articles/nonlin/best.md#best-fit-polynomials).  
Generally, the higher the order of the polynomial,
the better the approximation. You don't want to overdo it though *(computational cost increases linearly for polynomials)*.   

### Existence and Uniqueness
Let `A` be a [*Vandermonde Matrix*](https://www.wikiwand.com/en/Vandermonde_matrix).
```applescript
let it be nonsingular IFF for xᵢ ≠ xⱼ if i ≠ j : det(A) = ∏ ∏(i>j) of xᵢ - xⱼ
```  
Then the interpolating polynomial of degree `n` is unique.  

### 

### Notes
†: A set of functions are linearly dependent if there is a vector `α ≠ 0` such that `sum(α * fᵢ(x)) = 0`.
