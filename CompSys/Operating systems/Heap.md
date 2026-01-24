

# Heap
# Definitions
The heap grows from the bottom
Consists of blocks containing a **footer** and a **header**.
Footer, header contains info about the bytes in the block.

Every address is **4 bytes**
Every block **must be divisible by 8**
Header and footer must have same value in block
Every header and footer **must be 4 bytes each** and counts in the size

![[Pasted image 20260119183931.png]]
## Decoding header and footer

Binary representation:
- Bit 0 - Block is free or allocated 
- Bit 1 - Previous block is free or allocated 
- Bit 2 - Always 0

`0x12` $\to$ `00010010`
**Block size** is always found by setting first three bits to zero.
	`00010000 = 16`
	This is why the block size must be a multiple of 8 (probably).
# Examples

## Question 2.1.3 (24-25)

Consider a [[Dynamic memory|memory allocator]] that uses an **implicit free list** and **immediate coalescing of neighbouring free blocks**. The layout of each allocated and free memory block is as follows, with one 32-bit word per row.

Each memory block, either allocated or free, has a size in bytes, rounding up allocations if necessary so that each block is a multiple of 8 bytes. 
Thus, only the 29 higher order bits in the header and footer are needed to record block size, which includes the header and footer. B**locks of size 8 are not allowed (so the minimum size of a block is 16 bytes).**

The usage of the remaining 3 lower order bits is as follows: 
	• Bit 0 indicates the use of the current block: 1 for allocated, 0 for free. 
	• Bit 1 indicates the use of the previous adjacent block: 1 for allocated, 0 for free. 
	• Bit 2 is unused and is always set to be 0

Given the partial contents of the heap shown on the left, show the new contents of the heap after a call `ptr = malloc(12)` is executed (in the middle-left column), followed by a call `free(1164D2CC)` (middle-right column), and finally after a call of `free(ptr)` (rightmost column)

• All addresses and values in memory are hexadecimal, as should be your answers. 
• Note that the address grows from bottom up. 
• Some parts of the heap may lie outside the area shown. 
• Assume that the allocator uses immediate coalescing, that is, adjacent free blocks are merged immediately each time a block is freed. 
• Perform the minimum number of memory changes required.

### Solution
`malloc(12)`
Mallocs 12 bytes. Each header and footer are 4 bytes each.
$$
12+4+4=20
$$
Therefore the size must be $24$ since it must divide by $8$.
Start by finding headers and footers:
![[Pasted image 20260119190341.png]]

Here, we see that the first instance that has space for 24 is the free block of size 40.
We note:
- This block is now occupied - bit 0 must be `1`
- The prev block is occupied - bit 1 must be `1`
- **The following block must also now have a header and footer (but it will be free)**
- Bit 2 must be `0` (**always**)
- Size is 24
- Run `./bin/dtb 24`
	- That is 24 + 3 (`011`)
		- This gives `11011`
	- We run `./bin/bth 11011`
		- This gives `0x1B`
- We write `1B` at slot `0` and `3`

Then we check `free(0x1164D2CC)`
- Set bit 0 i header og footer til 0, for at fri den
- Check for ”**immediate coalescing**”
	- Der kommer 2 frie blocks ved siden af hinanden = immediate coalescing
	- Vi smider derfor de to frie blokke sammen i én
	- Vi opdaterer den nederste fra `0x12` til `0x22`. Da den går fra størrelse 16 til 32. Footers og headers beholder vi i størrelsen. 
	- **The footer that comes after the header must also be updated when this one is freed**

When we run `free(ptr)`, everything in the middle of the heap gets unified into one free block.
![[Pasted image 20260119193625.png]]
![[Pasted image 20260119223407.png]]

## Question 2.1.3 (23-24)

Consider a memory allocator that uses an implicit free list and immediate coalescing of neighbouring free blocks. The layout of each allocated and free memory block is as follows, with one 32-bit word per row
The minimum block size is 2 words.

`free(0xd1c040)`
then `malloc(30)` that returns `0xd1c030`
