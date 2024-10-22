# Chapter 2 - Convolution

[toc]

## Linear and Time-Invariant (LTI) Systems

### What is LTI Property? 

**Linearity**:

For a linear system, if $x_1(t) \xrightarrow{\tau} y_1(t)$ and $x_2(t) \xrightarrow{\tau} y_2(t)$, then $ax_1(t) + bx_2(t) \xrightarrow{\tau} y_1(t)+by_2(t)$.

**Time-Invariance**:

For a time-invariant system, if $x(t) \xrightarrow{\tau} y(t)$, then $x(t-t_0) \xrightarrow{\tau} y(t-t_0)$​.

**Graphical Understanding of LTI Property: **













### Why LTI Property Matters?

LTI property **simplify** the analysis of a system. Specifically, it makes the system design and response analysis easier. To design an LTI system, we only need to care about its impulse response $h(t)$, since an LTI system is **completely described** by its impulse response $h(t)$.

In this chapter, we cares how to analyze LTI system using **convolution** methods.


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
**Concept Question: **

1. **Why we can decompose $x(t)$​ into delayed impulses? **

   - Hint: Start from discrete case $x[n]$ to understand the idea,  and build an approximation by short time impulses ($\Delta \rightarrow 0$)

     

2. **How to derive the convolution integral using LTI property?** 

   - Hint 1: $x(\tau)$​ is a constant so that we can use linearity property. 

   - Hint 2: $\delta(t-k) \xrightarrow{\tau} h_k(t)$, since the system is TI, $\delta(t-k) \xrightarrow{\tau} h(t-k)$



### Why Convolution? 

An LTI system is completely described by its impulse response $h(t)$​. 

Any system whose input-output relationship can be expressed in $y(t)=\int_{-\infty}^{\infty}x(\tau)h(t-\tau)d\tau = x(t)*h(t)$​​ is time-invariant. 



**Pratical Question:**

1. Known the representation of a LTI system, $y(t)=F(x(t))$, how to solve $h(t)$? 

   - By definition: 

     $h(t)$ is the output signal when input signal $x(t)$ is $\delta(t)$​.

     $h(t)=F(\delta(t))$

   - By convolution:

     $y(t)=h(t)*x(t)=F(x(t))$

     solve $h(t)$ by transforming the $F(x(t))$ to convolution form

​	**You should handle both! **



**Exercise: **

1. Find the impulse response of the LTI systems. 
   $$
   y(t) = \int_{-3}^{3}\tau^2x(t-\tau)d\tau + \int_{-\infty}^{t+1}(t-\tau+3)^{-2}x(\tau)d\tau
   $$













**Summary**: How to get turn $y(t)$ to $h(t)*x(t)$​?

1. Use $u(t)$ to represent range of integration
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

**If you do not have 100% confidence, use algebra methods than graphical methods in the exam, since algebra methods enable you to gain more partial points. **



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

For properties which are not included, please derive from integral form! 

More in https://zhuanlan.zhihu.com/p/150737244

### LTI Systems properties via $h(t)$

1. **Casual**:

   An LTI System is casual iff its impulse response $h(t) = 0$ for all $t < 0$.  

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

**Tips: **

**Solving differential equation in the time domain is NOT covered in the Mid1 !!!!! **

**Also, it is not the focus of VG216. The course emphasizes more on solving differential equations on the frequency domain, which will be covered in Chapter 3&9**



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



### Convolution of Common Signals

***Copy them on your CTPP! Copy them on your CTPP! Copy them on your CTPP!***

- $k*f(t)=k\int_{-\infty}^{\infty}f(t)dt=k\times$(area of $f(t)$​ over R)
- $f(t)*u(t) = \int_{-\infty}^tf(t)dt$
- $u(t)*u(t)=tu(t)$​
- $u(t)*e^{-at}u(t)=\frac{1}{a}(1-e^{-at})u(t)$
- $e^{-at}u(t)*e^{-at}u(t)=te^{-at}u(t)$
- $e^{-a_1t}u(t)*e^{-a_2t}u(t)=\frac{e^{-a_1t}-e^{-a_2t}}{a_2-a_1}u(t)$

- $f(t)*\sum_{m=-\infty}^{\infty}\delta(t-mT)=\sum_{m=-\infty}^{\infty}f(t-mT)$​\

- $\frac{1}{a}rect(\frac{t}{a})*rect(\frac{t}{a})=tri(\frac{t}{a})$

- $\frac{1}{a}rect(\frac{t-t_0}{a})*rect(\frac{t-t_1}{a})=tri(\frac{t-t_0-t_1}{a})$

***Be familiar with all of them, and derive them by yourself once.***

***You can use them directly in your exam!***



**Useful Tips: **

1. **Write all the $Arect(at)$ signal to the form of $Au(t-t_1)-Au(t-t_0)$ first when calculating the convolution of signals.** 

2. If you can find the common convolution results, use them directly in the exam.

**Let's Practice! **

1. Find the response of the input $x(t) = u(t)$, when $h(t) =e^{-at}u(t)$

   Method 1: Using convolution definition

   Method 2: Using the results above

   <img src="C:\Users\86151\AppData\Roaming\Typora\typora-user-images\image-20240603123046040.png" alt="image-20240603123046040" style="zoom: 33%;" />

   ***Take care of the range of integral and use the results above in the exam if possible.***

2. 



















## Tips

**If you found it's really hard to understand some chapters of this course, you can: **

1. Go to corresponding chapter of MIT open course: https://www.bilibili.com/video/BV1SB4y1C7yx/?spm_id_from=333.999.0.0&vd_source=0be2819c805c6da41df6967754921b05

2. Read the slides/textbook page by page

**Before the exam: **

1. **Review all the quizzes! **
1. Review homework answers.
1. Gain proficiency in convolution calculation.
1. Check whether all the contents on summary sheet have been on your ctpp. 

**During the exam: **

1. Use convolution of common signals if possible. 
1. Pay attention to the range of integral. 
1. For the problem with a "!", it means that only zero points or full points. Take care of them! 



## Reference

1. Yuan Jiaming. *VE216 Mid 1 RC part 2.* 
2. Long Yong. *VE216 slides.* 
