## Representation of Numbers
### Integers
> ![rappr](http://www.sciweavers.org/tex2img.php?eq=%24%28a_ma_%7Bm-1%7D...a_1a_0%29_%20%5Cbeta%24%20with%20%24i%20%3D%201...m%24%20and%20%240%20%5Cleq%20a_i%20%3C%20%5Cbeta%24&bc=White&fc=Black&im=png&fs=30&ff=modern&edit=0)
### Real Numbers
> ![rappr2](http://www.sciweavers.org/tex2img.php?eq=%20%24%5Cpm%200.a_1a_2...a_m%5Cbeta%5Eb%24%20such%20that%20%24a_1%20%20%5Cneq%200%24%20and%20%24m%20%5Cleq%20%5Cinfty%24&bc=White&fc=Black&im=png&fs=30&ff=modern&edit=0)  

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
