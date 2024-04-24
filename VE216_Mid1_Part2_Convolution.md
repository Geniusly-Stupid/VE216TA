# Chapter 2 - Convolution

[toc]

## Linear and Time-Invariant (LTI) Systems

### What is LTI Property? 

**Linearity**:

For a linear system, if $x_1(t) \xrightarrow{\tau} y_1(t)$ and $x_2(t) \xrightarrow{\tau} y_2(t)$, then $ax_1(t) + bx_2(t) \xrightarrow{\tau} ay_1(t)+by_2(t)$.

**Time-Invariance**:

For a time-invariant system, if $x(t) \xrightarrow{\tau} y(t)$, then $x(t-t_0) \xrightarrow{\tau} y(t-t_0)$.

### Why LTI Property Matters?

LTI property **simplify** the analysis of a system. Specifically, it makes the system design and response analysis easier. 

In this chapter, we cares how to analyze LTI system using **convolution** methods.

**Questions**: 

1. **How to design an LTI system?** 

   We only need to care about its impulse response $h(t)$, since an LTI system is completely described by its impulse response $h(t)$.

2. **How to determine the response $y(t)$ of LTI systems?** 

   Known $h(t)$, we can determine the response $y(t)$ following these steps: 

   1. Decompose the input signal $x(t)$ into delayed impulses $\delta(t-\tau)$.
   
   2. Use convolution to solve: $y(t)=x(t)*h(t)$.


## Convolution

### What is Convolution?

$x(t)$ can be decomposed into delayed impulses
$$
x(t) = \int_{-\infty}^{\infty}x(\tau)\delta(t-\tau)d\tau.
$$
Denoted 
$$
\delta(t) \xrightarrow{\tau} h(t),
$$
For LTI system, the corresponding response $y(t)$ can be derived using LTI property, which is
$$
y(t) = \int_{-\infty}^{\infty}x(\tau)h(t-\tau)d\tau = x(t) * h(t).
$$
**Question: **

1. **Why we can decompose $x(t)$​ into delayed impulses? **

   - Hint: Start from discrete case $x[n]$ to understand the idea,  and build an approximation by short time impulses ($\Delta \rightarrow 0$)

   

2. **How to derive the convolution integral using LTI property?** 

   - Hint 1: $x(\tau)$​ is a constant so that we can use linearity property. 

   - Hint 2: $\delta(t-k) \xrightarrow{\tau} h_k(t)$, since the system is TI, $\delta(t-k) \xrightarrow{\tau} h(t-k)$









### Why Convolution? 

An LTI system is completely described by its impulse response $h(t)$​. 

Any system whose input-output relationship can be expressed in $y(t)=\int_{-\infty}^{\infty}x(\tau)h(t-\tau)d\tau = x(t)*h(t)$​​​ is time-invariant. 



**THEREFORE**, turn $y(t)$ to the form $h(t)*x(t)$, then we can directly get $h(t)$. 

In many cases, there's NO need to substitute $x(t)$ with $\delta(t)$ in the algebra representation of $y(t)$ to solve $h(t)$. 

**Exercise: **

1. Find the impulse response of the LTI systems. 
   $$
   y(t) = \int_{-3}^{3}\tau^2x(t-\tau)d\tau + \int_{-\infty}^{t+1}(t-\tau+3)^{-2}x(\tau)d\tau
   $$











**Summary**: How to turn $y(t)$ expression to the form $h(t)*x(t)$​?

1. Use $u(t)$ to substitute range of integration
2. Turn to convolution form (first find $t-\tau$ and $\tau$ , then substitute them with $t$ ).



### Graphical Method for Convolution Calculation

For time-limited signals, it’s more convenient and intuitive to calculate the convolution with the help of graphics.

**Steps**: (Exchange the role of h and x is fine)

- Fold: fold $h(\tau)$ about $\tau=0$ to get $h(-\tau)$

- Shift: shift $h(-\tau)$ by $t$ to get $h(t-\tau)$

- Multiply: multiply $x(\tau)$ by $h(t-\tau)$ for every $\tau$

- Integrate: $y(t) = \int_{-\infty}^{\infty}x(\tau)h(t-\tau)d\tau$​



*If you don't understand, please refer to this video (from 32:40):* 

https://www.bilibili.com/video/BV1SB4y1C7yx?p=4&vd_source=0be2819c805c6da41df6967754921b05



### Properties of Convolution

- $x(t) ∗ h(t) = h(t) ∗ x(t)$
- $[x(t) ∗ h_1(t)] ∗ h_2(t) = x(t) ∗ [h_1(t) ∗ h_2(t)]$
- $x(t) ∗ δ(t) = x(t)$
- $x(t) ∗ δ(t - t_0) = x(t - t_0)$
- $δ(t - t0) ∗ δ(t - t1) = δ(t - t0 - t1)$
- $x(t - t0) ∗ h(t - t1) = y(t - t0 - t1)$​
- $\frac{d}{dt}y(t)=[\frac{d}{dt}x(t)]*h(t)=[\frac{d}{dt}h(t)]*x(t)$
- $\int_{-\infty}^{\infty}y(t)=[\int_{-\infty}^{\infty}x(t)dt][\int_{-\infty}^{\infty}h(t)dt]$
- $y(at)\neq x(at)*h(at)$

For properties which are not included, please **derive from integral form of convolution**! 



**Exercise: **

1. One of following two statements is correct, and the other is incorrect. 

   - If $y(t) = h(t)*x(t)$ then $y(t-3) = h(t-3) * x(t-3)$;
   - Or if $y(t) = h(t)*x(t)$ then $y(t-3) = h(t) * x(t-3)$​​.

   

2. Show that

$$
\frac{1}{a}rect(\frac{t}a)*rect(\frac{t}{a})=tri(\frac{t}{a})\quad\text{where }a>0
$$

Hint: $rect(t)*rect(t)=tri(t)$​













### LTI Systems properties via $h(t)$

1. **Causal**:

   An LTI System is causal iff its impulse response $h(t) = 0$ for all $t < 0$.  

2. **Memoryless:**

   An LTI System is memoryless iff its impulse response $h(t) = a\delta(t)$.  

   Otherwise, the system is **dynamic**.

   (Note: A finite impulse response or FIR system means $h(t)\neq 0, t_1<t<t_2$. )

3. **BIBO stable**:

   An LTI system is BIBO stable iff its impulse response is absolutely integrable, i.e. $\int_{-\infty}^{\infty}|h(t)|dt < \infty$.

4. **Invertible**:

   An LTI system is invertible iff there exist an inverse system whose impulse response $h_i(t)$ satisfies 
   $$
   h(t) ∗ h_i(t) = δ(t)
   $$
   

**Exercise:**

1. Determine whether the system is causal, stable and static via $h(t)$.
   $$
   y(t) = \int_{-\infty}^{t}(t-\tau)e^{-(t-\tau)}x(\tau)d\tau
   $$
   













### Step Response

Step response of an LTI system is defined as the response of the system to an input signal $s(t)$​ that is unit step.
$$
\delta(t)\xrightarrow{\tau}h(t)\\
u(t)\xrightarrow{\tau}s(t)=\int_{-\infty}^{\infty}u(t-\tau)h(\tau)d\tau\\
s(t)=u(t)*h(t)=\int_{-\infty}^{t}h(\tau)d\tau\\
h(t)=\frac{d}{dt}s(t)
$$



### CT systems described by differential equation models

Linear constant-coefficient differential equation:
$$
\sum_{k=0}^Na_k\frac{d^k}{dt^k}y(t)=\sum_{k=0}^Nb_k\frac{d^k}{dt^k}x(t)
$$
Approach:
$$
y(t)=y_h(t)+y_p(t)
$$
$y_h(t)$: homogeneous solution, or zero-input response, or natural response.

$y_p(t)$: particular solution, or zero-state response, or forced response.

### Initial rest condition

Initial rest states that if $x(t)=0$ for $t<t_0$, then $y(t)=0$ for $t<t_0$.

It means that the output must be zero up until the time when the input becomes zero. 

Causal and LTI system ⇔ initial rest

**Exercise: **

1. Find the expression of response of the CT system described by the linear constant-coefficient differential equation.
   $$
   \frac{d}{dt}y(t)+10y(t)=2x(t), \qquad y(0)=1, \qquad x(t) = u(t)
   $$















**Summary - How to find step response or impulse response of diffeq systems? **

1. Find general solution $y_h(t)$
2. Set $x(t)=u(t)$, find particular solution $y_p(t)$
3. Solve all the constants according to initial rest condition.
4. $s(t)$ determined, solve impulse response (if required) according to  $h(t)=\frac{d}{dt}s(t)$. Remember to add $u(t)$ according to initial rest. 



### Convolution of Common Signals

***Copy them on your CTPP! Copy them on your CTPP!***

- $k*f(t)=k\int_{-\infty}^{\infty}f(t)dt=k\times$(area of $f(t)$​ over R)
- $f(t)*u(t) = \int_{-\infty}^tf(t)dt$
- $u(t)*u(t)=tu(t)$​
- $u(t)*e^{-at}u(t)=\frac{1}{a}(1-e^{-at})u(t)$
- $e^{-at}u(t)*e^{-at}u(t)=te^{-at}u(t)$
- $e^{-a_1t}u(t)*e^{-a_2t}u(t)=\frac{e^{-a_1t}-e^{-a_2t}}{a_2-a_1}u(t)$

- $f(t)*\sum_{m=-\infty}^{\infty}\delta(t-mT)=\sum_{m=-\infty}^{\infty}f(t-mT)$​\

- $\frac{1}{a}rect(\frac{t}{a})*rect(\frac{t}{a})=tri(\frac{t}{a})$

- $\frac{1}{a}rect(\frac{t-t_0}{a})*rect(\frac{t-t_1}{a})=tri(\frac{t-t_0-t_1}{a})$

***Be familiar with all of them, deduce them by yourself and use them in the exam!***



## Exercises

1. Compute the following convolution: 
   $$
   u(t) * t^2u(t)
   $$
   









2. Consider an LTl system whose response to the signal $x_1(t)$ is the signal $y_1(t)$​ which are illustrated below.
   (a) Determine the response of the system to the input $x_2(t)$ depicted below.
   (b) Determine the response of the system to the input $x_3(t)$ depicted below.

<img src="C:\Users\86151\AppData\Roaming\Typora\typora-user-images\image-20240310115735592.png" alt="image-20240310115735592" style="zoom:50%;" />





## Notes

**Before the exam: **

1. **Review all the quizzes! **
1. Review homework answers.
1. Gain proficiency in convolution calculation.
1. Check whether all the contents on summary sheet have been on your ctpp. 

**During the exam: **

1. If algebra doesn’t work, go for graphics.  
1. Use convolution of common signals if possible. 
1. If you use method of substitution, pay attention when substituting the range of integral. 



## Reference

1. Yuan Jiaming. *VE216 Mid 1 RC part 2.* 
2. Long Yong. *VE216 slides.* 
