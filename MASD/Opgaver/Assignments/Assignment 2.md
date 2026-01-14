
![[Regneregler#Afledte funktioner]]


## 2

![[Regneregler#Rødder og potenser]]
![[Regneregler#Parenteser]]


### 7
Let's try a 2x2 matrix and see that its result is a scalar:
$$
\text{A}\mathbf{x}=
\begin{bmatrix}
a_{11} & a_{12} \\
a_{21} & a_{22}
\end{bmatrix}
\begin{bmatrix}
x_{1} \\
x_{2}
\end{bmatrix}
=
\begin{bmatrix}
a_{11}x_{1}+a_{12}x_{1} \\
a_{21}x_{2}+a_{22}x_{2}
\end{bmatrix}
$$
$$
\mathbf{x}^{\mathbf{T}}\text{A} =
\begin{bmatrix}
x_{1}  & 
x_{2}
\end{bmatrix}
\begin{bmatrix}
a_{11} & a_{12} \\
a_{21} & a_{22}
\end{bmatrix}
=
\begin{bmatrix}
a_{11}x_{1}+a_{21}x_{2} & a_{12}x_{1}+a_{22}x_{2}
\end{bmatrix}
$$
We can express this generally:
$$
\mathbf{x^T A}=\left[ \sum^n_{j=1}(a_{1j}x_{j}) \dots \sum^n_{j=1}(a_{nj}x_{j}) \right]
$$
Let's try and insert this into our expression:
$$
\begin{align}
\mathbf{x}^{\mathbf{T}}\text{A}\mathbf{x}
 & =
\left[ \sum^2_{j=1}(a_{1j}x_{j}) + \sum^2_{j=1}(a_{2j}x_{j}) \right] \begin{bmatrix}
x_{1} \\
x_{2}
\end{bmatrix}\\
 
 & = \left[ x_{1}\left( \sum^2_{j=1}(a_{1j}x_{j}) \right) + x_{2}\left( \sum^2_{j=1}(a_{2j}x_{j}) \right) \right] 
\\ & =
\begin{bmatrix}
x_{1}(a_{11}x_{1}+a_{21}x_{2})+x_{2}(a_{12}x_{1}+a_{22}x_{2})
\end{bmatrix}
\end{align}
$$
We see that the value of $x_{i}$ and the row number is incrementing by 1 for each term. We can therefore express it even further as a sum:
$$
\mathbf{x}^{\mathbf{T}}\text{A}\mathbf{x} =
\sum_{i=1}^{n}x_{i}\left(\sum^n_{j=1}(a_{ij}x_{j})\right)
$$
We express the partial derivative with respect to $x_{i}$ as
$$
\begin{align}
\frac{\partial}{\partial x_{i}} 
\left( \sum_{i=1}^{n}x_{i}\left(\sum^n_{j=1}(a_{ij}x_{j})\right) \right) & =
 \sum_{i=1}^{n}\frac{\partial}{\partial x_{i}}\left( x_{i}\sum^n_{j=1}(a_{ij}x_{j})\right)
\end{align}
$$
Here, we utilize the fact that $\frac{d}{dx}(f(x)\pm g(x))=f'(x)\pm g'(x)$, and move $\frac{\partial}{\partial x_{i}}$ within the summation symbol.

### 6
$$
e^{(x^2+y^2-x)^3}
$$
We utilize the chain rule and split the function up:
$$
\begin{align}
g(x) & = e^{h(x)}\\
h(x) & = (x^2+y^2-x)^3
\end{align}
$$
To derive h, we use the chain rule once more, and split the function into u and v where
$$
\begin{align}
u & = v^3 \\
v & = x^2+y^2-x
\end{align}
$$
We derive them:
$$
\begin{align}
v' & = 3v^2 \\
u' & = 2x-1
\end{align}
$$
and use them to express h':
$$
\begin{align}
h'(x) & = 3(x^2+y^2-x)^2 \cdot (2x-1) \\
g'(x) & = e^{h(x)}
\end{align}
$$

Thus we can express f:
$$
\begin{align}
\frac{\partial }{\partial x} \left(e^{(x^2+y^2-x)^3}\right) & =
e^{(x^2+y^2-x)^3}\cdot 3(x^2+y^2-x)^2\cdot (2x-1)
\end{align}
$$
### 5

$$
\begin{align}
\frac{d^2}{dx^2}\left(\frac{\ln(1+e^{qx})}{q}\right)  & = \frac{d}{dx}(f'(x)) \\
&  = \frac{d}{dx}\left( \frac{qe^{qx}}{1+e^{qx}} \right)
\end{align}
$$
We again use the quotient rule and split the function into g and h:
$$
\begin{align}
g(x) & = qe^{qx} \\
h(x) & = 1+e^{qx}
\end{align}
$$
We derive them:
$$
\begin{align}
g'(x) & = q^2e^{qx} \\
h'(x) & = qe^{qx}
\end{align}
$$
We insert into the quotient rule expression:
$$
\begin{align}
\frac{d}{dx}\left( \frac{qe^{qx}}{1+e^{qx}} \right) & =
\frac{q^2e^{qx}(1+e^{qx})-qe^{qx}(qe^{qx})}{(1+e^{qx})^2} \\
 & = \frac{q^2e^{qx}(1+e^{qx})-qe^{2qx}}{e^{2qx} + 2e^{qx} + 1} \\
 & = \frac{q^2e^{qx}+q^2e^{2qx}-qe^{2qx}}{e^{2qx} + 2e^{qx} + 1}
\end{align}
$$
### 4
$$
f(x)=\frac{\ln(1+e^{qx})}{q}
$$
Here, we assume $q$ is a constant. Therefore we can express the function as:
$$
f(x)=\frac{1}{q}\ln(1+e^{qx})
$$
We can utilize the chain rule:
$$
\begin{align}
g(x) & = \frac{1}{q}\ln(u) & \text{where } u=h(x) \\
h(x) & = 1+e^{qx}
\end{align}
$$
We derive g and h:
$$
\begin{align}
g'(x) & = \frac{1}{u} \\
h'(x) & =qe^{qx}
\end{align}
$$
We insert into the chain rule:
$$
\begin{align}
f'(x) & = \frac{1}{1+e^{qx}}\cdot qe^{qx} \\
 & = \frac{qe^{qx}}{1+e^{qx}}
\end{align}
$$
### 3

$f(x)=\frac{\ln x}{x^4}$
We utilize the Quotient Rule and split our function into g and h.

$$
\begin{align}
g(x) & = \ln x \\
h(x) & = x^4
\end{align}
$$
We derive them:
$$
\begin{align}
g'(x) & = \frac{1}{x}=x^{-1} \\
h'(x) & = 4x^3
\end{align}
$$
We insert into the quotient rule
$$
\begin{align}
f'(x) & = \frac{x^{-1}x^4-\ln (x)4x^3}{(x^4)^2} \\
 & = \frac{x^3-4x^3\ln(x)}{x^8} \\
 & = \frac{x^3(1-4\ln(x))}{x^8} \\
 & = \frac{1-4\ln(x)}{x^5}
\end{align}
$$
### 2

$$
f(x)= \sin(x)e^{-\cos(x)^2}
$$
We use the product rule and split the function up:
$$
\begin{align}
h(x) & = \sin(x) \\
g(x) & = e^{-\cos(x)^2}
\end{align}
$$
$$h'(x)=\cos x$$
To derive g, we must apply the chain rule where:
$$
\begin{align}
g(x) & =u^v \\
\text{where } \\
u & =e \\
v & =-\cos(x)^2
\end{align}
$$
$$
\begin{align}
g'(x) & =e^{-\cos(x)^2}\cdot(-(-2\cos(x)\cdot \sin(x))) \\
 & = e^{-\cos(x)^2}\cdot 2\cos(x)\cdot \sin(x)
\end{align}
$$
We insert g' into our derivative:
$$
\begin{align}
f'(x) & = h(x)'g(x)+h(x)g(x)' \\
 & = \cos(x)e^{-\cos(x)^2}+\sin(x)e^{-\cos(x)^2}\cdot 2\cos(x)\cdot \sin(x) \\
 & = \cos(x)e^{-\cos(x)^2}+\sin^2(x)e^{-\cos(x)^2}\cdot 2\cos(x) \\
 & = e^{-\cos(x)^2}(\cos (x)+\sin^2(x)\cdot 2\cos (x)) \\
 & = e^{-\cos(x)^2}\cos (x)(1+ 2\sin^2(x))
\end{align}
$$

### 1
$$
f(x)=\sqrt{ 2x^2+2x-4 }
$$
We calculate the derivative by using the chain rule. We split the function into to parts, g and h:
$$
\begin{align}
h(x) & = 2x^2+2x-4 \\
g(x) & =\sqrt{ u } \\
\text{ where } u  & = h(x)
\end{align}
$$
The derivatives are calculated individually:
$$
\begin{align}
h'(x) & = 4x+2  \\
g'(x) & =\frac{1}{2\sqrt{ u }}
\end{align}
$$
We apply the chain rule:
$$
\begin{align}
f'(x) & = \frac{1}{2\sqrt{ 2x^2+2x-4 }}\cdot 4x + 2 \\
 & = \frac{4x + 2}{2\sqrt{ 2x^2+2x-4 }} \\
 & = \frac{2x + 1}{\sqrt{ 2x^2+2x-4 }}
\end{align}
$$
## 3

$$
f_{1}(x)=-\frac{x}{2\sigma^2}e^{-\frac{x^2}{2\sigma^2}} \text{ with } \sigma =1
$$
$$
f_{2}(x) = 
1.45469 − 3.46032x − 0.272173x^2 + 0.186534x^3 − 0.0022172x^4 − 0.00156431x^5
$$
---
Derivatives:

$$
\begin{align}
 &  \frac{d}{dx}(1.45469 − 3.46032x − 0.272173x^2 + 0.186534x^3 − 0.0022172x^4 − 0.00156431x^5) \\
 &  = -3.46032-2(0.272173x)+3(0.186534x^2)-4(0.0022172x^3)-5(0.00156431x^4) \\
 & =-3.46032 - 0.544346x+0.559602x^2-0.0088688x^3-0.00782155x^4
\end{align}
$$

$$
\frac{d}{dx}(-\frac{x}{2\sigma^2}e^{-\frac{x^2}{2\sigma^2}}) \text{ with } \sigma=1
$$
$$
\frac{d}{dx}(-\frac{x}{2}e^{-\frac{x^2}{2}}) \\
$$
We utilize the product rule and split the function in two

$$
\begin{align}
h(x) & = -\frac{x}{2} \\
g(x) & = e^{-x^2/2}
\end{align}
$$
We differentiate both:
$$
\begin{align}
h'(x) & = -\frac{1}{2}
\end{align}
$$
We differentiate g using the chain rule
$$
\begin{align}
g'(x) & = e^{-x^2/2}\cdot (-x) \\
 & =-xe^{-x^2/2}
\end{align}
$$
We insert into product rule:
$$
\begin{align}
f'(x) & = h(x)'g(x)+h(x)g(x)' \\
 & = -\frac{1}{2}e^{-x^2/2}-\left( \frac{x}{2} \right)(-xe^{-x^2/2}) \\
 & = -\frac{1}{2}e^{-x^2/2}+\frac{x^2}{2}e^{-x^2/2} \\
 & = e^{-x^2/2}\left( -\frac{1}{2} + \frac{x^2}{2} \right) \\
 & = e^{-x^2/2}\left(\frac{x^2-1}{2} \right)
\end{align}
$$


## 3.2

We calculate $f_{1}''$:
We have $f_{1}'=e^{-x^2/2}\left(\frac{x^2-1}{2} \right)$
We split it up and use the product rule:

$$
\begin{align}
h'(x) & = e^{-x^2/2} \\
g'(x) & = \frac{x^2-1}{2}
\end{align}
$$
We use the chain rule for g':
$$
\begin{align}
h''(x) & =-xe^{-x^2/2} \\
g''(x) & = x
\end{align}
$$
Thus:
$$
\begin{align}
f_{1}''(x) & = h''(x)g'(x)+h'(x)g''(x) \\
 & = (-xe^{-x^2/2}) \frac{x^2-1}{2}+e^{-x^2/2}(x) \\
 & = e^{-x^2/2}\left( -\frac{x(x^2-1)}{2}+x \right) \\
 & = e^{-x^2/2}\left( -\frac{x^3-x}{2}+x \right) \\
 & = e^{-x^2/2}\left( \frac{-x^3+3x}{2}\right)
\end{align}
$$
We calculate $f_{2}''$
We have $f_{2}'(x)=-3.46032 - 0.544346x+0.559602x^2-0.0088688x^3-0.00782155x^4$
$$
\begin{align}
 &  \frac{d}{dx}(-3.46032 - 0.544346x+0.559602x^2-0.0088688x^3-0.00782155x^4) \\
 & = - 0.544346 + 1.119204x - 0.0255064x^2 - 0.0312862x^3 \\
\end{align}
$$

