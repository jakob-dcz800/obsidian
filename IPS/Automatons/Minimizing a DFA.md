# Minimizing a DFA

## Process

1. Group accepting and non-accepting states.
2. For each group:
	1. Note for each character in the alphabet ($\sum$) which group the outward arrow points to.
	2. All states in the group must point to the same pairs of groups
	3. Otherwise split the group into new groups and repeat the process for each group until all groups are homogenous.
3. Note each group and its members.

> [!QUESTION] Question
> How do i pre-process the DFA by making [[DFA#Move|the move function]]  total?

>[!DEFINITION] Total move function
> The `move` function is total when there are transitions on all symbols from all states *or* when there are no [[DFA#Dead states|dead states]] in the [[DFA]].
> Dead states might make a group *inconsistent*, when in fact it is not
> >[!IMPORTANT] Remove dead states
> >It is important to remove dead states - and you can simply remove them intirely.


## Example 1 - Dead state

![[Pasted image 20260611165521.png|637]]

Here, see that 4 is a dead state.
You *could* simply remove it, but the task requires us to not do so.

```
Accepting states
G1 = { 1 }
Non-accepting states
G2 = { 2, 3, 4, 5, 6 }
```

---

| ✅ G1 | a   | b   | c   |
| ---- | --- | --- | --- |
| 1    | G2  | G2  | G2  |

| ✅ G6 | a   | b   | c   |
| ---- | --- | --- | --- |
| 6    | -   | -   | G1  |

| ✅ G5 | a   | b   | c   |
| ---- | --- | --- | --- |
| 5    | G5  | G6  | G4  |

| ✅ G4 | a   | b   | c   |
| ---- | --- | --- | --- |
| 4    | G4  | -   | -   |

| ✅ G7 | a   | b   | c   |
| ---- | --- | --- | --- |
| 3    | G4  | G4  | -   |

| ✅ G8 | a   | b   | c   |
| ---- | --- | --- | --- |
| 2    | G5  | G6  | -   |

---

| ❌ G3 | a   | b   | c   |
| ---- | --- | --- | --- |
| 3    | G4  | G4  | -   |
| 2    | G5  | G6  | -   |

| ❌ G2 | a   | b   | c   |
| ---- | --- | --- | --- |
| 2    | G2  | G2  | -   |
| 3    | G2  | G2  | -   |
| 4    | G2  | -   | -   |
| 5    | G2  | G2  | G2  |
| 6    | -   | -   | G1  |

---

| Group | Members | a   | b   | c   |
| ----- | ------- | --- | --- | --- |
| 1     | { 1 }   | 2   | 2   | 2   |
| 4     | { 4 }   | 4   | -   | -   |
| 5     | { 5 }   | 5   | 6   | 4   |
| 6     | { 6 }   | -   | -   | 1   |
| 7     | { 3 }   | 4   | 4   | -   |
| 8     | { 2 }   | 5   | 6   | -   |

## Example 2
![[Pasted image 20260611162930.png|377]]

```
Accepting states
G1 = { 3 }
Non-Accepting states
G2 = { 1, 2, 4, 5, 6, 7, 8 }

G1 | 0  | 1  |
---+----+----|
3  | G2 | G2 |


G2 | 0  | 1  |
---+----+----|
1  | G2 | G2 |
2  | G2 | G1 |
4  | G1 | G2 |
5  | G2 | G2 |
6  | G1 | G2 |
7  | G2 | G2 |
8  | G2 | G1 |
G2 is Not consistent

G1 = { 3 }
G3 = { 1, 5, 7 }    --2, 2
G4 = { 4, 6 }       --1, 2
G5 = { 2, 8 }       --2, 1

We pick G3 for consideration

G3 | 0  | 1  |
---+----+----|
1  | G4 | G4 |
5  | G4 | G4 |
7  | G3 | G3 |
G3 is Not consistent


G1 = { 3 }      -m
G4 = { 4, 6 }   -m
G5 = { 2, 8 }   -m
G6 = { 1, 5 }   -m    
G7 = { 7 }      -m

We pick G4 for consideration

G4 | 0  | 1  |
---+----+----|
4  | G1 | G7 |
6  | G1 | G7 |
G4 is consistent, and we pick G5

G5 | 0  | 1  |
---+----+----|
2  | G7 | G1 |
8  | G7 | G1 |
G5 is consistent, and we pick G6

G6 | 0  | 1  |
---+----+----|
1  | G5 | G4 |
5  | G5 | G4 |
G6 is consistent

Thus, we have the groups:

G1 = { 3 }
G4 = { 4, 6 }
G5 = { 2, 8 }
G6 = { 1, 5 }    
G7 = { 7 }
```