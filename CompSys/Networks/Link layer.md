# Link/Physical layer
%% Discuss network configurations consisting of subnets and LAN segments %%

Link layers are implemented in adaptors (network interface card)
*e.g. Ethernet card, PCMCIA card, 802.11 card*

![[Pasted image 20260120143355.png]]
## Types of Links
%% Identify the main functions of the link layer: framing, error detection, and multiple access %%

### Point-to-point

### Broadcast

Ethernet
Wireless LAN (local area network)
## MAC addresses
%% Describe what MAC addresses are as well as the Address Resolution Protocol (ARP) %%
32-bit [[IP Adresses|IP address]] (NOT MAC): 
	• [[Network layer]] address 
	• used to get datagram to destination IP subnet

MAC Address: 
function: get frame from one interface to another physically-connected interface (same network)
48 bit MAC address (for most LANs) 
	• burned in NIC ROM, also sometimes software settable

MAC address allocation administered by IEEE 
- manufacturer buys portion of MAC address space (to assure uniqueness)

Analogy: 
	• MAC address: like Social Security Number 
	• IP address: like postal address
## ARP

> Address Resolution Protocol 

Each IP node (host, router) on LAN has **ARP table**
ARP table: IP/MAC address mappings for some LAN nodes `<IP address; MAC address; TTL>`
	TTL (Time To Live): time after which address mapping will be forgotten (usually 20 mins)

Page 21: [slides](obsidian://open?vault=compSys-e2025&file=material%2F26-01-07__network-and-link_layer%2Fslides_3_link-layer.pdf)
## Framing
Page 8: [slides](obsidian://open?vault=compSys-e2025&file=material%2F26-01-07__network-and-link_layer%2Fslides_3_link-layer.pdf)

"Break sequence of bits into a frame"
	Typically implemented by the network adaptor	
Sentinel-based 
	Delineate frame with special pattern (e.g., `01111110`)

![[Pasted image 20260120143530.png]]
## Ethernet
%% Explain the multiple access mechanisms of Ethernet and their rationale %%
## Multiple Access
%% Define the following methods for multiple access: channel partitioning, taking turns, random access %%
## Switching
%% Define hubs, switches, and routers %%
%% Describe the self-learning mechanism used in switches to build forwarding tables %%

# Error detection

## Parity check 
• Add an extra bit to a 7-bit code 
• Odd parity: ensure an odd number of 1s 
• E.g., 0101011 becomes 01010111 
• Even parity: ensure an even number of 1s 
• E.g., 0101011 becomes 01010110
## Checksum 
• Treat data as a sequence of 16-bit words 
• Compute a sum of all 16-bit words, with carries and wraparounds 
• Transmit the sum (1s complement of this) along with the packet 
• Cyclic Redundancy Check (CRC)