# Quicksort
Quicksort is an efficient, general-purpose sorting algorithm.

>[!IMPORTANT] In-place sorting
>Unlike [[Mergesort|merge-sort]], quicksort sorts _in place_, meaning that it requires only $O(1)$ words of memory in addition to the memory for the input list.
>
>Quicksort has worst case running time $\Theta(n^{2})$

Quicksort is a [[divide and conquer|divide-and-conquer]] algorithm. It works by selecting a "pivot" element from the array and partitioning the other elements into two sub-arrays, according to whether they are less than or greater than the pivot.


![[Pasted image 20260125001004.png]]

## Code

![[Pasted image 20260125001108.png]]![[Pasted image 20260125001046.png]]

> Antal elementer der skal sorteres: $n = r − p + 1$