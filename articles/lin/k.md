## Conditioning of a Linear System
Let `A` be a nonsingular matrix and `Ax = b` the corresponding system.  
Let `δb` and `δA` be called the *residual* and instead let *error* be used for `δx`.  
### Simple Case
Disturbances on `x` lead to disturbances on `b`.  
```vim
A(x + δx) = b + δb
```  
#### Relative Error
![ka](/img/k/ka.png)
##### Minor note
`δx/x` is the relative error on the output, because in a linear system `Ax=b`, `A` as the function/constraints matrix and `b` as the parameter, we expect `x` as output.  
> Very frequently, one is solving the inverse problem: given f(x) = y, one is solving for x, and thus the condition number of the (local) inverse must be used.

### General Case
Disturbances on both matrix `A` and vector `b`  

![ska](/img/k/ka2.png)  
#### Example
Let `A` be a **Hilbert Matrix** with `n` columns. Let `||A||` be the p-norm of matrix `A`. Then:  
```matlab
% run on MATLAB interpreter
% p can be anything equal or greater than one
% K(A) is by definition the product of ||A|| and ||inv(A)||

p = 2

for n=2:20
    condition_no = norm(hilb(n)^-1, p) * norm(hilb(n), p)
end
```
Starting from the *12th iteration*, you should get something like this `Warning: Matrix is close to singular or badly scaled. Results may be inaccurate.`; This means that the matrix is ill-conditioned and the condition number has a large value *(1.5619e16 for n=12; 2.4944e18 for n=20)*.  
#### Another Example
From [a previous example](https://github.com/Besnn/Numerical-Analysis/blob/main/articles/lin/cond.md#conditioning-of-a-linear-system) we get the following matrices:  

![ill-matrices](/img/k/ill-matrices.png)  

In case of `∞-norm` we get that `K(A) = 4e5`, which is a large condition number.
