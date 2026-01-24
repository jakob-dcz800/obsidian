# Network layer
There is one: IP (internet protocol)
- transport segment from sending to receiving host
- on sending side encapsulates segments into datagrams 
- on receiving side, delivers segments to transport layer 
- There are network layer protocols in every host, router 
- router examines header fields in all IP datagrams passing through it

## Key functions

### Forwarding
Move packets from router’s input to appropriate router output
analogy: process of getting through single interchange

### Routing
Determine route taken by packets from source to destination.
analogy: process of planning trip from source to destination.

# Design

![[Pasted image 20260120141242.png]]

# IP
> Best-Effort is Enough

• No error detection or correction 
	• Higher-level protocol can provide error checking 
• Successive packets may not follow the same path 
	• Not a problem as long as packets reach the destination 
• Packets can be delivered out-of-order 
	• Receiver can put packets back in order (if necessary) 
• Packets may be lost or arbitrarily delayed 
	• Sender can send the packets again (if desired) 
• No network congestion control (beyond “drop”) 
	• Sender can slow down in response to loss or delay
## Purpose
What service does IP actually provide?

Goal: connect existing networks
- Multiplexed utilization of existing networks 
- Communication should continue despite failures
- Support multiple types of communication services
	- Differing requirements for speed, latency, & reliability 
	- Bidirectional reliable delivery vs. message service
- Accommodate a variety of networks
- Cost-effectiveness
- Ease of attaching new hosts
- Accountability for use of resources
	- Monitoring functions in the nodes
## Fragmentation and Reassembly

• network links have MTU (maximum transfer size) 
	largest possible link-level frame. 
• different link types, different MTUs 
	large IP datagram divided (“fragmented”) within n

## Packet Structure

![[Pasted image 20260120141837.png]]
![[Pasted image 20260120141850.png]]

**8-bit Protocol**: 
	• Identifies the higher-level protocol 
	• E.g., “6” for TCP, “17” for UDP 
	• Important for demultiplexing at receiving host 
	• Indicates what kind of header to expect next


 Potential robustness problem 
	 • Forwarding loops can cause packets to cycle forever 
	 • Confusing if the packet arrives much later
Therefore: Time-to-live field in packet header 
	• TTL field **decremented by each router** on path 
	• Packet is discarded when TTL field reaches 0... 
	• ...and “time exceeded” message (ICMP) sent to source 

# IPv6

Similar format, but
- 128-bit addresses
- No fragmentation, no checksum, options optional