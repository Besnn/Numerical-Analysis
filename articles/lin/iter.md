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
* `||M⁻¹N|| < 1` (sufficient[†](https://github.com/Besnn/Numerical-Analysis/blob/main/articles/lin/iter.md#notes))  
#### Notes
