# A pipeline with 3 cycle cache access

Langsommere opslag i lageret påvirker både hentning af instruktioner og hentning af data. Vi antager at [[cache]] tilgang kan [[Pipelines|pipelines]] i tre trin som vi kalder for "Fa","Fb" og "Fc" for instruktionshenting og "Ma", "Mb" og "Mc" for datatilgang.

![[Pasted image 20260119113633.png]]
Betragt her [[Hazards#Lager adgang - structural hazards|data-afhængigheden]] fra load til add via x12.

Her ses udførelsen af et betinget hop:
![[Pasted image 20260119113759.png]]
Prisen er nu 5 clock perioder for et taget hop, stadig en periode for et ikke taget hop.