# 26

## 2.2.1


### 1
Virtual address: `0x1234` = `001001000110100`
	Offset bits: $\log_{2}(\text{page size}) = \log_{2}(64)=6$
VPO page offset (first 6): `110100` = `0x34`
VPN (rest) = `0001001000` = `0x48`
	TLB index bits: $\log_{2}(\text{sets}) = \log_{2}(4)=2$:
TLB set index: 00  = `0x0`
TLB tag (rest):   =  `0x12`
TLB hit? **n**
Page fault? **y**

### 2
Virtual address: `0x2282` = `010001010000010`
	Offset bits: $\log_{2}(\text{page size}) = \log_{2}(64)=6$
VPO page offset (first 6): `000010` = `0x2`
VPN (rest) = `0010001010` = `0x8a`
	TLB index bits: $\log_{2}(\text{sets}) = \log_{2}(4)=2$:
TLB set index:   = `0x2`
TLB tag (rest):   =  `0x22`
TLB hit? **n**
Page fault? **y**
PPN: `0x44` = `01000100`
PA: `PPN | VPO = 001000100000010`

![[Pasted image 20260121095900.png]]
### 3
Virtual address: `0x1f40` = `001111101000000`
	Offset bits: $\log_{2}(\text{page size}) = \log_{2}(64)=6$
VPO page offset (first 6): `000000` = `0x0`
VPN (rest) = `0001111101` = `0x7d`
	TLB index bits: $\log_{2}(\text{sets}) = \log_{2}(4)=2$:
TLB set index:   = `0x1`
TLB tag (rest):   =  `0x1F`
TLB hit? **Y**
Page fault? **N**
PA: `PPN | VPO = 00101100000000`
# 22/23

## 3.2
![[Pasted image 20260120164323.png]]

The window size must be of size 3.
Three packages are sent in quick succession. After, there is a wait for ACK

# 24/25

## 2.2.1

![[Pasted image 20260120193509.png]]

• Memory is byte-addressed. 
• Virtual addresses are 15 bits wide. 
• Physical addresses are 14 bits wide. 
• The page size is 64 bytes. 
• The TLB is 3-way set associative with 4 sets and 12 total entries.

### 1
Virtual address: `0x0513` = `000010100010011`
	Offset bits: $\log_{2}(\text{page size}) = \log_{2}(64)=6$
VPO page offset (first 6): `010011` = `0x13`
VPN (rest) = `0000010100` = `0x14`
	TLB index bits: $\log_{2}(\text{sets}) = \log_{2}(4)=2$:
TLB set index:   = `0x0`
TLB tag (rest):   =  `0x5`
TLB hit? **N**
PTE hit? **N**
Page fault? **Y**
PA = PPN | VPO: `  |  ` = ` `

### 2
Virtual address: `0x0A13` = `000101000010011`
	Offset bits: $\log_{2}(\text{page size}) = \log_{2}(64)=6$
VPO page offset (first 6): `010011` = `0x13`
VPN (rest) = `0000101000` = `0x28`
	TLB index bits: $\log_{2}(\text{sets}) = \log_{2}(4)=2$:
TLB set index:   = `0x0`
TLB tag (rest):   =  `0xA`
TLB hit? **Y**
Page fault? **N**
PA = PPN | VPO: `0x05 | 010011 ` = `00000101010011`

### 2
Virtual address: `0x71` = `000000001110001`
	Offset bits: $\log_{2}(\text{page size}) = \log_{2}(64)=6$
VPO page offset (first 6): `110001` = `0x31`
VPN (rest) = `000000001` = `0x1`
	TLB index bits: $\log_{2}(\text{sets}) = \log_{2}(4)=2$:
TLB set index:   = `0x1`
TLB tag (rest):   =  `0x0`
TLB hit? **N**
Page fault? **Y**
# 23/24

## 2.2.2

[[Address translation]]

![[Pasted image 20260120152710.png]]
• Memory is byte-addressed. 
• Virtual addresses are 15 bits wide. 
• Physical addresses are 13 bits wide. 
• The page size is 128 bytes. 
• The TLB is 3-way set associative with 4 sets and 16 total entries.

### 1
Virtual address: `0xef2` = `111011110010`
	Offset bits: $\log_{2}(\text{page size}) = \log_{2}(128)=7$
VPO page offset (first 7): `1110010` = `0x72`
VPN (rest) = `11101` = `0x1d`
	TLB index bits: $\log_{2}(\text{sets}) = \log_{2}(4)=2$:
TLB set index: 111**01** = `0x1`
TLB tag (rest): **111**01 =  `0x7`
TLB hit? Y
PA = PPN | VPO: `0x12 | 0x72` = `0001001001110010`

### 2
Virtual address: `0x8f` = `00010001111`
	Offset bits: $\log_{2}(\text{page size}) = \log_{2}(128)=7$
VPO page offset (first 7): `0001111` = `0xf`
VPN (rest) = `00001` = `0x1`
	TLB index bits: $\log_{2}(\text{sets}) = \log_{2}(4)=2$:
TLB set index: 000**01** = `0x1`
TLB tag (rest): **000**01 =  `0x0`
TLB hit? **N**
Page fault? **N**
PA = PPN | VPO: `0x33 | 0xf` = `001100110001111`

### 3
Virtual address: `0x1af` = `000110101111`
	Offset bits: $\log_{2}(\text{page size}) = \log_{2}(128)=7$
VPO page offset (first 7): `0101111` = `0x2f`
VPN (rest) = `00011` = `0x3`
	TLB index bits: $\log_{2}(\text{sets}) = \log_{2}(4)=2$:
TLB set index: 000**11** = `0x3`
TLB tag (rest): **000**11 =  `0x0`
TLB hit? **N**
Page fault? **Y**



## 2.3.1

Each memory block, either allocated or free, has a size that is a **multiple of eight bytes**, rounding up allocations if necessary. 
Thus, only the 29 higher order bits in the header and footer are needed to record block size, which includes the header and footer. The minimum block size is 8. 

Given the partial contents of the heap shown on the left, show the new contents of the heap after a call to `malloc(8)` is executed that returns `0xd1c008` (in the middle column), followed by a call `free(0xd1c028)` (rightmost column)

### Solution
First, we draw the existing heap. What is free and what's taken?

We run `malloc(8)` that returns `0xd1c008`
We have allocated **8 bytes**. In each row there can be **4 bytes** ($32/8=4$)
The data thus fills 2 blocks ($8 /4=2$).
The new block is 4 blocks long (ftr. and hdr. incl.).
We calculate the size in binary.
First convert to number of bytes $4\cdot 4=16$: `10000`

The prev is taken, as well as this one. Add `011 + 10000 = 10011`: `0x13`
The block after is updated.

Then we run `free(0xd1c028)`
Top is 64, next is 32 last is 16.
It's free and the previous is taken.
64+32+16 = 112 (`1110000`) --> `1110010`
# 23/24

## 2.2.2

![[Pasted image 20260120110917.png]]
• Memory is byte-addressed. 
• Virtual addresses are 12 bits wide. 
• Physical addresses are 14 bits wide. 
• The page size is 64 bytes. 
• The TLB is 3-way set associative with 4 sets and 12 total entries.

### 1

VA: `0x032B` = `0000001100101011`
$\log_{2}(\text{page size}) = \log_{2}(64)=6$
aka. 0000001100**101011** - Page offset = `101011`: `0x2b`
VPN: 0000001100 aka the rest = `0xc`
TLB index bits: $\log_{2}(\text{sets}) = \log_{2}(4)=2$:
	TLB index = 00000011**00** = `0x0`
TLB tag bits: remaining bits:
	00000011 = `0x3`
Check set `0` with tag `0x3` - **no tag exists**: 
	TLB HIT: NO
We then check the page table.
	There is a valid set with PPN: `0x02`
Add together: 
	`0x02 | page offset`
	`00000010 | 101011 = 00000010101011` (max 14 bits)
[[Address translation]]
(**PTE** Page table entry)

![[Pasted image 20260120112416.png]]

### 2

Virtual address: `0x0D06` = `0000110100000110`
offset bits: $\log_{2}(\text{page size}) = \log_{2}(64)=6$
VPO page offset (first 6) = `000110` = `0x6`
VPN (rest) = `0000110100` = `0x34`
TLB index bits: $\log_{2}(\text{sets}) = \log_{2}(4)=2$:
TLB index:       00001101**00** = `0x0`
TLB tag (rest): **00001101**00 =  `0xd`

**TLB hit: N**
**Page fault: Y**

### 3
VA: `0x0082` = `0000000010.000010` 
VPO Page offset: `000010` = `0x2`
VPN: `0000000010` = `0x2`
TLB index: `10` = `0x2`
TLB tag: `00000000` = `0x0`
TLB hit: yes, valid: yes
PPN: `0x0A`
PA: `0x0A | 000010` = `00001010000010`