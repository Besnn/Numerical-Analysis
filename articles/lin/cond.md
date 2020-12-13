## Conditioning
>A well-conditioned problem is a problem where a small change of the input cannot lead to a big change of the output.  
>A problem that is ill-conditioned if it is not well-conditioned.
### Conditioning of a linear system
![ill](/img/ill.png)  
A small change of `2e-5` in the input led to a change of `2e5` in the output.  
Moreover
```lua
-- let k(A) be the condition number of a system
-- and
'absolute' k(A) = Δf(x)/Δx
'relative' k(A) = (Δf(x)/f(x)) / (Δx/x) --gets rid of magnitude
```
then the *absolute condition* number of our system is `10^10`, which is a great number relative to our inputs and solutions, and should give us an idea of how wrong things went. 
## Stability
> A stable algorithm is an algorithm that avoids small errors summing up to a big error.  
> For every input, the result has an accuracy not much worse than the accuracy with which the single steps are done.  

![e](/img/e.png)
