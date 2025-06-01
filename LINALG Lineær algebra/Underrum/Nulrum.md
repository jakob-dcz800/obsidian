# Nulrum

## Definition

Nulrummet er de søjler i $\Bbb{R}^n$ som opfylder $\mathbf{Ax}=\mathbf{0}$
Nulrummet er et [[Underrum#Definition 3.2|underrum]] af $\Bbb{R}^n$
Skrives $\text{null A}$

![[Pasted image 20250506212922.png]]

## Theorem

### 3.11

![[Pasted image 20250506213022.png]]



## Eksempel

### 1
Vi vil gerne finde en basis for nulrummet af $A$

![[Pasted image 20250506212951.png]]

Man bør tage nullerne med på højre side af matricen.

![[Pasted image 20250506212958.png]]

Vi får jo altså at den generelle løsning er en linearkombination af vektorerne
De to vektorer $sv+st$ [[Span|udspænder]] altså nulrummet, derfor mangler vi bare at vise, at de er lineært uafhængige.

![[Pasted image 20250506213006.png]]

De to frie variabler vil være lineært uafhængige pga. 0 og 1 plads.
### 2
![[Pasted image 20250506213034.png]]

For at løse $\mathcal{B}$ tager vi nulsøjlen på $\mathbf{B}$.
$x_{4}$ er en fri variabel
$$
\begin{matrix}
x_{3}+x_{4}=0 \to  \\
x_{3}= (-x_{4})\to \\
x_{3}=-t
\end{matrix}
$$
Vi skriver $-1$ på $x_{3}$'s række (søjle to i $\mathcal{B}$)
$x_{2}$ er også en fri variabel:
$$
\begin{matrix}
x_{1}+2s+t=0\to\\
x_{1}=(-2s)-t
\end{matrix}
$$
Så vi skriver $-2$ på $x_{1}$'s plads kolonne 1, og $-1$ kolonne 2.
## Nullity

Lad $A$ være en $m \times n$ matrix, man definerer:
$$
\text{nullity }A = \text{dim}(\text{null }A)
$$
[[#3.11|Theorem 3.11]] kan derfor skrives som:
$$
\text{rank }A+\text{nullity }A=n
$$
