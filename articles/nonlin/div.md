## Divided Differences
> *Divided Differences* is a recursive division algorithm used to calculate the coefficients of the polynomial in a *Newton's Polynomial*.  

### Definition
![divdiffdef](/img/approx/divdiffdef.png)  

with `i` in `[0, n+1]` and `j` in `[1, n+1]`.  
It can be shown that the divided differences are the coefficients of *Newton's Polynomial*:  
```python
A₀ = [y₀] = y₀;  
A₁ = [y₀, y₁] = (y₁ - y₀) / (x₁ - x₀);  
A₂ = [y₀, y₁, y₂] = (1 / x₂ - x₀) * (A'₁ - A₁)` with `A'₁ = [y₁, y₂] = (y₂ - y₁) / (x₂ - x₁)
```
An apparent advantage is that changing the order of arguments in the latter differences doesn't force use to recalculate the coefficient.  

### Tabular Form
