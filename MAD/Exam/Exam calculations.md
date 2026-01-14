# 1

[Link to article](https://www.statlect.com/fundamentals-of-statistics/normal-distribution-maximum-likelihood)
## 1.1
$$
\begin{align*}
L(\mu)&= \prod^n_{i=1}  p(x_i\mid \mu)\\
& = \prod_{i=1}^n \frac{1}{\sqrt{2 \pi \sigma^2}}e^{-\frac{(x_{i}-\mu)^2}{2\sigma ^2}} \\
& = \left( \frac{1}{\sqrt{2 \pi \sigma^2}} \right)^n
    \cdot e^{\left( -\frac{1}{2 \sigma^2} \sum_{i=1}^n (x_{i}-\mu)^2 \right)}\\
& = (2 \pi \sigma^2)^{-n/2}
    \cdot e^{\left( -\frac{1}{2 \sigma^2} \sum_{i=1}^n (x_{i}-\mu)^2 \right)}
\end{align*}
$$
Here, the property is used: $\prod e^a=e^{\sum a}$, such that we can separate constant from variable terms.
It is also used, that $\left( \frac{1}{\sqrt{ a }} \right)^n = \left( \frac{1}{a^{1/2}} \right)^n=(a^{-1/2})^n=a^{-n/2}$
## 1.2

We need to find the likelihood estimator $\hat{\mu}$ that maximizes the likelihood function.

First we take the natural logarithm of $L(\mu)$
$$
\begin{align}
l(\mu) & = \ln(L(\mu)) \\
 & = \ln((2 \pi \sigma^2)^{-n/2}) + \ln \left( e^{\left( -\frac{1}{2 \sigma^2} \sum_{i=1}^n (x_{i}-\mu)^2 \right)} \right)
\\
 & = -\frac{n}{2} \ln((2 \pi \sigma^2))
- \frac{1}{2 \sigma^2} \sum_{i=1}^n (x_{i}-\mu)^2
\end{align}
$$
Then we find the derivative of $L(\mu)$ since we must know $\text{argmax}(l(\mu))$. We use the derivative to find $\frac{\partial l(\mu)}{\partial \mu}=0$. Since we have the variable $\sigma ^2$, we take the derivative with respect to $\mu$:
$$
\begin{align}
\frac{\partial l(\mu)}{\partial\mu} & = 
\frac{\partial}{\partial\mu} \left( -\frac{n}{2} \ln((2 \pi \sigma^2))
- \frac{1}{2 \sigma^2} \sum_{i=1}^n (x_{i}-\mu)^2 \right) \\
 & = \frac{\partial}{\partial\mu}\left( - \frac{1}{2 \sigma^2} \sum_{i=1}^n (x_{i}-\mu)^2 \right) \\
 & = - \frac{1}{2 \sigma^2} \sum_{i=1}^n \frac{\partial}{\partial\mu} (x_{i}-\mu)^2 \\
 & = -\frac{1}{2 \sigma^2} \sum_{i=1}^n 2(x_{i}-\mu)(-1) \\
 & = \frac{1}{\sigma^2} \left( \left( \sum_{i=1}^n x_{i} \right)-n\mu \right) \\
\end{align}
$$
We assume that $\sigma^{2}$ won't be equal to zero, and see that for the derivative to be equal to zero:
$$
\sum ^{n}_{i=1}x_{i}-n \hat \mu =0
$$
We rearrange the expression to derive $\hat{\mu}$:
$$
\begin{align}
 & \sum ^{n}_{i=1}x_{i}-n\hat{\mu} = 0 \\
\implies  & \sum ^{n}_{i=1}x_{i} = n\hat{\mu} \\
\implies  & \frac{1}{n} \sum ^{n}_{i=1}x_{i} = \hat{\mu}
\end{align}
$$
## 3

To apply the MLE, we simply take the mean of the data.

# 2

see excalidraw

I assume that the two hills have the same volume. Therefore mean and median are the same.
# 3

Data table:

| patient | Drug A | Drug B | Survival (years) |
| ------- | ------ | ------ | ---------------- |
| 1       | 1      | 0      | 1                |
| 2       | 1      | 0      | 1                |
| 3       | 0      | 1      | 2                |
| 4       | 0      | 1      | 2                |
| 5       | 1      | 1      | 3                |
We assume that drug usage is a boolean and not a volume.
We first center the data to the zero mean.
The means are:

| Drug A | Drug B | Survival (years) |
| ------ | ------ | ---------------- |
| 0.6    | 0.6    | 1.8              |
So we get the normalized data:

| patient | Drug A | Drug B | Survival S |
| ------- | ------ | ------ | ---------- |
| 1       | 0.4    | -0.6   | -0.8       |
| 2       | 0.4    | -0.6   | -0.8       |
| 3       | -0.6   | 0.4    | 0.2        |
| 4       | -0.6   | 0.4    | 0.2        |
| 5       | 0.4    | 0.4    | 1.2        |
We calculate the covariance matrix:
$$
\mathbf{cov} \set{\mathbf{r}} = \frac{1}{N-1}\sum ^{n}_{i=1}\mathbf{pp}^T
$$
First for drug A on itself:
$$
\begin{align}
\mathbf{cov}\set{A, A} & =
\frac{1}{N-1}\sum^{N}_{i=1}x_{i}y_{i} \\
& = \frac{1}{N-1}
\begin{bmatrix}
0.4 &
0.4 &
-0.6 &
-0.6 &
0.4
\end{bmatrix}
\times
\begin{bmatrix}
0.4\\
0.4\\
-0.6\\
-0.6\\
0.4
\end{bmatrix} \\
 & =\frac{1}{4} (0.4^2+0.4^2+(-0.6)^2+(-0.6)^2+0.4^2) \\
 & = 0.3
\end{align}
$$
Then on A and B together:
$$
\begin{align}
\mathbf{cov}\set{A, B} & = \frac{1}{N-1}
\begin{bmatrix}
0.4 &
0.4 &
-0.6 &
-0.6 &
0.4
\end{bmatrix}
\times
\begin{bmatrix}
-0.6\\
-0.6\\
0.4\\
0.4\\
0.4
\end{bmatrix} \\
 & =\frac{1}{4} (4(0.4\cdot (-0.6))+0.4^2) \\
 & = -0.2
\end{align}
$$
And then for the rest:
$$
\begin{align}
\mathbf{cov}\set{A, S}
 & =\frac{1}{4}(0.4 \cdot (-0.8)+ 0.4 \cdot(-0.8)+(-0.6) \cdot (0.2) + (-0.6) \cdot (0.2) + 0.4 \cdot 1.2) \\
 & = -0.1
\end{align}
$$
$$
\begin{align}
\mathbf{cov}\set{B, B}
 & =\frac{1}{4} (0.4^2+0.4^2+(-0.6)^2+(-0.6)^2+0.4^2) \\
 & = 0.3
\end{align}
$$
$$
\begin{align}
\mathbf{cov}\set{B, S}
 & =\frac{1}{4}((-0.6 \cdot (-0.8))+(-0.6\cdot (-0.8))+(0.4 \cdot 0.2 )+(0.4 \cdot 0.2 )+(0.4 \cdot 1.2 )) \\
 & = 0.4
\end{align}
$$
$$
\begin{align}
\mathbf{cov}\set{S, S}
 & =\frac{1}{4}(
(-0.8)^2+(-0.8)^2+0.2^2+0.2^2+1.2^2
) \\
 & = 0.7
\end{align}
$$

|            | Drug A | Drug B | Survival S |
| ---------- | ------ | ------ | ---------- |
| Drug A     | 0.3    |        |            |
| Drug B     | -0.2   | 0.3    |            |
| Survival S | -0.1   | 0.4    | 0.7        |

Eigenvalues are found by solving
$$
\text{det}(\mathbf{cov}\set{\mathbf{r}}-\lambda \mathbf{I})=0
$$
Thus, we solve:
$$
\det\begin{bmatrix}
0.3-\lambda & -0.2 & -0.1\\
-0.2 & 0.3-\lambda & 0.4 \\
-0.1 & 0.4 & 0.7-\lambda
\end{bmatrix}
$$
This is done (maybe)
$$
\begin{align}
(0.3-\lambda)(0.3-\lambda)(0.7-\lambda)+(-0.2\cdot 0.4)(-0.1)+(-0.1\cdot 0.4)()
\end{align}
$$

![[Determinant#Definition]]
## 3.2

We can read from the table, that survival decreases a small amount when drug A is used, and increases when drug B is consumed.

# 4

Models:
- Linear regression
- multivariate regression
- nonlinear regression
	- logarithmic regression
	- Regression is good for data with a mathematical relation
- classification regression
- kn neighbours
- decision forests / random forest
	- Very good for classification

# 5

## 1

We note the number of candidates for each side of the split:
$$
\begin{align}
19 \text{ candidates} & \geq 0.55 \\
11 \text{ candidates} & < 0.55
\end{align}
$$
Then we calculate the entropy with this formula:
$$
H(T)=-p_{+} \log_{2} p_{+}-p_{-} \log_{2} p_{-}
$$

There are 9 samples *with* heart disease and 21 without
We calculate
$$
\begin{align}
Q_{H}(T, j) & = H(21, 9)- \frac{19}{30}H(14, 5)-\frac{11}{30}H(7,4) \\
 & = \left( -\frac{21}{30}\log_{2}\left( \frac{21}{30} \right) -\frac{9}{30}\log_{2}\left( \frac{9}{30} \right) \right) - \frac{19}{30}H(14, 5)-\frac{11}{30}H(7,4) \\
 & \simeq 0.88- \frac{19}{30}\left(-\frac{14}{19} \log_{2}\left( \frac{14}{19} \right)-\frac{5}{19} \log_{2}\left( \frac{5}{19} \right) \right)-\frac{11}{30}H(7,4)\\
 & \simeq 0.88- \frac{19}{30}\left(0.83\right)-\frac{11}{30} \left(-\frac{7}{11} \log_{2}\left( \frac{7}{11} \right)-\frac{4}{11} \log_{2}\left( \frac{4}{11} \right) \right) \\
& \simeq 0.88- \frac{19}{30}(0.83)- \frac{11}{30}(0.946) \\
& \simeq 0.00746
\end{align}
$$

The gini coefficient is given by:
$$
gini(T)=1-\sum_{i} \left( \frac{|T_{i}|}{|T|} \right)^2
$$
$$
\begin{align}
Q_{Gini}(T,j) & = gini(T)
\end{align}
$$
## 2

- Recall the 2d line where we'd choose thresholds.
- Choose only when class changes in-between
![[Pasted image 20260113174008.png]]

This isn't entirely correct. There are multiple samples with the same restingBP value, but different labels. Lets utilize the y-axis to separate by label:
![[Pasted image 20260113181148.png]]

**What then?**
## 3

- for 1) something with the 2d line and the spread of data
	- plot with python every feature