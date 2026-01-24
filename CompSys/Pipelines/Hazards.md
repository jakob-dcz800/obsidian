# Data hazards

Vi vil tilstræbe at hver instruktion kan bruge resultatet af den umiddelbart forudgående instruktion. Det er vi vant til fra vore single-cycle maskine. Det er bare ikke så nemt:

En triviel løsning er at bremse pipelinen for de senere instruktioner indtil det er sikkert at fortsætte. Det kaldes et "stall".

![[Pasted image 20260119111608.png]]

## Løsning
Compileren må indsætte instruktioner der er uafhængige!
- bruges ikke rigtig til opgaver
## Hardware løsning
Vi tilføjer dedikerede forbindelser fra resultat-siden af ALUen til der hvor værdierne skal bruges.

Det kaldes "bypassing" eller "[[forwarding]]". Det vil koste lidt på clockfrekvensen i forhold til hvis man ikke har bypassing. Men gevinsten er stor.

![[Pasted image 20260119111841.png]]
# Structural hazards

Det bliver ret besværligt, hvis samme hardware stump skal bruges fra flere forskellige trin i pipelinen. Så skal man koordinere brugen. Det kaldes en "structural hazard".

Moderne maskiner har separat instruktions- og datacache blandt andet for at undgå at skulle koordinere tilgang til en enkelt meget hyppigt brugt lager- klods.

## Lager adgang - structural hazards
Vi har potentielt to instruktioner pr clock men kun en mulig tilgang til datacachen per clock. Så hvis de to instruktioner der hentes samtidigt begge skal tilgå lageret, så må vi stalle den ene:

![[Pasted image 20260119112609.png]]
## Langsommere instruktioner

Det er ikke alle instruktioner der udføres i et enkelt trin - kun de aritmetisk/ logiske (**dog IKKE multiplikation**).

Læsning fra lageret har først et resultat efter 'Me' trinnet:
![[Pasted image 20260119112218.png]]
Vi siger at load-instruktionen har en "skygge" på en instruktion. Hvis vi kan finde en uafhængig instruktion at placere i skyggen behøver vi ikke at bremse pipelinen.