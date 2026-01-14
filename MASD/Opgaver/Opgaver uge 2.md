---
tags:
  - Assignment
---
## Opgave 1

[[Regneregler#Brøker|Regneregler]]
### 1

$f(x) = 3x^2- 2\cos x$
Løs $f'$
$$
\begin{align}
6x+2\sin x
\end{align}
$$
### 2
Løs $h'(\Theta)$:
$$
h(\Theta) = \frac{1}{\sin \Theta}+\frac{e^{\Theta}}{\tan \Theta}
$$
Først del h op:
$$
\begin{align}
h(\Theta) & =f(\Theta)+g(\Theta) \\
f(\Theta) & = \frac{1}{\sin \Theta}\\
g(\Theta) & = \frac{e^\Theta}{\tan \Theta}
\end{align}
$$
Så differentierer vi g vha. kædereglen
$$
\begin{align}
f'  &  = -\frac{1}{(\sin \Theta)^2}+\cos \Theta\\
g' & =\frac{e^\Theta \tan (\Theta) + e^\Theta \cdot (1+(\tan (\Theta)^2))}{\tan^2\Theta}
\end{align}
$$

Så lægger vi dem sammen:
$$
h'(\Theta) = \frac{\cos \Theta}{\sin^2\Theta}+
\frac{e^\Theta \tan (\Theta) + e^\Theta \cdot (1+(\tan (\Theta)^2))}{\tan^2 \Theta}
$$

## Opgave 2

### 1
$h=\sqrt{ 4+3x }$

Vi har de to funktioner:
$$
\begin{align}
u & = g(x) = 4+3x \\
y & =f(x) = \sqrt{ u }
\end{align}
$$
Vi bruger kædereglen $\frac{d}{dx}f(g(x))=f'(g(x))\cdot g'(x)$
Vi differentierer først f, g:
$$
\begin{align}
y' & = \frac{1}{2\sqrt{ u }} \\
u' & = 3
\end{align}
$$
Vi udleder udtrykket:
$$
\begin{align}
h' & =\frac{1}{2\sqrt{ 4+3x }}\cdot3 \\
 & = \frac{3}{2\sqrt{ 4+3x }}
\end{align}
$$
### 2
$h=n\sin e^x$
$n$ er en konstant - så vi bruger regel nr. 3
Vi deler så funktionen op:
$$
\begin{align}
g(x) = u & = e^x \\
f(x) = y & = \sin u
\end{align}
$$
Vi benytter kædereglen: $\frac{d}{dx}f(g(x))=f'(g(x))\cdot g'(x)$
$$
h'(x) =n\cdot\cos(e^x)\cdot e^x
$$


## Opgave 3

### 1
$f(x)=(1+x^4)^{2/3}$

$$
\begin{align}
f'(x) &  = \frac{2}{3}(1+x^4)^{-1/3}\cdot 4x^3 \\
 & =\frac{8}{3}(1+x^4)^{-1/3}\cdot x^3 \\
 & = \frac{8}{3(1+x^4)^{-1/3}}x^3 \\
 & = \frac{8x^3}{3(1+x^4)^{-1/3}}
\end{align}
$$
### 2
[[Regneregler]]

$h(t)=(t^4-1)^3(t^3+1)^4$

Her kan vi først dele funktionen op i to - og bruge produktreglen.
Begge funktioner differentieres ved at bruge kædereglen.

$$
\begin{align}
u(t) & =(t^4-1)^3 \\
y(t) & =(t^3+1)^4 \\
 \\
u'(t) & =3(t^4-1)^2\cdot 4t^3  = 12(t^4-1)^2\cdot t^3\\
v'(t) & =4(t^3+1)^3\cdot 3t^2 = 8(t^3+1)^3\cdot t^2
\end{align}
$$
Dernæst sætter vi dem sammen vha. produktreglen:
$$
\begin{align}
h'(t)  & = u'(t)v(t)+u(t)v'(t) \\
 & =(12(t^4-1)^2\cdot t^3)
(t^3+1)^4
+(t^4-1)^3(8(t^3+1)^3\cdot t^2)
\end{align}
$$
## 12

$$
f_{x}(x)=\frac{1}{2\sqrt{ x }}\ln t
$$
$$
f_{t}(x)= \frac{\sqrt{ x }}{t}
$$
## 13

Vi benytter kædereglen, differentierer kun mht. $z$.
$$
\begin{align}
\frac{d}{dz}f(x,y,z) & =
\end{align}
$$
