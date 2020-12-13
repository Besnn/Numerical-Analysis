## Conditioning of a Linear System
Let `A` be a nonsingular matrix and `Ax = b` the corresponding system.  
### Simple Case
Disturbances on `x` lead to disturbances on `b`.  
```vim
A(x + δx) = b + δb
```  
#### Relative Error
![re](/img/ka.png)
##### Minor note
`δx/x` is the relative error on the output, because in a linear system `Ax=b`, `A` as the function/constraints matrix and `b` as the parameter, we expect `x` as output.
