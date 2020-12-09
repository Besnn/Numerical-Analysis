## Representation of Numbers
### Integers
> ![rappr](https://quicklatex.com/cache3/53/ql_e3c069a0c9ef5dc61555ce9487b24953_l3.png)
### Real Numbers
> ![rappr2](http://www.sciweavers.org/tex2img.php?eq=%24%5Cpm%200.a_1a_2...a_m%5Cbeta%5Eb%24%20such%20that%20%24a_1%20%5Cneq%200%24%20and%20%24m%20%5Cleq%20%5Cinfty%24%20&bc=White&fc=Black&im=jpg&fs=30&ff=modern&edit=0) 

The string of **a**s is called the `mantissa`, while **b** is the `characteristic`.
#### Note
By convention, `x = 0` has a nil mantissa and a null characteristic.
## Machine Representation of Numbers
Let the number of bits available for storing a number be `m`.  
If we are storing signed integers, then the leftmost bit is used to express the sign. Which leaves `m-1` bits to store magnitude.

The maximum number we can store in `m` bits is `2^(m-1) - 1` for signed and `2^m - 1` for unsigned integers.  
Attempting to store a *m*-bit long number in `m-1` bits will result in an overflow, and the number will be stored as `[number] mod [max_value]`.

If the number to be stored is a real number, the machine representation may not reflect the real *(pun?)* value of the number.  
The standard for representing real numbers in binary is specified by *IEEE754* and for 32-bit and 64-bit spaces is as follows:  
`[n] will signify n bits`  
> [1] for sign; [8] for characteristic; [23] for mantissa for 32-bit floats  
> [1] for sign; [11] for characteristic; [52] for mantissa for 64-bit floats
### Note
Since the very first figure is implicit (and 1 by convention), we actually have 24 bits and 53 bits for storing the figures respectively for 32-bit and 64-bit.  
**Overflow** happens when the characteristic (and by extension the exponent) of a number is not rappresentable in the given space.  
Same with **Underflow**: the characteristic is too small *(number is smaller than machine epsilon)*.  
The mantissa usually limits the *precision*.
