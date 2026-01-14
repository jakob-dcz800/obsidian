A page table is an array of page table entries (PTEs) that maps [[Addressing#Virtual addressing|virtual]] pages to [[Addressing#Physical addressing|physical]] pages.
- Per-process kernel data structure in [[Hardware terms#DRAM|DRAM]]

![[Pasted image 20250928182007.png]]
	Pages also exist on the [[Hardware terms#Disk|disk]], but are fetched from DRAM to lower locality.

## Multi-Level Page Tables

Problem: the page table would have to be extremely large to hold all the [[Address translation#Components of the physical address|PTE]]'s.
Common solution: Multi-level page table

Example: 2-level page table
- Level 1 table: each PTE points to a [[Page table|page table]] (always memory resident)
- Level 2 table: each PTE points to a page (paged in and out like any other data)
![[Pasted image 20250928215112.png]]

