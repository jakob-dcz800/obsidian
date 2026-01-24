# UDP

The crude version
Basically the same as sending a letter
- Unreliable: Garanterer hverken rækkefølgen af pakker eller om de overhovedet kommer. 
- Connectionless: UDP opsætter ikke en connection som TCP, hver pakke sendes uafhængigt. 
- Low overhead/fast speed: UDP header er kun 8 bytes ([[#TCP]] er 20). Dette plus at det ikke kræver handshake, gør UDP en del hurtigere end TCP. 

![[Pasted image 20260120121957.png]]

![[Pasted image 20260120121734.png]]