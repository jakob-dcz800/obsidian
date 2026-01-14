# 2

### i

First step must be finding the planes of $f$ and $g$ given by thm. 12.6. [Notes_for_MASD.pdf] The plane and affine approximation of $z = f(x_0, y_0)$ is given by
$$
p(x_0, y_0) = f(x_0, y_0) + f_x(x_0, y_0)(x - x_0) + f_y(x_0, y_0)(y - y_0)
$$
Thus we can write the affine approximation of $f$ and $g$ as:
$$
\begin{align*}
    z = f(x_0, y_0) + f_x(x_0, y_0)(x - x_0) + f_y(x_0, y_0)(y - y_0) \\
    z = g(x_0, y_0) + g_x(x_0, y_0)(x - x_0) + g_y(x_0, y_0)(y - y_0)
\end{align*}
$$
This plane as contact of first order with the given function in the point $(x_0, y_0, f(x_0, y_0))$. We can thus denote the plane of

$$
\begin{cases}
f(x_{0}, y_{0})+f_{x}(x_{0},yx)(x-x_{0}) + f_{y}(x_{0},y_{0})(y-y_{0}) & =  & 0 \\
g(x_{0}, y_{0})+g_{x}(x_{0},yx)(x-x_{0}) + g_{y}(x_{0},y_{0})(y-y_{0}) & = & 0
\end{cases}
$$
We can express $(x-x_{0})$ and $(y-y_{0})$ as $\Delta x, \Delta y$

$$
\begin{cases}
f(x_{0}, y_{0})+f_{x}(x_{0},yx)(\Delta x) + f_{y}(x_{0},y_{0})(\Delta y) & =  & 0 \\
g(x_{0}, y_{0})+g_{x}(x_{0},yx)(\Delta x) + g_{y}(x_{0},y_{0})(\Delta y) & = & 0
\end{cases}
$$
We rewrite both expressions:
$$
\begin{cases}
f_{x}(x_{0},yx)(\Delta x) + f_{y}(x_{0},y_{0})(\Delta y) & =  & -f(x_{0}, y_{0}) \\
g_{x}(x_{0},yx)(\Delta x) + g_{y}(x_{0},y_{0})(\Delta y) & = & -g(x_{0}, y_{0})
\end{cases}
$$
This is a linear system. We can thus write it as a system of equations:
$$
\begin{pmatrix}
f_{x}(x_{0},y_{0}) & f_{y}(x_{0},y_{0})\\
g_{x}(x_{0},y_{0}) & g_{y}(x_{0},y_{0})
\end{pmatrix}
\begin{pmatrix}
\Delta x \\
\Delta y
\end{pmatrix}
=
\begin{pmatrix}
-f(x_{0},y_{0}) \\
-g(x_{0},y_{0})
\end{pmatrix}
$$
We can use [[Lineære systemer#5.8 Cramer’s formel|Cramer's rule]] to get a general expression for $\Delta x,\Delta y$
$$
\begin{pmatrix}
\Delta x \\
\Delta y
\end{pmatrix}
=
\frac{1}{\det \begin{bmatrix}
f_{x}(x_{0},y_{0}) & f_{y}(x_{0},y_{0})\\
g_{x}(x_{0},y_{0}) & g_{y}(x_{0},y_{0})
\end{bmatrix}}
\begin{pmatrix}
\det \begin{bmatrix}
-f(x_{0},y_{0})  & f_{y}(x_{0},y_{0}) \\
-g(x_{0},y_{0}) & g_{y}(x_{0},y_{0}) 
\end{bmatrix} \\
\det \begin{bmatrix}
f_{x}(x_{0},y_{0}) & -f(x_{0},y_{0}) \\
g_{x}(x_{0},y_{0})  & -g(x_{0},y_{0}) 
\end{bmatrix}
\end{pmatrix}
$$
We can try and write out the determinants:
$$
\begin{pmatrix}
\Delta x \\
\Delta y
\end{pmatrix}
=
\frac{1}{
f_{x}(x_{0},y_{0})g_{y}(x_{0}y_{0})-f_{y}(x_{0},y_{0})g_{x}(x_{0}y_{0})
}
\begin{pmatrix}
-f(x_{0},y_{0})g_{y}(x_{0},y_{0})-(-g(x_{0},y_{0})f_{y}(x_{0},y_{0})) \\
-g(x_{0},y_{0})f_{x}(x_{0},y_{0})-(-f(x_{0},y_{0})g_{x}(x_{0},y_{0})) \\
\end{pmatrix}
$$
Let's simplify a bit:
$$
D(x_{0},y_{0})=f_{x}(x_{0},y_{0})g_{y}(x_{0}y_{0})-f_{y}(x_{0},y_{0})g_{x}(x_{0}y_{0})
$$
And insert in our expression above:
$$
\begin{pmatrix}
\Delta x \\
\Delta y
\end{pmatrix}
=
\frac{1}{
D(x_{0},y_{0})
}
\begin{pmatrix}
g(x_{0},y_{0})f_{y}(x_{0},y_{0})-f(x_{0},y_{0})g_{y}(x_{0},y_{0}) \\
f(x_{0},y_{0})g_{x}(x_{0},y_{0})-g(x_{0},y_{0})f_{x}(x_{0},y_{0}) \\
\end{pmatrix}
$$
It should now be obvious that for a solution to exist $D(x_{0},y_{0} )\neq 0$, must be upheld.
For a unique solution to exist, we look back at our original expression $\mathbf{Ax=b}$. 
Geometrically, the determinant can be seen as the area within the 'box' that is outlined by the four partaking functions.  Since we are taking the determinant, the result cannot be 0 - since that would result in zero or an infinite amount of results.
As a benifit of the expression above, we can express $\Delta x$ like so:
$$
\Delta x =
\frac{g(x_{0},y_{0})f_{y}(x_{0},y_{0})-f(x_{0},y_{0})g_{y}(x_{0},y_{0})}{
D(x_{0},y_{0})
}
$$
### 2
Here we call $x_{1}$ and say that $\Delta x=x-x_{0}$ now is defined by: $\Delta x=x_{1}-x_{0}$
Then we write:
$$
\begin{align*}
\begin{pmatrix}
x_{1} \\
y_{1}
\end{pmatrix}
 &=
\begin{pmatrix}
x_{1}-x_{0} +x_{0} \\
y_{1}-y_{0} +y_{0}
\end{pmatrix}
\\&=
\frac{1}{
D(x_{0},y_{0})
}
\begin{pmatrix} 
g(x_{0},y_{0})f_{y}(x_{0},y_{0})-f(x_{0},y_{0})g_{y}(x_{0},y_{0}) \\
f(x_{0},y_{0})g_{x}(x_{0},y_{0})-g(x_{0},y_{0})f_{x}(x_{0},y_{0}) \\
\end{pmatrix}
+
\begin{pmatrix}
x_{0} \\
y_{0}
\end{pmatrix}
\end{align*}
$$
$$
\begin{align}
x_{1} & = \frac{g(x_{0},y_{0})f_{y}(x_{0},y_{0})-f(x_{0},y_{0})g_{y}(x_{0},y_{0})}{D(x_{0},y_{0})}+x_{0}
\end{align}
$$
And since that 
$$
g(x_{0},y_{0})f_{y}(x_{0},y_{0})-f(x_{0},y_{0})g_{y}(x_{0},y_{0}) = -(f(x_{0},y_{0})g_{y}(x_{0},y_{0})-g(x_{0},y_{0})f_{y}(x_{0},y_{0}))
$$
We can rewrite the expression:
$$
\begin{align}
x_{1} & = x_{0} -\frac{f(x_{0},y_{0})g_{y}(x_{0},y_{0})-g(x_{0},y_{0})f_{y}(x_{0},y_{0})}{D(x_{0},y_{0})}
\end{align}
$$
and express each of the unknowns in a system of equations like so:
$$
\begin{cases}
x_{1} & = x_{0} -\frac{f(x_{0},y_{0})g_{y}(x_{0},y_{0})-g(x_{0},y_{0})f_{y}(x_{0},y_{0})}{D(x_{0},y_{0})} \\
y_{1} & = y_{0} -\frac{f_{x}(x_{0},y_{0})g(x_{0},y_{0})-g_{x}(x_{0},y_{0})f(x_{0},y_{0})}{D(x_{0},y_{0})}
\end{cases}
$$
### 3

Derivatives are given by
$$
\begin{align}
f_{x} & = \frac{\partial}{\partial x}(x^x) = \frac{\partial}{\partial x}(e^{x\ln x}) \\
 & = e^{x\ln x}(\ln (x)+1)  & \text{ (chain rule) }\\
 & = x^x(\ln(x)+1)
\end{align}
$$
Same logic applies to $f_{y}$, where: 
$$
f_{y} = y^y(\ln(y)+1)
$$
Then we calculate $g_{x}, g_{y}$
$$
\begin{align}
g_{x} & = \frac{\partial}{\partial x}(x^y)+\frac{\partial}{\partial x}(y^x) \\
 & = yx^{y-1}+y^x\ln(y)
\end{align}
$$
Here, we used the rule: $\frac{\partial}{\partial x}(a^x)=a^x\ln(x)$
We again apply the same logic to $g_{y}$
$$
\begin{align}
g_{y} & = \frac{\partial}{\partial y}(x^y)+\frac{\partial}{\partial y}(y^x) \\
 & = xy^{x-1}+x^y\ln(x)
\end{align}
$$
