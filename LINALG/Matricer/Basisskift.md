---
tags:
  - Matrices
  - LINALG
---
# Basisskift



![[Pasted image 20250506212703.png]]

Forklaring:

Vi har et underrum $\mathcal{U}$ og tager to forskellige baser $\mathcal{C}, \mathcal{B}$
De har begge $k$ vektorer
Vi laver så en særlig [[LINALG/Matricer/Matricer|matrice]] (basisskift matricen) $\mathbf{P}_{\mathcal{B}\gets\mathcal{C}}$

"P fra C til B" med k søjler
Første søjle i P er første [[Baser|basisvektors]] [[Koordinater]] i C med henhold til base B

Matricen er interessant fordi:
Hvis vi tager en vilkårlig vektor $\mathbf{v}$ i underrumet $\mathcal{U}$, tager dens koordinater i henhold til $\mathcal{C}$ og ganger med matricen $\mathbf{P}$, får vi vektorens koordinater iht. basen $\mathcal{B}$
Vi går altså fra C til B

## Eksempel

### 1
![[Pasted image 20250616113153.png]]
![[Pasted image 20250616113209.png]]
![[Pasted image 20250616113222.png]]

# Den inverse til basisskiftmatricen

![[Pasted image 20250616113433.png]]

![[Pasted image 20250616113446.png]]

