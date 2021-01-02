## Bisection Method
> Let `f(x)` be continuous in `[a,b]`.  
> Let `f(a) * f(b) < 0`.
> Then there exists such a value `c` in `(a,b)` satisfying `f(c) = 0`.

### Algorithm
```javascript
let lb = a, ub = b
//let eps = 0.0001 // or any other tolerance that seems reasonable
do {
	c = 1/2 * (lb + ub)
	if (c < 0) lb = c
	if (c > 0) ub = c
} while ( |f(c)| > eps )  
```
The usual termination conditions for this algorithm are `|f(c)| < eps` and `|ub - lb| < eps`, but `iterations -le MAX_ITER` is acceptable as a fallback.  
### Error
```haskell
Δc -le |b - a|/2^n     -- n being the number of iterations
-- which yields
n -le log₂(|b - a|/Δc)
```  
The above bounds can be used to estimate the number of iterations for a given tolerance.  
#### Minor Note
The algorithm is in essence a *binary search* and therefore `Γ(n) = θ(log₂(n))`.  
However, the method has been shown to be [nonoptimal in average](https://link.springer.com/article/10.1007/BF01396051) which has allowed for popular 
alternatives such as the *secant method*.
