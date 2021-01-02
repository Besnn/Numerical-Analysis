## Validity of an iterative method
### Theorem
> Let {`x`⁽ᵏ⁾} be a sequence of vectors and `A = M - N` a square matrix of size `n`.  
Then the sequence converges to the correct value **only and only if** `M⁻¹N` converges to `zero`.  
#### Proof
Let `Δ⁽ᵏ⁾ = x⁽ᵏ⁾ - x`. Then `x⁽ᵏ⁾ tends to x IFF Δ⁽ᵏ⁾ tends to 0`.  
Let `Δ⁽⁰⁾ = x⁽⁰⁾ - x`.  
Then `Δ⁽ᵏ⁾ = x⁽ᵏ⁾ - x = M⁻¹Nx⁽ᵏ⁻¹⁾ + M⁻¹b - M⁻¹Nx - M⁻¹b = (M⁻¹N)Δ⁽ᵏ⁻¹⁾ = (M⁻¹N)²Δ⁽ᵏ⁻²⁾ = ... = (M⁻¹N)ᵏΔ⁽⁰⁾`.  
It is obvious that since `Δ⁽ᵏ⁾ = (M⁻¹N)ᵏΔ⁽⁰⁾` and the LHS converges to `zero`, `(M⁻¹N)ᵏ` converges to `zero` (`Δ⁽⁰⁾` constant). ■   
### Convergence Conditions
An iterative method converges:
* IFF `M⁻¹N` converges;  
* IFF `ρ(M⁻¹N) := max(eigenvalues(M⁻¹N)) < 1`;
* `||M⁻¹N|| < 1` (sufficient [†](https://github.com/Besnn/Numerical-Analysis/blob/main/articles/lin/iter.md#notes));  
* `A` is diagonally dominant in the strict sense (`A[i][i] > |sum of row elements w/o A[i][i]|`; sufficient);  
* *(applies only to Gauss-Siedel)* `A` is symmetric and definite-positive (sufficient).

### Termination Condition
[As noted before](https://github.com/Besnn/Numerical-Analysis/blob/main/articles/lin/resolution.md#types-of-numerical-methods),
iterative methods are often equipped with termination conditions.  
Some very in fashion *(as of always)* conditions are:  
* `||x⁽ᵏ⁺¹⁾ - x⁽ᵏ⁾|| -le ϵ`;
* `||x⁽ᵏ⁺¹⁾ - x⁽ᵏ⁾|| / ||x⁽ᵏ⁺¹⁾|| -le ϵ`;
* `||r⁽ᵏ⁾|| := ||Ax⁽ᵏ⁾ - b|| -le ϵ` *(`r` is the 
[residual](https://github.com/Besnn/Numerical-Analysis/blob/main/articles/lin/k.md#conditioning-of-a-linear-system) vector)*.
##### Minor Note
A little residual error does not imply that `x⁽ᵏ⁾` is close to `x`.
#### Notes
A condition is **sufficient** if it represents `S` in `S => N`. Sufficiency implies that `N` has to be `true` for `S` `true`.  
Likewise, it is **necessary** if it represents `N` in `S => N`. Necessity implies `S` has to be `false` for `N` `false`.
