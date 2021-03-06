## Interpolation of Data
Let `S = {(xᵢ, yᵢ) | x ∈ [a, b]; xᵢ ≠ xⱼ if i ≠ j}` represent the set of points on the graph and 
`V = {φ₀, φ₁, ...,φₙ}` be a set of approximating functions defined on `[a, b]` and linearly independent [†](/articles/nonlin/interp.md#notes).  
We want to define `g ∈ [a, b]; g(x) = sum([ αᵢ * φᵢ for φᵢ in V]); g(xᵢ) = yᵢ`.  

### Polynomial Interpolation
If the class of functions is chosen to be a polynomial, then the coefficient of the polynomial can be concluded
by solving the [appropriate linear system](/articles/nonlin/best.md#best-fit-polynomials).  
Generally, the higher the order of the polynomial,
the better the approximation.  

### Existence and Uniqueness
Let `A` be a [*Vandermonde Matrix*](https://www.wikiwand.com/en/Vandermonde_matrix).
```applescript
let it be nonsingular IFF for xᵢ ≠ xⱼ if i ≠ j : det(A) = ∏ ∏(i>j) of xᵢ - xⱼ
```  
Then the interpolating polynomial of degree `n` is unique for `n+1` values of `xᵢ`.  
**In other words**: Nonsingularity of Vandermonde Matrix implies polynomial existence.  

#### Possible Obstacles
* `A` is ill-conditioned;  
* `xᵢ` and `xⱼ` can be equal in finite arithmetic.  

### Notes
†: A set of functions are linearly dependent if there is a vector `α ≠ 0` such that `sum(α * fᵢ(x)) = 0`.
