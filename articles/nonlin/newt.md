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
Δc -le |b - a|/2^(n+1)     -- n being the number of iterations
-- which yields
n -le log₂(|b - a|/Δc) - 1
```  
The above bounds can be used to estimate the number of iterations for a given tolerance.  
#### Minor Note
The algorithm is in essence a *binary search* and therefore `Γ(n) = θ(log₂(n))`.  
However, the method has been shown to be [nonoptimal in average](https://link.springer.com/article/10.1007/BF01396051) which has allowed for popular 
alternatives such as the *secant method*.

## Newton's Method
> Also known as Method of Tangents  

Recall that the equation for a tangent line is `Δy = f'(x₀)(x - x₀)` with (obvs.) `Δy = f(x) - f(x₀)`.  
What Newton's Method is is an iterative application of this formula for `f(x) = 0` (hence it being a root-finding algorithm).  
More precisely, `-f(xᵢ) = f'(xᵢ)(xᵢ₊₁ - xᵢ)`, from which we get `xᵢ₊₁ = xᵢ - f(xᵢ)/f'(xᵢ)`.  

### Conditions of Convergence
Let `f(x)` be twice differentiable.
Let `sgn(f'(x))` and `sgn(f''(x))` be constant.  
Let there be `x₀` such that `f(x₀) * f''(x₀) > 0` [†](#notes). Then the method converges if starting from `x₀`.  

### Algorithm
```python
df = derivative(f)

for i in range(MAX_ITER):
  if df(x) == 0:
    raise ZeroDivisionError
  x = x - f(x)/df(x)
  if f(x) < eps:
    break
```  
A less expensive version would be using only `f'(x₀)` in the calculations. 

### Secant Method
Similar to **Newton's Method** but uses a secant line instead of a tangent line *(finite difference)*.  
A secant line can be expressed as `Δy/Δx = f(x)-f(x₀)/(x - x₀)`. Knowing that we can interpolate a single iteration as:  
```
xᵢ₊₂ = xᵢ₊₁ - f(xᵢ₊₁)(xᵢ₊₁ - xᵢ)/(f(xᵢ₊₁) - f(xᵢ))
```
### Termination Conditions
For these methods most used are:  
* `|xᵢ₊₁ - xᵢ| -le eps`;  
* `|xᵢ₊₁ - xᵢ|/|xᵢ| -le eps`;  
* `f(xᵢ) -le eps`;  
* `|bᵢ - aᵢ| -le eps` *(bisection only)*.

#### Notes
†: Such a number is called a **Fourier Extreme**.
