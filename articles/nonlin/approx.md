## Approximation of Data ⅋ Functions
The need of approximating a function arises when:  
* we are dealing with a very complicated and expensive *(to calculate)* function;  
* we know only discrete values of that function.  

Both cases are similar, in that in the first case we also have to use a lookup table of discrete values.  
The error is handled according to needs:  
* If the data contains residual error, it should be approximated within the dataset; 
* In case the data is correct, we look for a function to fit this data.  

## Function Classes
Some functions are more suited than others when it comes to approximating values from datasets.  
These are split into classes according to properties of interest *(ease of use, generality etc.)*.  

### Polinomials
The most simple functions to use and implement.
### Rational Functions
Wider range of coverage than polinomials.
### Trigonometric Functions
Useful for periodicity.
### Splines
Piecewise functions. Can approximate most anything.  
