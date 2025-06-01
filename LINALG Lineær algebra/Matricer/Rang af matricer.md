# Rang af matricer

## Theorem

### 1.3 Rang og løsninger til ligningssystemer
Lad M = $[A|b]$ være den tilsvarende totalmatrix. Da gælder:
1. Hvis rank A < rank M så har (S) **ingen løsninger**
2. Hvis rank A = rank M = n så har (S) netop **én løsning** 
3. Hvis rank A = rank M < n så har (S) **uendeligt mange løsninger**

### 1.5 Kvadratiske ligningssystemer

Ethvert ligningssystem med n ligninger og n ubekendte hvis koefficientmatrix A har rang n har netop én løsning!

![[Lineær uafhængighed#3.4]]
## Definition

Rangen af en matrix $A$ er antallet af ikke-nul-rækker i en echelonform af $A$. 
Rangen betegnes rank $A$.

(Man kan vise, at der altid vil være samme antal ikke-nul-rækker i forskellige echelonformer af A)

### Eksempel

![[Pasted image 20250429181653.png]]

## Facts

• Rangen af en matrix ændres ikke ved elementære [[Rækkeoperationer|rækkeoperationer]]. 
• Lad U være en [[Rækkeechelonform|rækkeechelonform]] af A. Da er rank A lig antallet af pivot-søjler i U (og i A). 
• Lad R være en [[Rækkeechelonform#Reduceret rækkeechelonform|reduceret rækkeechelonform]] af A. Da er rank A lig antallet af ledende 1-taller i R. 
• Lad A være en m × n matrix. Da er rank A ≤ min(m, n).

[[Homogene ligningssystemer]]
