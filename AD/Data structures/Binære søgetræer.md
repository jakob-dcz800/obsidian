# Binære søgetræer 
## Operationer

| Operation        | Køretid | Betydning |
| ---------------- | ------- | --------- |
| `Tree-Insert(x)` | $O(h)$  |           |
| `Tree-Delete(x)` | $O(h)$  |           |
| `Tree-Search(x)` | $O(h)$  |           |
| `Max`            |         |           |
| `Min`            |         |           |
Alle i tid $O(h)$ hvor $h$ er højden på træet, 
$\lg n ≤ h < n$

[[LSM Trees]]

Vi vil gerne have et balanceret træ som har dybde $\log_{2}n$

![[Pasted image 20260403182923.png]]