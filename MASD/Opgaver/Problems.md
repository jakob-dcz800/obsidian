# [[Integration by substitution]]
## 1
$$
\int 3x^2e^{x^3}dx
$$
Identify g:
$$
\begin{align}
g & =x^3 \\
g' & =3x^2
\end{align}
$$
[[Integration|Integrate]] expression with u:
$$
\begin{align}
\int e^udu = e^u+C
\end{align}
$$
Substitute back:
$$
e^u + C=e^{x^3}+C
$$
## 2

$$
\int \frac{2x}{x^2+1}dx
$$
$$
\begin{align}
g & =x^2 +1\\
g' & =2x
\end{align}
$$
Insert u:
$$
\int \frac{1}{u} du
= \ln(u) + C
$$
Substitute:
$$
\ln(u)+C=\ln(x^2+1)+C
$$
## 3

$$
\int x \sqrt{ x^2+4 }dx =\int x(x^2+4)^{1/2}dx
$$
$$
\begin{align}
u & =x^2+4 \\
du & =2xdx \implies xdx=\frac{1}{2}du
\end{align}
$$
Insert u
$$
\int x \sqrt{ x^2+4 }dx =
\int(xdx)\sqrt{ u } =
\int\frac{1}{2}u^{1/2}du
$$
Substitute and integrate:
$$
\frac{1}{2} \int u^{1/2}du=
\frac{1}{2} \cdot \frac{2}{3}u^{3/2}=
\frac{2}{3}u^3+C
$$
$$
\underline{
\frac{2}{3}(x^2+4)^{3/2}
}
$$
## 4

$$
\int x^3 \sqrt{ x^4+1 }dx= \int x^3(x^4+1)^{1/2}
$$
$$
u=x^4+1
$$
$$
du=4x^3dx \implies \frac{1}{4}du=x^3dx
$$
$$
\frac{1}{4} \int u^{1/2} = \frac{1}{4} \cdot \frac{2}{3} u^{3/2}
= \frac{2}{12}u^{3/2}=\frac{1}{6}(x^4+1)^{3/2}
$$
## 5

$$
\int \frac{x}{\sqrt{ x^2+9 }}dx = 
\int x\cdot \frac{1}{\sqrt{ x^2+9 }}dx
$$
$$
\begin{align}
u & = x^2+9 \\
du & = 2xdx \implies \frac{1}{2}du
\end{align}
$$
$$
\frac{1}{2} \int x \cdot \frac{1}{\sqrt{  x^2+9 }} =
\frac{1}{2} \int \frac{1}{\sqrt{ u }}=
\frac{1}{2} \int u^{-1/2}du
$$
$$
\frac{1}{2} \int u^{-1/2}du= 
\frac{1}{2} \cdot \frac{1}{-\frac{1}{2}+1}u^{1/2}+C
=u^{1/2}+C
$$
Insert u
$$
u^{1/2}+C = (x^2+9)^{1/2}
$$
## 6

$$
\int \frac{dx}{\sqrt{ a^2-x^2 }}
$$
Since this is a standard inverse trig function, we can express:
$$
\int \frac{1}{\sqrt{ a^2-u^2 }} du = \sin^{-1}(\frac{u}{a})+c
$$
Therefore with g:
$$
\int \frac{1}{\sqrt{ a^2-(a \sin \theta)^2 }}dx
= \sin^{-1} \left( \frac{a\sin \theta}{a} \right) + c
= \sin^{-1} (\sin \theta)+c=c
$$

# [[Integration by parts]]

## 1

$$
\int xe^x dx
$$
We define our functions v, and u:
$$
\begin{align}
u & = x \\
dv & = e^x dx
\end{align}
$$
Differentiate $u$:
$$
\begin{align}
u' & = 1
\end{align}
$$
Integrate $dv$:
$$
v=\int v dx=\int e^x dx=e^x
$$
Put it all together and **Do not** carry the arbitrary constant +C inside intermediate antiderivatives. That constant is added once at the end:
$$
\int udv=uv-\int vdu
= u\int vdx -\int u'\left( \int v dx \right)dx
$$
$$
xe^x-\int e^xdx=xe^x-e^x+C
$$
Factor:
$$
e^x(x-1)+C
$$
## 2

$$
\int e^xx^2dx
$$
$$
\begin{align}
u & = e^x \\
dv & = x^2
\end{align}
$$
$$
u'=e^x
$$
### Integral of v using parts
$$
v=\int x^2dx= \int x\cdot xdx
$$
$$
u = x
, \text{ } dv =x
$$
$$
u'=1
$$
$$
d=\int xdx = \frac{1}{2}x^2
$$
$$
uv-\int vdu=x\left( \frac{1}{2}x^2 \right)-\left( \frac{1}{2}x^2 \right)
$$
# Extrema

## 1
$$
f(x, y) =
x^2+y^2-4x-6y+13
$$
$$
\begin{align}
f_{x} & = 2x-4 \\
f_{y} & = 2y-6
\end{align}
$$
This can be written as a system of equations.
$$
\left[
\begin{array}{cc|c}
2 & 0 & 4 \\
0 & 2 & 6
\end{array}
\right]
\to
\left[
\begin{array}{cc|c}
1 & 0 & 2 \\
0 & 1 & 3
\end{array}
\right]
$$
We get the result $(2, 3)$ as a critical point.
Lets check the point using a hessian matrix.

$$
H =
\begin{bmatrix}
f_{xx} & f_{xy} \\
f_{yx} & f_{yy}
\end{bmatrix}
$$
$$
\begin{align}
f_{xx} & = 2 \\
f_{xy} & = 0 \\
f_{yx} & = 0 \\
f_{yy} & = 2
\end{align}
$$
Thus:
$$
H=
\begin{bmatrix}
2 & 0 \\
0 & 2
\end{bmatrix}
$$
$$
\text{det A} = (2\cdot2)-0=4
$$
What can we see from this?
### Step 1: Check the determinant of the Hessian

- $det⁡(H)>0$ → The critical point is either a **local minimum** or a **local maximum**
- If $det⁡(H)<0$, it would be a **saddle point**

### Step 2: Check the sign of f_{xx}

- $f_{xx}=2>0$ → This tells us the function is **concave up** in the xxx-direction.
- When $det⁡(H)>0$ and $f_{xx}>0$, the critical point is a **local minimum**.

**Conclusion:**  
The critical point $(2, 3)$ is a **local minimum**.
And because $f(x, y)$ is a quadratic function with **positive definite Hessian**, this is also the **global minimum**.

## 2

$$
f(x,y)=x^2+xy+y^2-6x-6y+14
$$
$$
f_x​=2x+y−6,f_y​=x+2y−6
$$
We solve f_x = 0 and f_y = 0
$$
\left[\begin{array}{cc|c}
2 & 1 & 6 \\
1 & 2 & 6
\end{array}\right]
\to
\left[\begin{array}{cc|c}
2 & 1 & 6 \\
0 & 3/2 & 3
\end{array}\right]
\to
\left[\begin{array}{cc|c}
2 & 0 & 2 \\
0 & 3/2 & 3
\end{array}\right]
\to
\left[\begin{array}{cc|c}
1 & 0 & 1 \\
0 & 1 & 2
\end{array}\right]
$$
We get the point (1, 2)
Let's get the hessian:
$$
H=
\begin{bmatrix}
f_{xx} & f_{xy} \\
f_{yx} & f_{yy}
\end{bmatrix}
=
\begin{bmatrix}
2 & 1 \\
2 & 1
\end{bmatrix}
$$
$$
\text{det H} = 2\cdot 1-1\cdot 2 = 0
$$
