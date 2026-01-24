**Klassiske instruktioner:**
Pipelining går ud på at arrangere udførelsen af instruktioner som et samlebånd. Den klassiske pipeline som man ofte ser i lærebøgerne har 5 trin:

• 'Fe' for "fetch" - hentning af instruktion 
• 'De' for "decode" - afkodning 
• 'Ex' for "execute" - udførelse (ALU) 
• 'Me' for "memory" - læsning fra lageret 
• 'Wb' for "writeback" - opdatering af registre

Ovenstående elementer findes også i en single-cycle mikroarkitektur

![[Pasted image 20260119110950.png]]
## Example 1

Prerequisites:
- [[In-order machines|in-order machine]]
- 5 stage
- [[Forwarding|full forwarding]] (we don't wait for writeback (`Wb`) to use the value from an execute step `Ex`)

![[Pasted image 20260118211046.png]]

> See that line 6 is offset by 1
> This is because of [[Forwarding|full forwarding]] where the result from `Ex` is bypassed

## Pipeline registre

Simpel fem-trins pipeline (uden bypass/forwarding)
![[Pasted image 20260119111035.png]]
Bemærk hvordan der er indskudt registre (såkaldte pipeline-registre) foran afkoderen, ALUen, data-cachen og til sidst, før skrivning til registrene.

De blå felter er midlertidige registre som holder værdier imellem skridtene.

## RISC-V

[[RISC-V]] er designet til at lette pipelinede implementationer 
	• Instruktioner har samme længde 
	• Hver instruktion bruger kun en resource (e.g. adder, datacache) en gang

