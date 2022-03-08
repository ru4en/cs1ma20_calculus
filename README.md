# CS1MA20 - Spring Term Assignment

**Module Title:** Mathematics and Computation

**Module Code:** CS1MA20

**Student Number:** 30021591

**Git Repository:** [https://csgitlab.reading.ac.uk/il021591/cs1ma20_spring_assignment.git](https://csgitlab.reading.ac.uk/il021591/cs1ma20_spring_assignment.git)

**Lecturer responsible:** Professor Xia Hong

**Weighting of the Assignment:** 35%

**Date:** 09/03/2022

**Actual hrs spent for the assignment:** hrs

**Assignment evaluation :**

# Task 1

$$
f(x)= x^3+(-2)x^2+(-3)x+(0)
$$

## 1.  Plot the function f(x) with input x ranging from -15 to 15

```matlab
x = [-15:15]
y = x.^3+(-2)*x.^2+(-3)*x+(0)
plot(x,y)
```

![untitled3.png](CS1MA20%20-%20%205c5b2/untitled3.png)

## 2.  Find   $\frac{df}{dx}$

$$
3x^2 + 4x -3
$$

## 3.  Plot   $\frac{df}{dx}$

```matlab
x = [-15:15]
y = 3*x.^2+4*x-3
plot(x,y)
```

![untitled4.png](CS1MA20%20-%20%205c5b2/untitled4.png)

## 4.  Write code in Matlab that uses Newton-Raphson method to find all **three** roots of *f(x)*. You should implement the Newton-Raphson method yourself, rather than relying on an existing library. Show your code. Demonstrate that your code works by showing how you call it from the command line and what output Matlab gives. (If you found repeated roots in your question. Explain which ones are repeated.)

-1, 0 , 3

```matlab
function x = NewtonRaphsonMethod(x0)
% ^ turns file to a function and lets arg 0 be the estimate

format long;

x = x0;
f = @(x) x.^3+(-2)*x.^2+(-3)*x+(0);
% ^ function
fd = @(x) 3*x.^2+4*x-3;
% ^ derivite of the function

n = 100;
% ^ ittarations until answer found (approximations)
oldx = 0.1;

for i = 0:n
    x = x - f(x) / fd(x);
    % ^ the Newton Raphson Method
    % v break if answer found
    if oldx == x
        break
    else
    end
end
end
```

```matlab
>> NewtonRaphsonMethod(30)

ans =

   3.000000000000000
```

## 5.  Explain how different initializations are used for each root.

-1, 0 , 3

I used randoms numbers to find the closes root of the function. varable `n` was also incresed to improve the approximation of the root. I found three roots for the function -1, 0 , 3 using the arguments -1, 0 and 30.

```matlab
>> NewtonRaphsonMethod(30)

ans =

   3.000000000000000
```

```matlab
NewtonRaphsonMethod(-24)

ans =

     0
```

```matlab
>> NewtonRaphsonMethod(-1)

ans =

    -1
```

# Task 2

$$
f(x)=   (1)x^2+ (6)x+(5)

$$

## 1.  Find $\int f(x) dx$  by hand.

$$
\int f'(x)=(1)x^2+ (6)x+(5)
$$

$$
\int f'(x)= 2x +6
$$

$$
f(x) = \int (x^2+6x+5)dx
$$

$$
\frac {1}{3}x^3+\frac {6}{2}x^2+\frac {5}{6}x+c
$$

$$
\frac {1}{3}x^3+3x^2+5x+c
$$

## 2.  Plot the function  $\int f(x) dx$  over input *x* ranging from -15 to 15, by setting $*c=0*$.

```matlab
x=[-15:15]
c=0
y=((1/3)*x.^3) + (3*x.^2) + (5*x) + (c)
plot(x,y)
```

![untitled2.png](CS1MA20%20-%20%205c5b2/untitled2.png)

## 3.  Find  $\int ^{5} _{0} f(x) dx$  by hand.

$$
[1/3x^3 + 3x^2+5x]5
$$

$$
\frac{1}{3} (5) ^3 + 3(5)^2 +5(5)=(0)
$$

$$
f'(1)=\frac{1}{3}x^3 +3x^2+5x 
$$

$$
f'(0)=\frac{1}{3}0^3 +3(0)^2+5(0) = 0
$$

$$
f'(1)=\frac{1}{3}1^3 +3(1)^2+5(1) = 14.3333
$$

$$
f'(2)=\frac{1}{3}2^3 +3(2)^2+5(2) = 48.6666

$$

$$
f'(3)=\frac{1}{3}3^3 +3(3)^2+5(3) = 105
$$

$$
f'(4)=\frac{1}{3}4^3 +3(4)^2+5(4) = 185.3333
$$

$$
f'(5)=\frac{1}{3}5^3 +3(5)^2+5(5) = 291.6666
$$

= 345

## 4.  With integrating points [0 1 2 3 4 5], formulate Matlab built-in function *trapz.m* to find numerical solution of $\int ^{5} _{0} f(x) dx$.

```matlab
x=[0:5]
y= (1)*x.^2 + (6)*x+(5)
q=trapz(y)
```

q=142.5000

## 5.  Use Matlab built-in function *integral.m* to find numerical solution of  $\int ^{5} _{0} f(x) dx$.

```matlab
fun=@(x) (1/3)*x.^3 +3*x.^2+5*x
xmin=0
xmax=5
q = integral(fun,xmin,xmax)
```

q = 239.5833

## 6.  **Write Euler’s method in Matlab to solve $\frac{dy}{dx} = f(x)$, with initial condition *y(0)=0,* step size *h=0.5,* for ten steps.

```matlab
h=0.5; % step's size
N=10; % number of steps
 
x=0:N;
dx = (1)*x.^2 + (6)*x+(5);
dy = ((1/3)*x.^3) + (3*x.^2) + (5*x);

plot(dx, dy)
```

![untitled3.png](CS1MA20%20-%20%205c5b2/untitled3%201.png)

# Task 3

## 1.  Represent this robotics system in a vector differential equation form (state space model).

## 2.  **Implement a code to call Matlab built- in function *****ode45.m**,* with time span [0 20], initial conditions $*y(0)=0, y’(0) =0$.*

## 3.  Plot the position *y* and velocity $*\frac{dy}{dt}*$, and briefly discuss the simulated motion.

# Task 4

$$
a =1+11i
$$

$$
b =8+91i
$$

## 1.  Add *a* and *b*

 $*a+b =*$

## 2.  Multiply *a* and *b*

 $*ab =*$

## 3.  Divide *a* by *b*

$*a/b =*$

## 4.  Represent *a* and *b* in polar form, clearly state the magnitude/angle values.