## Newton's Method
> Also known as Method of Tangents  

Recall that the equation for a tangent line is `Δy = f'(x₀)(x - x₀)` with (obvs.) `Δy = f(x) - f(x₀)`.  
What Newton's Method is is an iterative application of this formula for `f(x) = 0` (hence it being a root-finding algorithm).  
More precisely, `-f(xᵢ) = f'(xᵢ)(xᵢ₊₁ - xᵢ)`, from which we get `xᵢ₊₁ = xᵢ - f(xᵢ)/f'(xᵢ)`.  

### Conditions of Convergence
Let `f(x)` be twice differentiable in a certain interval `[a, b]`.
Let `sgn(f'(x))` and `sgn(f''(x))` be constant.  
Let there be `x₀` in `[a, b]` such that `f(x₀) * f''(x₀) > 0` [†](#notes). Then the method converges if starting from `x₀`.  

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


#### Notes
†: Such a number is called a **Fourier Extreme**.
