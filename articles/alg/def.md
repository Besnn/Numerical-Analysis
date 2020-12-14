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
> ![pn](/img/alg/pn.png)  

Horner's Method (or Algorithm) is a method for evaluating polynomials.  
It is very efficent. Why? The standard algebric way to evaluating polynomials looks something like this:  

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
### Terminating Condition
To ensure an algorithm terminates, the number of iterations can be limited to a certain number. This is especially useful for inefficient algorithms *(think `n!` complexity or even polynomial)*.
