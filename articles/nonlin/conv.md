## Rate of Convergence
> The **rate of convergence** *(a.k.a. **order of convergence**)* of a method is a metric used to measure 
how quickly the sequence of solutions converges to a desirable value.  

A sequence is said to have an order of convergence `p` if the following holds true:  

![conv_order](/img/resolution/conv_order.png)  

For `p = 1`, the order of convergence is **linear**; `p = 2` **quadratic** and so on.  
The constant `μ` is called *asymptotic error constant*.  

### Bisection Method
The **Method of Bisection** has a linear rate of convergence.  

![conv_bisect](/img/resolution/conv_bisect.png)  

### Newton's Method
> [Proof of Convergence for Newton's Method](https://www.wikiwand.com/en/Newton%27s_method#/Proof_of_quadratic_convergence_for_Newton's_iterative_method)  

**Newton's Method**, on the other hand, has a quadratic rate of convergence:  


![conv_newts](/img/resolution/conv_newt.png)  
