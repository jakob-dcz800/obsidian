
# 4

Let $D_{A}$ be the event where $A$ was the [[Random variables|randomly]] chosen dice and let $X=\set{5,3,9,3,8,4,7}$ be the rolled outcomes. We want the probability: $P(D_{A}|X)$, i.e. the chance that dice A was chosen given X.
For this we use [[Probability#Bayes rule|Bayes rule]]:
$$
P(D_{A}|X)= \frac{P(X|D_{A})P(D_{A})}{P(X)}
$$
We assume that the probability for each of the dice to be chosen is $0.5$:
$$
P(D_{A})=P(D_{B})=0.5
$$
Now we calculate $P(X|D_{A})$ and $P(X|D_{B})$
$$
\begin{align}
P(X|D_{A}) &  = 
P(\set{5}|D_{A})\cdot
P(\set{3}|D_{A})\cdot
P(\set{9}|D_{A})\cdot
P(\set{3}|D_{A})\cdot
P(\set{8}|D_{A})\cdot
P(\set{4}|D_{A})\cdot
P(\set{7}|D_{A})  \\
& = 
\frac{1}{20}\cdot \frac{3}{20}\cdot \frac{1}{20}\cdot \frac{3}{20}\cdot \frac{1}{20} \cdot\frac{2}{20} \cdot \frac{1}{20} \\
 & = \frac{18}{20^7}
\end{align}
$$
$$
\begin{align}
P(X|D_{B}) &  = 
P(\set{5}|D_{B})\cdot
P(\set{3}|D_{B})\cdot
P(\set{9}|D_{B})\cdot
P(\set{3}|D_{B})\cdot
P(\set{8}|D_{B})\cdot
P(\set{4}|D_{B})\cdot
P(\set{7}|D_{B})  \\
& = 
\frac{2}{20}\cdot \frac{2}{20} \cdot \frac{1}{20} \cdot \frac{2}{20} \cdot \frac{2}{20} \cdot \frac{2}{20} \cdot \frac{2}{20}
\\  & =\frac{64}{20^7}
\end{align}
$$
Now, let us calculate $P(X)$ using [[Probability#Law of total probability|the law of total probability]].
Recall that $P(A)= \sum^m_{i=1} P(A|B_{i})P(B_{i})$, where $P(B_{i})=P(D)=\frac{1}{3}$
$$
\begin{align}
P(X) & =\frac{1}{2}\left( \frac{64}{20^7}+\frac{18}{20^7} \right) \\
 & = \frac{1}{2}\left( \frac{82}{20^7} \right) \\
 & = \frac{41}{20^7}
\end{align}
$$
Now we can calculate the probability that the chosen dice was $A$
$$
\begin{align}
P(D_{A}|X) & = \frac{\frac{1}{2}\left( \frac{18}{20^7} \right)}{\frac{41}{20^7}} \\
 & = \frac{\frac{9}{20^7}}{\frac{41}{20^7}} \\
 & = \frac{9(20^7)}{41(20^7)} \\
 & = \frac{9}{41}  \\
 & \simeq 0.22
\end{align}
$$
We see that the probability that the chosen dice is 0.22.
Let's perform a sanity check and calculate the probability that the chosen dice was B:
$$
\begin{align}
P(D_{B}|X) & = \frac{\frac{1}{2}\left( \frac{64}{20^7} \right)}{\frac{41}{20^7}} \\
 & = \frac{\frac{32}{20^7}}{\frac{41}{20^7}} \\
 & = \frac{32(20^7)}{41(20^7)} \\
 & = \frac{32}{41}  \\
 & \simeq 0.78
\end{align}
$$
We see that $\frac{32}{41}+\frac{9}{41}=1$, i. e. the probability that any dice was chosen is 1.
### b

Yes, this changes our belief that the dice was A. It is less likely that the dice will be A now that a third dice has been introduced. The answer depends a lot on how we know C looks like. If it was a dice with just the number 10 on it, the chance that the selected dice is A would increase. But in reality, C looks a lot like B. When we calculated  $P(X|D_{B})$ we got $\frac{64}{20^7}$, but because all numbers have chance $2 / 20$ to be rolled, the chance of rolling $X$ will be double the chance of $B$:
$$
\begin{align}
P(X|D_{C}) &  = 
P(\set{5}|D_{C})\cdot
P(\set{3}|D_{C})\cdot
P(\set{9}|D_{C})\cdot
P(\set{3}|D_{C})\cdot
P(\set{8}|D_{C})\cdot
P(\set{4}|D_{C})\cdot
P(\set{7}|D_{C})  \\
& = 
\frac{2}{20}\cdot \frac{2}{20} \cdot \frac{2}{20} \cdot \frac{2}{20} \cdot \frac{2}{20} \cdot \frac{2}{20} \cdot \frac{2}{20}
\\  & =\frac{128}{20^7}
\end{align}
$$

Now we calculate that $X$ was rolled by dice A, B, and C. We reuse our calculations from above:
$$
\begin{align}
P(X|D_{A})= \frac{18}{20^7} \\
P(X|D_{B})= \frac{64}{20^7} \\
P(X|D_{C})= \frac{128}{20^7}
\end{align}
$$
For these calculations we see that $P(D_{A})=P(D_{B})=P(D_{C})=\frac{1}{3}$
We then calculate $P(X)$:
$$
\begin{align}
P(X) & =\frac{1}{3}\left( \frac{64}{20^7}+\frac{18}{20^7}+\frac{128}{20^7} \right) \\
 & = \frac{1}{3}\left( \frac{210}{20^7} \right) \\
 & = \frac{70}{20^7}
\end{align}
$$
Now we can calculate $P(D_{A}|X)$, $P(D_{B}|X)$, $P(D_{C}|X)$:

$$
\begin{align}
P(D_{C}|X) & = \frac{\frac{1}{3}\left( \frac{128}{20^7} \right)}{\frac{70}{20^7}} \\
 & = \frac{\frac{128}{3(20^7)}}{\frac{70}{20^7}} \\
 & =\frac{128(20^7)}{210(20^7)} \\
 & = \frac{128}{210} \\
 & \simeq 0.6
\end{align}
$$
$$
\begin{align}
P(D_{B}|X) & = \frac{\frac{1}{3}\left( \frac{64}{20^7} \right)}{\frac{70}{20^7}} \\
 & = \frac{\frac{64}{3(20^7)}}{\frac{70}{20^7}} \\
 & =\frac{64(20^7)}{210(20^7)} \\
 & = \frac{64}{210} \\
 & \simeq 0.3
\end{align}
$$
$$
\begin{align}
P(D_{A}|X) & = \frac{\frac{1}{3}\left( \frac{18}{20^7} \right)}{\frac{70}{20^7}} \\
 & = \frac{\frac{6}{20^7}}{\frac{70}{20^7}} \\
 & =\frac{6(20^7)}{70(20^7)} \\
 & = \frac{6}{70} \\
 & \simeq 0.09
\end{align}
$$
Lets do a sanity check:
$$
\frac{64}{210}+\frac{128}{210}+\frac{18}{210}= 1 
$$
It is clear that our presumptions about dice C and the affect on the probability of dice A was correct. The probability that dice A was chosen dropped from $9/41$ to $6/70$.
# 4

5, 3, 9, 3, 8, 4, 7

We should start calculating $P_{k}(X)$:
$$
\begin{align}
P_{A}(5)\cdot
P_{A}(3)\cdot
P_{A}(9)\cdot
P_{A}(3)\cdot
P_{A}(8)\cdot
P_{A}(4)\cdot
P_{A}(7) & = 
\frac{1}{20}\cdot \frac{3}{20}\cdot \frac{1}{20}\cdot \frac{3}{20}\cdot \frac{1}{20} \cdot\frac{2}{20} \cdot \frac{1}{20} \\
 & = \frac{18}{20^7}
\end{align}

$$
And
$$
\begin{align}
P_{B}(5)\cdot
P_{B}(3)\cdot
P_{B}(9)\cdot
P_{B}(3)\cdot
P_{B}(8)\cdot
P_{B}(4)\cdot
P_{B}(7)
 & = \frac{2}{20}\cdot \frac{2}{20} \cdot \frac{1}{20} \cdot \frac{2}{20} \cdot \frac{2}{20} \cdot \frac{2}{20} \cdot \frac{2}{20}
\\  & =\frac{64}{20^7}
\end{align}
$$
$$
\frac{P(A)}{P(A)+P(B)}
$$
# 2

[watch this](https://www.youtube.com/watch?v=UubU3U2C8WM&t=28s)
$$
\int \int_{R} (3xy^2-xy+1) dA =
\int^{4}_{3} \int^{2}_{-1} (3xy^2-xy+1) dxdy
$$
On the rectangle
$$
R=\set{[a,b]\times[c, d]} = \set{(x,y)\mid a \leq x\leq b, c\leq y\leq d }
$$
Since $dA=dxdy=dydx$ we can see that
$$
\int^{4}_{3} \int^{2}_{-1} (3xy^2-xy+1) dxdy=
\int^{2}_{-1} \int^{4}_{3} (3xy^2-xy+1) dydx
$$
We choose to integrate the first option ($dxdy$)
We start off by solving the innermost integral with respect to $x$.
$$
\int(3xy^2-xy+1)
=\frac{3}{2}x^2y^2-\frac{1}{2}x^2y+x
$$
Then we get the integral within the bounds: 
$$
\begin{align}
\int_{-1}^{2}(3xy^2-xy+1) dx& =
\left[ \frac{3}{2}x^2y^2-\frac{1}{2}x^2y+x \right]_{-1}^{2} \\
 & = (6y^2-2y+2) - \left( \frac{3}{2}y^{2}-\frac{1}{2}y-1 \right) \\
 & =6y^2-2y+2-\frac{3}{2}y^2+\frac{1}{2}y+1 \\
 & = \left( 6-\frac{3}{2}\right)y^2 +\left(-2+\frac{1}{2} \right) y+3 \\
 & =\frac{9}{2}y^2-\frac{3}{2}y+3
\end{align}
$$
Now we can integrate with respect to y within the outer bounds.
First we take the integral of the inner expression:
$$
\begin{align}
\int \left( \frac{9}{2}y^2-\frac{3}{2}y+3 \right)dy & =
\frac{9}{2} \left( \frac{1}{3}y^3 \right)-\frac{3}{2} \left( \frac{1}{2} y^2\right)+3y \\
 & = \frac{9}{6}y^3-\frac{3}{4}y^2+3y \\
 & = \frac{3y^3}{2}-\frac{3y^2}{4}+3y
\end{align}
$$
Now we are ready to integrate within the boundaries:
$$
\begin{align}
\int^4_{3}\left( \frac{9}{2}y^2-\frac{2}{3}y+3 \right)dy & =
\left[ \frac{3y^3}{2}-\frac{3y^2}{4}+3y \right]^4_{3} \\
 & = \left( \frac{3(4^3)}{2}-\frac{3(4^2)}{4}+12 \right)-
\left( \frac{3(3^3)}{2} - \frac{3(3^2)}{4}+9 \right) \\
 & = \left( \frac{192}{2} - \frac{24}{2}+\frac{24}{2} \right)
-\left( \frac{81}{2} -\frac{27}{4} +\frac{18}{2} \right) \\
 & = \frac{384-171}{4} = 53.25
\end{align}
$$
Thus, the volume between the $xy$-plane and $3xy^2-xy+1$ is equal to $53.25$

Do the innermost integral first
![[Pasted image 20251005225248.png]]

But since $dxdy=dydx$ we can switch them like so:
![[Pasted image 20251005225413.png]]

![[Pasted image 20251005225555.png]]
x runs between a and b, while y runs between c and d.
Therefore the innermost integral is bound by a and b with dx.