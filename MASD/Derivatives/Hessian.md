# Example
$$
Hf(x, y) =  
\begin{pmatrix}  
3 & 2 \\
2 & 4  
\end{pmatrix}.  
$$

---

### Step 1: Write the characteristic equation

Eigenvalues ($\lambda$) satisfy

$\det(Hf - \lambda I) = 0$  

That means:
$$
\det  
\begin{pmatrix}  
3 - \lambda & 2 \\
2 & 4 - \lambda  
\end{pmatrix}  
= 0
$$

---

### Step 2: Compute the determinant

$$
(3 - \lambda)(4 - \lambda) - (2)(2) = 0
$$
Simplify:

$12 - 3\lambda - 4\lambda + \lambda^2 - 4 = 0$
$\lambda^2 - 7\lambda + 8 = 0$

---

### Step 3: Solve the quadratic equation

Use the quadratic formula:

$\lambda = \frac{7 \pm \sqrt{(-7)^2 - 4(1)(8)}}{2(1)} = \frac{7 \pm \sqrt{49 - 32}}{2}$

Simplify:
$\lambda = \frac{7 \pm \sqrt{17}}{2}$

---

### Step 4: Interpret the results

So the eigenvalues are
$$
\lambda_1 = \frac{7 - \sqrt{17}}{2}, \quad  
\lambda_2 = \frac{7 + \sqrt{17}}{2}
$$

Since both are **positive**, (Hf) is **positive definite**.

---

✅ **Final Answer:**


$$
\boxed{  
\lambda_1 = \frac{7 - \sqrt{17}}{2}, \quad  
\lambda_2 = \frac{7 + \sqrt{17}}{2}.  
}  
$$

# Interpretation

## 🧭 Step 1: Recall what the Hessian is

For a function ( $f(x, y)$ ), the **Hessian matrix** is:

$$
Hf(x, y) =  
\begin{pmatrix}  
f_{xx} & f_{xy} \\  
f_{yx} & f_{yy}  
\end{pmatrix}
$$

At a **critical point** ( $(x_0, y_0)$ ), where ( $f_x = 0$ ) and ( $f_y = 0$ ),  
we use ( $Hf(x_0, y_0)$ ) to determine the _type_ of that point.

---

## 🧮 Step 2: Compute these quantities

Let:  
$$
D = \det(Hf) = f_{xx}f_{yy} - (f_{xy})^2
$$
and also note the sign of ( $f_{xx}$ ).

---

## 📊 Step 3: Apply the classification test

| Case        | $( D = f_{xx}f_{yy} - (f_{xy})^2 )$ | $( f_{xx} )$                                                            | Type of Critical Point |
| ----------- | ----------------------------------- | ----------------------------------------------------------------------- | ---------------------- |
| $( D > 0 )$ | $( f_{xx} > 0 )$                    | → Local **minimum**                                                     |                        |
| $( D > 0 )$ | $( f_{xx} < 0 )$                    | → Local **maximum**                                                     |                        |
| $( D < 0 )$ | $—$                                 | → **Saddle point**                                                      |                        |
| $( D = 0 )$ | $—$                                 | → **Inconclusive** (could be inflection, saddle, etc. — need more info) |                        |

---

## 🧠 Intuition

- ( $D > 0$ ): curvature is the same in all directions → “bowl” shape (min) or “hill” shape (max).
- ( $D < 0$ ): curvature changes sign → “saddle”.
- ( $D = 0$ ): too flat or complicated — must check higher-order terms.

---

## ✅ Example

If:  
$$
Hf =  
\begin{pmatrix}  
3 & 2 \  
2 & 4  
\end{pmatrix}
$$
then:  
$$
D = 3 \cdot 4 - 2^2 = 12 - 4 = 8 > 0, \quad f_{xx} = 3 > 0.  

$$
⇒ **Local minimum**.