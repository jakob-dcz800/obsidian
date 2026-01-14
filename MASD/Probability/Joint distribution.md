![[PMF#Joint distributions]]


## Range

$$
R_{XY}=\set{(x,y) \mid P_{XY}(x, y) > 0}
$$
Sometimes we define $R_{XY}=R_X×R_Y$ to simplify the analysis
For two discrete random variables X and Y, we have
$$
\sum_{(x_{i}, y_{i}) \in R_{XY}}P_{XY}(x_{i}, y_{i})=1
$$
Note that
$$
\begin{align}
P_{XY}(x,y) & =P(X=x,Y=y) \\
 & =P((X=x)∩(Y=y))
\end{align}
$$

Note that we can use the joint PMF to find $P((X,Y)∈A)$ for any set $A⊂\mathbb{R}^2$
$$
P((X,Y) \in A) = \sum_{(x_{i}, y_{i})\in (A \cap R_{XY})}P_{XY}(x_{i}, y_{i})
$$

## Marginal PMFs

$$
\begin{align}
\label{} \nonumber P_X(x) &= P(X=x)\\ \nonumber &=\sum_{y_j \in R_Y} P(X=x, Y=y_j) &\textrm{law of total probablity}\\ \nonumber &=\sum_{y_j \in R_Y} P_{XY}(x,y_j). \end{align}
$$

### Theorem 5.1
$$
\begin{align} 
\nonumber P_X(x)&=\sum_{y_j \in R_Y} P_{XY}(x,y_j), \hspace{20pt} \textrm{ for any } x \in R_X \\
P_Y(y)&=\sum_{x_i \in R_X} P_{XY}(x_i,y), \hspace{20pt} \textrm{ for any } y \in R_Y
\end{align}
$$
## Example


|         | $Y = 0$       | $Y = 1$       | $Y = 2$       |
| ------- | ------------- | ------------- | ------------- |
| $X = 0$ | $\frac{1}{6}$ | $\frac{1}{4}$ | $\frac{1}{8}$ |
| $X = 1$ | $\frac{1}{8}$ | $\frac{1}{6}$ | $\frac{1}{6}$ |
a. Find $P(X=0,Y\leq1)$
$$
\begin{align}\label{} \nonumber P(X=0, Y \leq 1) =P_{XY}(0,0)+ P_{XY}(0,1) \\
=\frac{1}{6}+\frac{1}{4} \\
=\frac{5}{12}\end{align}
$$

b. Find the marginal PMFs of $X$ and $Y$.
Note that from the table,
$$
    \begin{align}\label{} \nonumber R_X=\{0,1\} \hspace{20pt}\textrm{ and }\hspace{20pt} R_Y=\{0,1,2\}. \end{align}
$$
Now we can use Equation 5.1 to find the marginal PMFs. For example, to find $P_X(0)$, we can write
$$
\begin{align}\label{} \nonumber P_X(0)&=P_{XY}(0,0)+P_{XY}(0,1)+P_{XY}(0,2)\\ \nonumber &=\frac{1}{6}+\frac{1}{4}+\frac{1}{8}\\ \nonumber &=\frac{13}{24}. \end{align}
$$
We obtain
$$\begin{equation} \nonumber P_X(x) = \left\{ \begin{array}{l l} \frac{13}{24} & \quad x=0 \\ & \quad \\ \frac{11}{24} & \quad x=1 \\ & \quad \\ 0 & \quad \text{otherwise} \end{array} \right. \end{equation}$$
$$
\begin{equation} \nonumber P_Y(y) = \left\{ \begin{array}{l l} \frac{7}{24} & \quad y=0 \\ & \quad \\ \frac{5}{12} & \quad y=1 \\ & \quad \\ \frac{7}{24} & \quad y=2 \\ & \quad \\ 0 & \quad \text{otherwise} \end{array} \right. \end{equation}
$$

c. Find $P(Y=1|X=0)$.
Using the formula for conditional probability, we have
$$
\begin{align}\label{} \nonumber P(Y=1 | X=0)&=\frac{P(X=0, Y=1)}{P(X=0)}\\ \nonumber &=\frac{P_{XY}(0,1)}{P_X(0)}\\ \nonumber &=\frac{\frac{1}{4}}{\frac{13}{24}} \\
 & =\frac{6}{13} \end{align}
$$

d. Are $X$ and $Y$ independent?
X and Y **are not independent**, because as we just found out
$$
\begin{align}\label{} \nonumber P(Y=1|X=0)=\frac{6}{13} \neq P(Y=1)=\frac{5}{12}. \end{align}
$$

**Caution**: If we want to show that X and Y are independent, we need to check that $P(X=x_i,Y=y_j)=P(X=x_i)P(Y=y_j)$, for all $x_i \in R_X$ and all $y_j \in R_Y$. 
Thus, even if in the above calculation we had found $P(Y=1 | X=0)= P(Y=1)$, we would not yet have been able to conclude that X and Y are independent. 
For that, we would need to check the independence condition for all $x_i \in R_X$ and all $y_j \in R_Y$.