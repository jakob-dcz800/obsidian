Fint ord for mere end en instruktion per clock cycle.

[[Cache]] adgang koster meget hardware. Hvis vi har lavet hardware med mulighed for en adgang pr clock, så lad os udnytte det! I gennemsnit er 40% af instruktionerne lagerreferencer. Lad os skalere resten af maskinen så der typisk er brug for cachen hver clock.
## Example
Prerequisites:
- Two-way
- With single cycle cache access

# [[Hazards]]

I en superskalar pipeline er der langt mange mulige "stalls" på grund af [[Hazards#Data hazards|data afhængigheder]]. Betragt flg. afvikling på en 2-vejs [[Superscalar|superskalar]] [[Pipelines|pipeline]]:
![[Pasted image 20260119112804.png]]

Forsinkelsen på en cyklus er den samme som i en simpel pipeline. Men betydningen for ydeevne er relativt større (1,5 instruktion i gennemsnit mod 1,0 for den simple pipeline).

[[Hazards#Løsning|Uafhængig instruktion er brugt her]]

![[Pasted image 20260119112900.png]]

## If in doubt

Jo dybere/bredere pipeline, jo vigtigere er disse teknikker
Over tid har man udviklet forskellige teknikker til at klare hop, kald og retur i lange pipelines - her er tre af dem:
	• "**branch target buffer**" - en lille [[cache]] der associerer en del af adressen på et hop med adressen der hoppes til. 
	• **Retur forudsigelse** - en lillebitte hardware stak (f.eks. 8 addresser) placeret tidligt i pipelinen så man kan få retur adressen uden at vente på at den læses fra registre, endsige [[Forwarding|forwardes]] fra en netop overstået læsning fra lageret. 
	• **Hop forudsigelse** - forudsigelse af om et betinget hop skal tages eller ej baseret på kontekst. Jo dybere/bredere pipeline, jo vigtigere er disse teknikker

## Example 1

Two-way in-order superscalar

![[Pasted image 20260120215539.png]]
Ag: address generation
Needed for storing and loading
Storing needs no writeback

| load        | Fe  | De  | Ag  | Mm  | Wb  |     |
| ----------- | --- | --- | --- | --- | --- | --- |
| store       | Fe  | De  | Ag  | Mm  |     |     |
| ALU         | Fe  | De  | Ex  | Wb  |     |     |
| conditional | Fe  | De  | Ex  |     |     |     |

Line 2 stalls after Fe since it needs Ag
	"They stall because both the store and the load need the single Address Generation (AG) unit, and in a 2-way in-order superscalar pipeline only one memory address can be generated per cycle."
Line 4 stalls since there are two decoders at work

## Example 2