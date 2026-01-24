# 1 DONE

[Link to article](https://www.statlect.com/fundamentals-of-statistics/normal-distribution-maximum-likelihood)
## 1.1
We calculate the likelihood function where $p(x_{i}|\mu)=\frac{1}{\sqrt{2 \pi \sigma^2}}e^{-\frac{(x_{i}-\mu)^2}{2\sigma ^2}}$, and $\sigma$ is some unknown fixed constant.
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

The likelihood function is thus given by:
$$
L(\mu)=(2 \pi \sigma^2)^{-n/2}
    \cdot e^{\left( -\frac{1}{2 \sigma^2} \sum_{i=1}^n (x_{i}-\mu)^2 \right)}
$$
## 1.2

We need to find the likelihood estimator $\hat{\mu}$ that maximizes the likelihood function $L(\mu)$.
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
## 1.3

To apply the MLE, we simply take the mean of the data, i.e. use the derived formula for the maximizer $\hat{\mu}$
$$
\frac{21+34+18+42+29+31+50+15+43+27+38+100+95+34-1}{15}
=38.4
$$
# 2 - 0.9

## 2.1
see excalidraw

I assume that the two hills have the same volume. Therefore mean and median are the same.
# 3

## 3.1 - 0.5
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
\Sigma=\mathbf{cov} \set{\mathbf{r}} = \frac{1}{N-1}\sum ^{N}_{n=1}\mathbf{pp}^T
$$
$\mathbf{p}$ is the centered vector, if we have the original vector $\mathbf{r}$:
$$
\mathbf{p}_{i}=\mathbf{r}_{i} -\overline{\mathbf{r}}
\space\space\space\text{ , where } \overline{\mathbf{r}} \text{ is the mean}
$$
First for drug A on itself:
$$
\begin{align}
\mathbf{cov}\set{A, A} & =
\frac{1}{N-1}\sum^{N}_{n=1} A_{n}^2 \\
 & =\frac{1}{4} (0.4^2+0.4^2+(-0.6)^2+(-0.6)^2+0.4^2) \\
 & = 0.3
\end{align}
$$
Then on A and B together:
$$
\begin{align}
\mathbf{cov}\set{A, B} & = \frac{1}{N-1}\sum^{N}_{n=1} A_{n}B_{n} \\
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

[[Egenværdier|Eigenvalues]] are found by solving
$$
\text{det}(\Sigma-\lambda \mathbf{I})=0
$$
Thus, we solve:
$$
\text{det}(\Sigma-\lambda \mathbf{I})=
\det\begin{bmatrix}
0.3-\lambda & -0.2 & -0.1\\
-0.2 & 0.3-\lambda & 0.4 \\
-0.1 & 0.4 & 0.7-\lambda
\end{bmatrix}
$$
This is done
$$
\begin{align} & 
(0.3-\lambda)\det
\begin{vmatrix}
0.3-\lambda & 0.4 \\
0.4 & 0.7-\lambda
\end{vmatrix} -(-0.2)\det
\begin{vmatrix}
-0.2 & 0.4 \\
-0.1 & 0.7-\lambda
\end{vmatrix} -0.1 \det
\begin{vmatrix}
-0.2 & 0.3-\lambda \\
-0.1 & 0.4
\end{vmatrix} \\
 & = (0.3-\lambda)((0.3-\lambda)(0.7-\lambda)-0.16)
 - (-0.2)(-0.2(0.7-\lambda)+0.04)
-0.1(-0.08+0.1(0.3-\lambda))
\end{align}
$$

We separate the terms:
1st term:
$$
\begin{align}
(0.3-\lambda)((0.3-\lambda)(0.7-\lambda)-0.16)
 & = (0.3-\lambda)(0.05-\lambda+\lambda^{2}) \\
 & = 0.3(0.05-\lambda+\lambda^{2})-\lambda(0.05-\lambda+\lambda^{2}) \\
 & = 0.015-0.3\lambda +0.3\lambda^{2}-0.05\lambda+\lambda^{2}-\lambda^{3} \\
 & = −\lambda^3+1.3\lambda^2−0.35\lambda+0.015
\end{align}
$$

2nd term:
$$
\begin{align}
-(-0.2)(-0.2(0.7-\lambda)+0.04) & = 0.2(−0.1+0.2 \lambda) \\
 & =0.04\lambda-0.02
\end{align}
$$
3rd term:
$$
\begin{align}
-0.1(0.1(0.3-\lambda)-0.08) & = 
-0.1(0.03-0.1\lambda-0.08) \\
 & = -0.1(-0.1\lambda-0.05) \\
 & = -0.005+0.01\lambda
\end{align}
$$
Put them all together:
$$
\begin{align}
 & (−\lambda^3+1.3\lambda^2−0.35\lambda+0.015)+(0.04\lambda-0.02)+(0.005+0.01\lambda) \\
 & = −\lambda^3+1.3\lambda^2+0.04\lambda+0.01\lambda−0.35\lambda+0.005+0.015-0.02 \\
 & = −\lambda^3+1.3\lambda^2+0.04\lambda+0.01\lambda−0.35\lambda \\
 & = −\lambda^3+1.3\lambda^2-0.3\lambda
\end{align}
$$
We can then factor out $\lambda$ like so:
$$
−\lambda^3+1.3\lambda^2-0.3\lambda=\lambda(−\lambda^2+1.3\lambda-0.3)
$$
It is then obvious that our first eigenvalue is $\lambda=0$, since that gives:
$$
\lambda(−\lambda^2+1.3\lambda-0.3)=0
$$
Our second eigenvalue is also obvious $\lambda=1$:
$$
1.3-0.3-(1)^{2}=0
$$
For the last eigenvalue, we must find the roots of the polynomial of 2 degrees:
$$
\begin{align}
\lambda & =\frac{1.3\pm\sqrt{ (1.3)^{2} - 4\cdot 0.3 }}{2}  \\
 & = \frac{1.3\pm\sqrt{ 0.49 }}{2} \\
 & = \frac{1.3\pm0.7}{2} \\
 & = \space 1,\space\space 0.3
\end{align}
$$
Thus we have three eigenvalues sorted by numerical value: 
$$
\set{\lambda_{1},\lambda_{2},\lambda_{3}} = \set{1,0.3,0}
$$
These values tell us a lot about the derived components and how much variance we gain by using said component. It is clear that the second component is 1/3 as impactful as the 1st, and the 3rd component does not grant any variance at all. The eigenvectors however tell us in which direction this variance is gained.  To find the eigenvectors, we solve:
$$
\begin{align}
\Sigma \mathbf{e} & = \lambda \mathbf{e}  \\
\implies \Sigma \mathbf{e} - \lambda \mathbf{e} & = 0 \\
\implies (\Sigma - \lambda\mathbf{I}) \mathbf{e} & = 0
\end{align}
$$
Each eigenvalue results in a corresponding normalized vector. In combination, they give a direction and magnitude. For example, if we have eigenvectors like these, what do they tell us? (these are example values)
$$
\begin{align*}
\begin{bmatrix}
-1 \\
4 \\
7
\end{bmatrix}
,& \space \text{ for } \space \lambda= 1\\
\begin{bmatrix}
5 \\
-2 \\
-7
\end{bmatrix}
,& \space \text{ for } \space \lambda= 0.3\\
\begin{bmatrix}
8 \\
4 \\
4
\end{bmatrix}
,& \space \text{ for } \space \lambda= 0
\end{align*}
$$
The first vector should tells us, that the most variance is gained by primarily going in the direction of the z-axis, secondly the y-axis and so on. The z-axis is the axis of survivability (S). Because this eigenvector is linked to the largest eigenvalue, it represents the first principal component, meaning it is the single direction that best summarizes the structure of the data.

\hfill

We see that the y- and z-axis are large positive values and the x-axis is a negative value. This would indicate that drug b (y-axis) usage moves together with survivability (z-axis), whereas drug a (x-axis) moves inversly with survivability. This is also seen in the covariance matrix. The second component would imply the same movement, but in the opposite direction. Increased drug A usage and decreased drug B usage results in lower survivability.

The goal is to keep the maximum amount of information even though the number of dimensions are being reduced. It is clear that maximum variance can be gained with only two components.


## 3.2 - 0.5

We can read from the table, that survival decreases a small amount when drug A is used, and increases when drug B is consumed.

# 4 - 0.2

Regression:
- Linear regression
	- The relationship between the predictor variable(s) and the response variable is reasonably linear.
	- The response variable is a continuous numeric variable.
- multivariate regression
- nonlinear regression (polynomial regression)
	- Regression is good for data with a mathematical relation
	- The relationship between the predictor variable(s) and the response variable is non-linear.
	- The response variable is a continuous numeric variable.
- Logistic regression
	- Binary response in range 0-1

Classification:
- k nearest neighbours
	- It is slow
- decision forests / random forest
	- Very good for classification
- Support vector machines (?)

Generative vs Discriminative models
Generative
	Computes probabilistic model for each class
	Can use unlabelled data
Discriminative
	Focus on separation of classes
	Cannot use unlabeled data

pre-processesing:
	- PCA
	- test-validation-holdout splitting
## Predicting apartment price
- regression

## Classifying apartments
- knn
- random forest
# 5

## 1 - 0.4

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
We calculate the information gain using entropy:
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

The gini coefficient is given by $gini(T)=1- \sum_{i} \left( \frac{T_{i}}{T} \right)^{2}$
Thus we calculate the information gain using gini:
$$
\begin{align}
Q_{gini}(T, j)
 & = gini(T)- \left(\frac{11}{30}gini(T_{x< 0.55}) +\frac{19}{30}(gini(T_{x\geq 0.55})) \right) \\
 & = \left( 1- \left( \frac{9}{30} \right)^2 - \left( \frac{21}{30} \right)^2 \right) - \left(\frac{11}{30}gini(T_{x< 0.55}) +\frac{19}{30}(gini(T_{x\geq 0.55})) \right) \\
 & =0.42-\left( \frac{11}{30} \left( 1-\left( \frac{4}{11} \right)^2 - \left( \frac{7}{11} \right)^2 \right)+\frac{19}{30}(gini(T_{x\geq 0.55})) \right) \\
 & \simeq 0.42-\left( \frac{11}{30}(0.46) + \frac{19}{30} \left( 1-\left( \frac{5}{19} \right)^2 - \left( \frac{14}{19} \right)^2 \right)\right) \\
 & \simeq 0.42-\frac{11}{30}(0.46) - \frac{19}{30} (0.39) \\
 & \simeq 0.0043
\end{align}
$$

## 2 - 0.5

- Recall the 2d line where we'd choose thresholds.
- Choose only when class changes in-between
![[Pasted image 20260113174008.png]]

This isn't entirely correct. There are multiple samples with the same restingBP value, but different labels. Lets utilize the y-axis to separate by label:
![[Pasted image 20260113181148.png]]

I found them by: 
...
Let's say that for each unique RestingBP value, there can be multiple instances with differing labels. E.g. for $\text{RestingBP}=0.6$ there are 7 instances without and 1 with heart disease. We need to test thresholds in between clusters of instances where the neighbouring clusters labels have at least one differing value. Here, we have a numerical label - so we can formulate that if the average label for the neighbours differ from this one, we test the threshold in between the clusters. 

The maximum number of thresholds to be tested to find the optimal threshold is $n-1$.
...
## 3

- for 1) something with the 2d line and the spread of data
	- plot with python every feature

# 6

![[Pasted image 20260114182606.png]]

Distance metric: Pearson correlation coefficient (L10 clustering)

Use Elbow method for clustering and finding number of clusters
Use silhouette score
Top down or bottom up? Agglomerative is bottom up

There is a problem of close points being assigned to different clusters

$$
s(\mathbf{x})=
\begin{cases}
1-a(\mathbf{x})/b(\mathbf{x}) & \text{if }a(\mathbf{x})<b(\mathbf{x}) \\
0 & \text{if}a(\mathbf{x})=b(\mathbf{x}), \text{ or } |C_{j}|=1 \\
b(\mathbf{x})/a(\mathbf{x})-1 & \text{if } a(\mathbf{x})>b(\mathbf{x})
\end{cases}
$$