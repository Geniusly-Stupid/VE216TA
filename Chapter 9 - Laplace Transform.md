# Chapter 9 - Laplace Transform

[toc]

## Laplace Transform

The Laplace Transform (LT) is the **generalization** of the Fourier Transform to include general complex exponential signals of the form
$$
e^{st}=e^{(\sigma+j\omega)t}=e^{\sigma t}e^{j\omega t}
$$
We can generalize because $e^{st}$ also follows:
$$
e^{st} \xrightarrow{\tau} H(s)e^{st}=e^{st}\int_{-\infty}^{\infty}h(\tau)e^{-s\tau}d\tau
$$
Laplace Transforms come in two flavors:

- Bilateral Laplace Transform (two-sided)
- Unilateral Laplace Transform (one-sided)

In this course, we only concern **Bilateral Laplace Transform**.

## Bilateral Laplace Transform

Bilateral Laplace Transform means that the integral starts from negative infinity to positive infinity. 

The formula is 
$$
X(s)=\int^{\infty}_{-\infty}x(t)e^{-st}dt\\
x(t)=\frac{1}{2\pi j}\int^{\sigma+j\infty}_{\sigma-j\infty}X(s)e^{st}ds\\
s=\sigma+j\omega
$$
LT pairs can be denoted as:
$$
x(t)\leftrightarrow X(s)
$$

### Relation between Laplace Transform & Fourier Transform

We can derive the following relationship:
$$
X(s)|_{s=j\omega}=\mathcal{F}\{x(t)\}\\
$$

$$
X(s)=\mathcal{F}\{x(t)e^{-\sigma t}\},  \text{where }s=\sigma+j\omega
$$

These two relationships can help you understand the properties below. 

## Region of Convergence (ROC)

### Concept

ROC is **the set of values of s** on the complex plane for which the **bilateral Laplace transform is guaranteed to exist/converge**. That is, 
$$
ROC=\{s\in C:\int^{\infty}_{-\infty}|x(t)|e^{-real\{s\}t}dt< \infty \}
$$
To define a Laplace Transform, you **have to** specify its **ROC**! 


### Display

Often we display the ROC of a signal using the **complex s-plane** as shown in the following ﬁgures.

<img src="C:\Users\86151\AppData\Roaming\Typora\typora-user-images\image-20240417212112121.png" alt="image-20240417212112121" style="zoom: 67%;" />

- The horizontal axis is called $\sigma$ axis, and the vertical axis is called $j\omega$ axis.
- The shaded region indicates ROC.
- Dotted lines is used to indicate boundaries if ROC doesn’t include its edges.
- **If the shaded region includes the $j\omega$ axis, then the FT of the signal exists.**



### Rational Laplace Transform

If the Laplace transform of a signal $x(t)$, $X(s)$, has the form:

$$
X(s) = \frac{N(s)}{D(s)} = \frac{\sum_{m=0}^{M} b_m s^m}{\sum_{n=0}^{N} a_n s^n} = G \frac{\prod_{k=1}^{M} (s - z_k)}{\prod_{k=1}^{N} (s - p_k)}
$$

- **Zeros**: \($z_1$,$z_2$, $\ldots$, $z_M$), sometimes infinity
- **Poles**: ( $p_1$, $p_2$, $\ldots$, $p_N$\), sometimes infinity
- **Gain**: G = $\frac{b_M}{a_N}$

#### Pole-zero plot

Using ’o’ to represent zeros, using ’X’ to represent poles

<img src="C:\Users\86151\AppData\Roaming\Typora\typora-user-images\image-20240417215026895.png" alt="image-20240417215026895" style="zoom:50%;" />



### Property of ROC

- The ROC of $X(s)$ consists of **stripe-shaped** regions parallel to the $j\omega$ axis in the s plane.
- The ROC of rational LT does not contain any poles.
- If $x(t)$ has a ﬁnite duration and is absolutely integrable, the ROC is the whole s plane.
- If $x(t)$ is **right sided** (remaining zeros when $t < t_0$), and if the line $Re\{s\} = \sigma_0$ is in the ROC, then all values of $s$ whose $Re\{s\} > \sigma_0$ will also be in the ROC.
- If $x(t)$ is **left sided**, and if the line $Re\{s\} = \sigma_0$ is in the ROC, then all values of s whose $Re\{s\} < \sigma_0$ will also be in the ROC.
- If $x(t)$ is **two sided**, and if the line $Re\{s\} = \sigma_0$ is in the ROC, then the ROC is composed of a stripe-shaped region including the line $Re\{s\} = \sigma_0$ on the s plane.
- If $X(s)$ is rational, its ROC is constrained by the poles or extents to inﬁnity.
- If $X(s)$ is rational, and if $x(t)$​ is right sided, the ROC is on the right of the rightest pole. 
- If $X(s)$ is rational and left sided, its ROC is on the left of the leftest pole.

**Explanation: **

https://www.bilibili.com/video/BV1SB4y1C7yx?p=20&vd_source=0be2819c805c6da41df6967754921b05



### ROC and System Properties

The Laplace transform $H(s)$ of a system’s impulse response $h(t)$ is called its system function.

- Stability ⇔ $j\omega$ axis in ROC ⇔ $h(t)$ absolutely integrable
- Causality ⇔ $h(t)$ is a right-sided signal ⇔ ROC of the system function H(s) is RHP
- Stability and Causality ⇔ All of its poles lie strictly within the LHP.
- ***CAUTION***: Consider poles at ±$\infty$! e.g. $H(s) = s$ has a pole at s = $\infty$.
- All improper systems are unstable!
- **A diffeq system is stable** iff all roots of its characteristic polynomial are in the left half plane.



### Geometric Properties of FT from pole-zero plot

Given the pole-zero plot corresponding to the transfer function $H(s)$  of an LTI system, we can sketch the magnitude response $|H(\omega)|$  and phase response $\angle H(\omega)$:

$$
H(\omega) = G \frac{(j\omega - z_1) \cdot \ldots \cdot (j\omega - z_m)}{(j\omega - p_1) \cdot \ldots \cdot (j\omega - p_n)}
$$
Magnitude response:

$$
|H(\omega)| = G \frac{|j\omega - z_1| \cdot \ldots \cdot |j\omega - z_m|}{|j\omega - p_1| \cdot \ldots \cdot |j\omega - p_n|}
$$
Phase response:

$$
\angle H(\omega) = \angle G + \angle(j\omega - z_1) + \ldots + \angle(j\omega - z_m) - \angle(j\omega - p_1) - \ldots - \angle(j\omega - p_n)
$$



## Common Laplace Transform & Inverse Laplace Transform

### Common Laplace Transform

![image-20240417213151277](C:\Users\86151\AppData\Roaming\Typora\typora-user-images\image-20240417213151277.png)

### Property of Laplace Transform

![image-20240417213220505](C:\Users\86151\AppData\Roaming\Typora\typora-user-images\image-20240417213220505.png)

### Inverse Laplace Transform

**Requirement**: Given rational $X(s)$ and **ROC**, we are required to invert it to ﬁnd signal $x(t)$.

**Steps**:

- Decompose $X(s)$ into **the sum of atomic expressions** by doing **PFE**.

- For each expression, ﬁnd ROC. Select the one including the ROC of LT.

- For each expression, use LT table and LT properties to get the result. Then sum them up.

- ***CAUTION***: If the ROC is not given explicitly, discuss all the situations!!! 

There are cases that given the pole-zero plot and DC value, and ask you to ﬁnd x(t). In this case, you need to ﬁnd the gain G with certain points.



#### Exercise

The system function of a causal LTI system is

$$
H(s) = \frac{s + 1}{s^2 + 2s + 2}
$$
Determine and sketch the response \( y(t) \) when the input is

$$
e^{-|t|}, \quad -\infty < t < \infty
$$
*Hint:* You can use $e^{-|t|}=e^{-t}u(t)+e^{t}u(-t)$



**Answer:**

![image-20240417224503529](C:\Users\86151\AppData\Roaming\Typora\typora-user-images\image-20240417224503529.png)





## Differential Equation

### How to solve

Solve **algebraic expression** by Linear Constant Coefficient Differential Equation.

Solve **ROC** by stability & causality & etc. conditions.



## Block Diagram

In this part, you should be capable of:

1. Writing $H(s)$ according to the block diagram. Then analyze the system with $H(s)$. e.g. How to solve the  Impulse Response $h(t)$? etc. 
2. Draw the block diagram according to $H(s)$.

### Parallel Interconnection

<img src="C:\Users\86151\AppData\Roaming\Typora\typora-user-images\image-20240417234515336.png" alt="image-20240417234515336" style="zoom: 33%;" />



### Series Interconnection

<img src="C:\Users\86151\AppData\Roaming\Typora\typora-user-images\image-20240417234539622.png" alt="image-20240417234539622" style="zoom: 33%;" />

### Feedback Interconnection

<img src="C:\Users\86151\AppData\Roaming\Typora\typora-user-images\image-20240417235123326.png" alt="image-20240417235123326" style="zoom: 33%;" />

**If you are not sure whether you can write the $H(s)$ according to the block diagram, take the above as an example and practice. **



#### Exercise

**Exercise 1**

Draw the block diagram of the causal LTI system with system function:
$$
H(s)=\frac{1}{s+3}
$$

1. Use differentiator to implement. Mention, the differentiator is both difﬁcult to implement and extremely sensitive to noise.
	

**Answer: **

<img src="C:\Users\86151\AppData\Roaming\Typora\typora-user-images\image-20240418134909339.png" alt="image-20240418134909339" style="zoom:50%;" />
	
2. Use integrator to implement. 

**Answer:**

<img src="C:\Users\86151\AppData\Roaming\Typora\typora-user-images\image-20240418135020434.png" alt="image-20240418135020434" style="zoom:50%;" />



**For normal cases, please use integrator ($\frac{1}{s} $) to draw the diagram **

**Exercise 2: **

Draw the block diagram for the causal LTI system with system function:
$$
H(s)=\frac{1}{(s+1)(s+2)}
$$
Use **Direct Form**, **Cascade Form**, and **Parallel From**

**Answer: **

1. Direct Form









2. Cascade Form









3. Parallel From











### General block diagram for rational systems

<img src="C:\Users\86151\AppData\Roaming\Typora\typora-user-images\image-20240418133449989.png" alt="image-20240418133449989" style="zoom:50%;" />

- $m = n$: Just apply the method.

- $m < n$: e.g. $H(s) = \frac{1}{s^2+3s+2}$, we just ﬁrst ﬁll all the item in the upper to make the upper and lower part are at the same order. Finally **remove the branch** with zero coeﬃcient.

- $m > n$: e.g. $H(s) = s$. It has poles at $s = \infty$, which makes the system improper (All rational but improper systems are unstable!!), thus **won’t appear in real cases**.

## Exercise

**Exercise 1: **

Suppose we are given the following information about a causal and stable LTI system S with impulse response $h(t)$ and a rational system function $H(s)$:

(1) When the input to the system is $x(t) = e^{−3t}$ for all t, the output is $y(t) = −e^{−3t}$ for all t.

(2) When the input is $u(t)$, the output is absolutely integrable.

(3) When the input is $tu(t)$, the output is not absolutely integrable.

(4) The signal $\frac{d^2}{dt^2}h(t)+4\frac{d}{dt}h(t)+1h(t)$ is of ﬁnite duration.

(5) $H(s)$ has exactly one zero at inﬁnity. 

Determine $H(s)$ and its region of convergence.



































**How to solve problem**: Given several information of $x(t)$ and $y(t)$, find $H(s)$​

**Steps: **

1. eigenfunction $e^{kt}$

   $x(t) = e^{kt}$, then $y(t)=H(k)e^{kt}$

2. for certain $x(t)$, $y(t)$ is absolutely integrable/ or not. 

   1. absolutely integrable => ROC contains $j\omega$ axis
   2. not absolutely integrable => ROC doesn't contain $j\omega$ axis

3. $y(t)$​ is of finite duration

   => ROC is the whole plane

   => no poles exist for $Y(s)$

4. $H(s)$ has one zero at infinity

   => $n-m=1$, where $n$ is the degree of denominator

5. $H(s)$ has one pole at infinity

   => $m-n=1$, where $n$ is the degree of denominator



**Exercise 2: **

Suppose that the signal
$$
y(t) = e^{-2t}u(t)
$$
is the output of a causal system with the system function
$$
H(s)=\frac{s-1}{s+1}
$$

1. Find and plot two possible input $x(t)$ for the output $y(t)$​.
2. If there exists a stable (but not necessarily causal) system, if it takes $y(t)$ as the input, its output will be $x(t)$. Which $x(t)$​ is it? Find the impulse response of the system, and prove by directly calculate convolution.

































## Notes

**Before the exam: **

1. **Review all the quizzes! **
1. Review homework answers.
1. Gain proficiency in calculation (PFE, Common Laplace Transform, differential equation, etc. ).
1. Check whether all the contents on summary sheet have been on your ctpp. 

**During the exam: **

1. For solving differential equation problem, consider Laplace Transform first. Do NOT use time domain methods to solve it!  
1. Always judge and specify the ROC.



## Reference

1. Hu fan. 216 final recitation class. 
2. Long yong. 216 slides. 
