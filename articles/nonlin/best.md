## Polynomial Least Squares
Let the pairs of the dataset `(xᵢ, yᵢ)` contain error.  
We want to be able to approximate this dataset via a polynomial.  

Two things are needed to establish this polynomial:  
* the order of the polynomial *(linear, quadratic and so on)*;  
* a metric/criterion measuring the viability of the polynomial.  

### Viability
Let `E = y - (a₀ + a₁x + a₂x² + ...)` be the error, `y` be the data vector and `(a₀ + a₁x + a₂x² + ...)` be the approximating polynomial.  
By this metric, the more appropriate polynomial would be the one to yield `E` smallest in value.  

**Popular criteria:**  
* `min(L1(E))` *(L1-Norm of Error Vector)*;  
* `min(L2(E))` *(Euclidean Norm of `E`)*;  
* `min(L∞(E))` *(Maximum Component of `E`)*.  

In *Least Squares Fitting*, the best fit polynomial is the one satisfying the criterion of the *L1-Norm*.  

### Line of Best Fit
![line](/img/approx/line.png)  

### Satisfying the Criterion
![diff_line](/img/approx/diff_line.png)  

Equaling to zero *(for the minimum/minima)* should yield the following system of equations:  
> ![syseq](/img/approx/syseq.png)

### Matricial Form
The following linear system is equivalent to the above:  

![syseq2](/img/approx/syseq2.png)  
and is easily solvable. 

### Best Fit Polynomials
The procedure is similar for finding other best fit polynomials. The matrix form can be generalized as:  

![monster](/img/approx/monster.png)  

It being a **positive-definite matrix**, the solution is unique.  
