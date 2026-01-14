---
tags:
  - Math
  - Matrices
  - LINALG
---
# Gauss elimination

• **Enhver** [[LINALG/Matricer/Matricer|matrix]] kan bringes på rækkeechelonform vha. elementære [[Rækkeoperationer|rækkeoperationer]]. 
• Processen “[[Forward reduction|forward reduction]]” kaldes for **Gauss-elimination**. 
• Gauss-elimination kan foretages på forskellige måder ved at anvende forskellige [[Rækkeechelonform#Pivotelement|pivotelementer]] og rækkeoperationer. 
• Resultatet afhænger bl.a. af hvilke rækkeoperationer der er brugt. Der er forskellige [[Rækkeechelonform|rækkeechelonformer]] for en given matrix.

## Backward reduction

Lad $U$ være på rækkeechelonform.

1. Vælg den pivotsøjle, der står længst til højre i $U$. Gang pivotrækken igennem med et tal, så pivotelementet får værdien 1. Skaf derefter 0 på alle pladser i pivotsøjlen over pivotelementet ved at bruge rækkeoperationer.
2. Gentag processen ovenfor for hver pivotsøjle i U (idet man går mod venstre). Stop når der ikke er flere pivotsøjler.

### Eksempel
![[Pasted image 20250429181136.png]]

## Gauss-Jordan elimination
Processen at foretage forward og dernæst backward reduction på en matrix kaldes Gauss-Jordan elimination.
### Sætning
• Antag, at A ved elementære rækkeoperationer omformes til A′ , hvor A′ er på reduceret rækkeechelonform. 
• Antag, at A ved elementære rækkeoperationer omformes til A′′ , hvor også A′′ er på reduceret rækkeechelonform. 
• **Da gælder A ′ = A ′′**

![[Pasted image 20250429181521.png]]

