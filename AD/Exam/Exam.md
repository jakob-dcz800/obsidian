# Råd omkring forberedelse til eksamen

Eksamen skal teste opfyldelse af målene i [[Algoritmer og datastrukturer|kursusbeskrivelsen]]. 
- Kan du løse en rekursionsligning? 
- Kan du håndkøre en algoritme? 
- Kan du analysere køretiden for en algoritme? 
- Kan du lave et induktionsbevis for korrekthed? 
- Kan du ræsonnere om amortiserede køretider ved hjælp af potentialfunktioner? 
- Kender du invarianterne for kursets datastrukturer? 
- Kan du løse et nyt algoritmisk problem ved at modificere en algoritme, I har set i kurset? 
- Kender du begreberne, der er brugt i analyserne af kursets algoritmer? 

## Multiple-choice opgaver

Et typisk multiple-choice spørgsmål er formuleret således at det bør tage ca. 4% af eksamenstiden at svare på, og procenten er angivet ved opgaven. Et helt korrekt svar vil derfor give 4 point mens intet svar vil give 0 point. 
Hvis man svarer forkert (fx hvis man gætter) er der risiko for **negative point** da de korrekte svar samlet giver 4 point mens de ukorrekte svar samlet giver -4 point. Eksempler for en opgave på 4%:

- Opgave X har 8 svarmuligheder, hvoraf 4 er korrekte. Hvert kryds ved en korrekt svarmulighed giver 1 point, og hvert kryds ved en forkert svarmulighed giver -1 point. Hvis du fx sætter kryds ved alle de korrekte svarmuligheder og én forkert svarmulighed får du 3 point. Hvis du ikke sætter nogen krydser får du 0 point, og sætter du krydser ved alle svarmuligheder får du også 0 point.
- Opgave Y har 3 svarmuligheder, hvoraf 1 er korrekt. Kryds ved den korrekte svarmulighed giver 4 point, og kryds ved en forkert svarmulighed giver -2 point. Sætter du fx kryds ved én svarmulighed, og den er forkert, giver opgaven totalt -2 point.

Generelt for en opgave med $p\%$: Lad $m$ være antallet af alle mulige svar og $k$ antallet af korrekte svar. Antallet af forkerte svar er så $f=m-k$. Hvert korrekt svar giver $\frac{p}{k}$ point og hvert forkert svar giver $-\frac{p}{f}$ point. Intet svar giver derfor altid $0$ point og man får også $0$ point ved at sætte kryds ved alle svar.
