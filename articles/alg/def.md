## Definition of Algorithm
> A finite set of unambiguous instructions that, given some set of initial conditions, 
can be performed in a prescribed sequence to achieve a certain goal and that has a recognizable set of end conditions.
### To break it down:
* An algorithm consists of a number of *clear* (unambiguous) instructions.  
* These instructions, if executed, take *data* and produce *results* from them.   
* This execution will eventually terminate.
### Basic Requirements
An algorithm must satisfy two fundamental requirements for it to be considered an algorithm:
* Generality *(resolve a class of problems)*
* Optimality
## Horner's Method
### What it is and why it is important
Horner's Method (or Algorithm) is a method for evaluating polynomials.  
It is a very efficent. Why? The standard algebric way to evaluating polynomials looks something like this:  
> ![pn](http://www.sciweavers.org/tex2img.php?eq=P_n%28x%29%20%3D%20%20%5Csum_%7Bi%3D0%7D%5En%20%5Calpha_i%20x%5En%20&bc=White&fc=Black&im=png&fs=30&ff=modern&edit=0)
```lua
read n, a, x
set p = 1
set s = a[0]
for i in range(1..n):
    set p = x*p -- 1 multiplication
    set s = s + a[i]*p -- 1 multiplication and 1 addition
write s
end
```
So how does Horner's Method differ? It performs one multiplication less, which for long polynomials can yield huge savings.
```lua
read n, a, x
set s = a[n]
for i in range(n-1, 0):
    set s = s*x + a[i] -- 1 multiplication and 1 addition
write s
end
```
### Termination Condition (Criterio di arresto)
To ensure an algorithm terminates, the number of iterations can be limited to a certain number. This is especially useful for inefficient algorithms *(think `n!` complexity or even polynomial)*
