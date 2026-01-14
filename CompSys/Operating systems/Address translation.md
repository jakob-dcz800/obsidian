
You are expected to perform address translation
[watch video](https://sid.erda.dk/share_redirect/HmziebsZol/09_00_address_translation_hit_example.mp4)
Consult [[CompSys/Hardware/Memory hierarchy|cache]]
# Basic parameters

$N = 2^n$: Number of addresses in virtual address space
$M = 2^m$: Number of addresses in physical address space
$P = 2^p$: Page size (bytes)
# Components of the virtual address

**VA**: Virtual address
**TLB**: [[Address translation#Translation lookaside buffer|Translation lookaside buffer]]
**TLBI**: TLB index 
**TLBT**: TLB tag 
**VPO**: Virtual page offset 
**VPN**: Virtual page number
# Components of the physical address

**PPO**: Physical page offset (same as VPO) 
**PPN**: Physical page number

**PTEA**: Page table entry address
**PTE** Page table entry
**PA**: Physical address

# Address translation

## Address Translation With a Page Table

![[Pasted image 20250928211818.png]]

The [[Page table|page table]] is individual for each process. It exists in memory/[[CompSys/Hardware/Memory hierarchy]] (hopefully L1).
It defines the virtual memory space

## Address Translation: Page Hit

![[Pasted image 20250928212426.png]]

## Address Translation: Page Fault

![[Pasted image 20250928212452.png]]

The exception writes page to memory and the process starts over. 
## Integrating VM and Cache

![[Pasted image 20250928212517.png]]

## Translation lookaside buffer

**TLB**

[[Page table|Page table]] entries (PTEs) are cached in L1 like any other memory word.
PTEs may be evicted by other data references
PTE hit still requires a small L1 delay

Solution: Translation Lookaside Buffer (TLB)
Small set-associative **hardware** cache in [[MMU]]
Maps virtual page numbers to physical page numbers
Contains complete page table entries for small number of pages

Has the same structure as the [[CompSys/Hardware/Memory hierarchy]]

![[Pasted image 20250928213438.png]]

