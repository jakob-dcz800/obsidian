---
tags:
  - Hardware
  - OS
---

You are expected to perform address translation
[watch video](https://sid.erda.dk/share_redirect/HmziebsZol/09_00_address_translation_hit_example.mp4)
Consult [[Cache|cache]]
# Basic parameters

$N = 2^n$: Number of addresses in virtual address space
$M = 2^m$: Number of addresses in physical address space
$P = 2^p$: Page size (bytes)
## Components of the virtual address

**VA**: Virtual address
**TLB**: [[Address translation#Translation lookaside buffer|Translation lookaside buffer]]
**TLBI**: TLB index 
**TLBT**: TLB tag 
**VPO**: Virtual page offset 
**VPN**: Virtual page number
## Components of the physical address

**PPO**: Physical page offset (same as VPO) 
**PPN**: Physical page number

**PTEA**: Page table entry address
**PTE** Page table entry
**PA**: Physical address

# Address translation

## Process
1) take the first log2(pagesize)=6 bits from the VA - this is the page offset
2) VPN is the rest
3) the first log2(no. sets)=2 bits are the TLB index
4) the last are the TLB tag
5) lookup in the TLB - if hit, then no page fault and return the PA: (PPN | VPO)
6) if no hit, go to page table, find VPN and if PTE is valid, return (PPN | VPO)
7) if PTE not valid, then there is a page fault

### Scaffold:
Virtual address: ` ` = ` `
	Offset bits: $\log_{2}(\text{page size}) = \log_{2}(64)=6$ (*change*)
VPO page offset (first log2(xx)): ` ` = ` `
VPN (rest) = ` ` = ` `
	TLB index bits: $\log_{2}(\text{sets}) = \log_{2}(4)=2$ (*change*)
TLB set index: ` `  = ` `
TLB tag (rest):  ` ` =  ` `
TLB hit? __
Page fault? __

PA = PPN | VPO: `  |  ` = ` `
## Address Translation With a Page Table

![[Pasted image 20250928211818.png]]

The [[Page table|page table]] is individual for each process. It exists in [[CompSys/Hardware/Memory hierarchy|memory]] (hopefully L1).
It defines the [[virtual memory]] space

## Address Translation: Page Hit

![[Pasted image 20250928212426.png]]

## Address Translation: Page Fault

![[Pasted image 20250928212452.png]]

The exception writes page to memory and the process starts over. 
## Integrating VM and Cache

![[Pasted image 20250928212517.png]]

## Translation lookaside buffer
%% [[Page table|Page table]] entries (PTEs) are cached in L1 like any other memory word.
PTEs may be evicted by other data references
PTE hit still requires a small L1 delay %%

Translation Lookaside Buffer (**TLB**)
Small set-associative hardware [[cache]] in [[MMU]]
Maps virtual page numbers (**VPN**) to physical page numbers (**PPN**)
Contains complete page table entries for small number of pages

[[#Components of the virtual address]]
Has the same structure as the [[CompSys/Hardware/Memory hierarchy|Memory hierarchy]]
![[Pasted image 20250928213438.png]]

# Example

- Memory is byte-addressed (meaning that the values are in hexadecimal)
- VA are 15 bits wide
- PA are 13 bits wide
- Page size is 128 bytes
- The TLB is 3-way set associative with 4 sets and 16 total entries - it has contents:
![[Pasted image 20260120104620.png]]

- Page table looks like this:
![[Pasted image 20260120104652.png]]

#### Find:
Virtual address is `0xef2`
- VA bits [14:0]
	`111011110010`
	As this is only 12 bit, add 0’s for the higher bits to fill the 15 bits.
- Page offset: 
	- $\log_2(\text{page Size}) = \log_2(128) = 7$
	- Then we know that the page offset is the 7 lowest bits of the VA
	- 00011101**11100101110010** is the page offset
- VPN:
	- Remaining bits of VA (Not In Page offset) **00011101**111001000011101 is the VPN
	- Convert to hex: `0x1d`
- TLB index:
	- $\log_{2}(\text{sets})=\log_2(4)=2$
	- Now we know that the TLB index is the 2 lowest bit of the VPN.
	- 000111**01** - Convert to hex: `0x1`
- TLB tag:
	- TLB Tag: Remaining bits in the VPN (Not In TLB Index)
	- **000111**01 - Convert to hex: `0x7`
- TLB Hit?
	- Our TLB index is `0x1` so we check set `0x1`
	- If there exists an entry for TLB Tag `0x7` with valid = 1. 
	- In this case there is so we have a **TLB hit**.
		- If we have a valid TLB hit, it follows that there is **no page fault**.
	- The Physical page number (PPN) can be found in the TLB entry: `0x12`
- PA
	- To find the physical address we concatenate: 
	- PA = *PPN* | *Page Offset* 
	- *0001 0010* | *111 0010* = 000 1001 0111 0010. 
	- If too large due to 0’s simply remove 0’s to fit.

| Parameter      | Value  |
| -------------- | ------ |
| VPN            | `0x1d` |
| TLB index      | `0x1`  |
| TLB tag        | `0x7`  |
| TLB hit Y/N    | Y      |
| Page fault Y/N | N      |
| PPN            | `0x12` |
- Bits of PA (if any)

**Page hit**: 
You don’t have a valid TLB hit, you **check the page table for a valid entry** for your VPN. 
If there is a valid entry you find the PA in the same way as shown on the previous slide:
	PPN | Page Offset. 
This of course also means that there is no page fault.

**Page fault**: 
You neither have a valid TLB hit or valid Page table hit, then you have a page fault. 
Here there is **no physical address**.