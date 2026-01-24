# 1.1

## 1.1.1

![[Pasted image 20260108184705.png]]

- bits in address: 32
- 2 lists and 8 kibibytes of sets
- lists are 16 bytes (block size)
- LRU replacement

![[Pasted image 20260108184841.png]]

$$
\begin{align}
S & = \log_{2}\left( \frac{8192}{2\cdot 16} \right) =
\log_{2}(265)=8
 \\ \\

B & = \log_{2}(16)=4 \\
 \\
T & = 32-(4+8)=20 
\end{align}
$$

Order is:

| Address fragment | tag | set index | block offset |
| ---------------- | --- | --------- | ------------ |
| Bit size         | 20  | 8         | 4            |
## 1.1.2

![[Pasted image 20260108185937.png]]

First into bits:
0111 0110 0101 0100 0011 0010 0001 0000
- $B=0000 = 0x0$
- $S=00100001 = 0x21$
- $t=01110110010101000011 = 0x76543$

01110110010101000011001000010000


![[Cache#Address structure]]
