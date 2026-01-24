Let $A$ be the event that it rains tomorrow, and suppose that $P(A)=0.33.$ 
Also suppose that I toss a fair coin; 
let $B$ be the event that it lands heads up. 
We have $P(B)=0.5$. 
Now I ask you, what is $P(A|B)$? 
$$
P(A|B) = P(A) = 0.33 
$$
This is an example of two independent events

## Definition

![[Pasted image 20251006164855.png]]
![[Pasted image 20251006164929.png]]

## Example

I pick a [[Random variables|random number]] from {1,2,3,⋯,10} and call it N. Suppose that all outcomes are equally likely. Let A be the event that N is less than 7, and let B be the event that N is an even number. Are A and B independent?

---

#### Step 1: Define the sample space


$S = \set{1,2,3,4,5,6,7,8,9,10}$   
Each outcome is equally likely, so  

$P(\text{any specific number}) = \frac{1}{10}.$  

---

### Step 2: Define the events

**Event A:** ( $N < 7$ )  
$A = {1,2,3,4,5,6}$
$P(A) = \frac{6}{10} = \frac{3}{5}$

**Event B:** ( N ) is even  
$B = {2,4,6,8,10}$  
$P(B) = \frac{5}{10} = \frac{1}{2}$
### Step 3: Find ( $A \cap B$ )

$( A \cap B )$ means ( $N$ ) is both less than 7 **and** even:  
$A \cap B = {2,4,6}$

So  
$P(A \cap B) = \frac{3}{10}$

---

### Step 4: Check independence

Events (A) and (B) are **independent** if and only if  
$P(A \cap B) = P(A) \times P(B)$

Compute:  
$P(A) \times P(B) = \frac{3}{5} \times \frac{1}{2} = \frac{3}{10}$

---

### Step 5: Compare

$P(A \cap B) = \frac{3}{10}, \quad P(A)P(B) = \frac{3}{10}$

They are **equal**.

---

✅ **Conclusion:**  
Events $A(N < 7)$ and $B(N\text{ is even})$ **are independent**.