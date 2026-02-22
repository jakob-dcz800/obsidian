# Regnskabsmetoden

>Teknik til at holde styr på [[Amortized analysis|amortiserede]] omkostninger


Idé: Vi lægger “penge” til side og knytter vi dem til elementer i datastrukturen
Eksempel: [[Binary counter|Binær tæller]]

• Hver bit der er sat til 1 har $1 
• "Betaler selv" $1 for at blive ændret til 0 
• Omkostning per operation er $2 fordi én bit skal ændres fra 0 til 1 og have $1 tilknyttet

## Omkostning for binær tæller

![[Pasted image 20260211161156.png]]