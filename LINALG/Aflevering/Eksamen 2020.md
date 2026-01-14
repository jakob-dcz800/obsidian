---
tags:
  - Assignment
---
# 1

## a

$$
\left[
\begin{array}{ccc|c}
1 & 2 & a & 1 \\
0 & 1 & 2a & a \\
2 & -1 & 4 & -a
\end{array}
\right]
$$
Vi bringer på [[Rækkeechelonform]]:
$$
\left[
\begin{array}{ccc|c}
1 & 2 & a & 1 \\
0 & 1 & 2a & a \\
2 & -1 & 4 & -a
\end{array}
\right]
\xrightarrow[]{
\begin{matrix}
-2r_{1}\to r_{3} \\
5r_{2}\to r_{3}
\end{matrix}
}
\left[
\begin{array}{ccc|c}
1 & 2 & a & 1 \\
0 & 1 & 2a & a \\
0 & 0 & 4+8a & 4a-2
\end{array}
\right]
$$
Hvis $4+8a=0$ så så er $a=-½$. I så fald er rangen af den reducerede matrix mindre end antal søjler. Og der er nul løsninger. For alle andre værdier af $a$ er rangen af totalmatricen lig antallet af søjler. og der er én løsning. Det er ikke muligt at have uendeligt løsninger.

## b

$$
\left[
\begin{array}{ccc|c}
1 & 2 & -½ & 1 \\
0 & 1 & -1 & -½ \\
2 & -1 & 4 & ½
\end{array}
\right]
$$
$$
\begin{bmatrix}
1 & 2 & -½ \\
0 & 1 & -1 \\
2 & -1 & 4
\end{bmatrix}
\begin{bmatrix}
1 & 2 & -½ \\
0 & 1 & -1 \\
2 & -1 & 4
\end{bmatrix}
=
\begin{bmatrix}
0 & 9/2 & -9/2 \\
-2 & 2 & -5 \\
10 & -1 & 16
\end{bmatrix}
$$
$$
\left[
\begin{array}{ccc|c}
0 & 9/2 & -9/2  & 3\\
-2 & 2 & -5  & 1\\
10 & -1 & 16 & 1
\end{array}
\right]
\xrightarrow[]{
\begin{matrix}
r_{1}\leftrightarrow r_{3} \\
5r_{1}\to r_{2} \\
-1/2 r_{2}\to r_{3} \\
1/3
\end{matrix}
}
\left[
\begin{array}{ccc|c}
-1 & 1 & -5/2  & 1/2 \\
0 & 1 & -1 & 2/3 \\
0 & 0 & 0  & 0\\
\end{array}
\right]
$$
![[Pasted image 20250616123843.png]]

# 2 
## a

![[Pasted image 20250616123928.png]]
## b

![[Pasted image 20250616123941.png]]
## c

![[Pasted image 20250616123954.png]]