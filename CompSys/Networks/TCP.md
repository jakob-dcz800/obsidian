[slides](obsidian://open?vault=compSys-e2025&file=material%2F25_11_05__TCP_and_Reliable_Communication%2FTCP_and_Reliable_Communication.pdf)
# TCP

Proper protocol which can retry sending packages
- Reliability: TCP sørger for at data kommer korrekt (checksum, acknowledgement (ACK), retransmissions) 
- Connection: Før data kan blive sent, skal en connection etableres (3-way handshake) 
- Flow control: Kontrollere mængden af data der sendes på en gang,. 
- Congestion control: justere sende raten baseret på netværket
![[Pasted image 20260120121948.png]]

## TCP Handshake

Initializing: 3-way handshake
Termination: 4-way teardown

![[Pasted image 20260120122030.png]]

# Flow control
## GBN (Go back N)
*Not part of TCP* (i think)

- Sender can send maximum N packages without ACK from the receiver.
- Discards packages that are out-of-order
	- i.e. there is no buffer on receiving end
- At triple ACK sender starts over at last sequence
- Depending on window size, it may be very expensive to resend packages.
![[Pasted image 20260120122902.png]]
### Example
![[Pasted image 20260120122912.png]]

### Example 2
Here, at e3, the lost package is re transmitted.
![[Pasted image 20260120165055.png]]

## SR (Selective repeat)
Used by TCP
- Uses a buffer for out of order packages
	- Needs a buffer on receiving end
- Retransmits lost or corrupted packages
	- Not base to base + N as in [[#GBN (Go back N)|GBN]]
- Both receiver and sender has sliding windows

### Example
![[Pasted image 20260120123210.png]]

### Exam example
![[Pasted image 20260120123357.png]]

client:
- send
- receive acknowledge
- timeout
- resend (after timeout)
server:
- acknowledge

*x*: number waiting
**x**: number received ack (removed the following step if at bottom of stack)

| stage | cmd        | window            | note                    |     |
| ----- | ---------- | ----------------- | ----------------------- | --- |
| c0    | send p0    | *0*               | fill it up              |     |
| c1    | send p1    | *0*, *1*          | fill it up              |     |
| c2    | send p2    | *0*, *1*, *2*     | fill it up              |     |
| c3    | rec ack p0 | **0**, *1*, *2*   |                         |     |
| c3    | send p3    | *1*, *2*, *3*     |                         |     |
| c4    | rec ack p2 | *1*, **2**, *3*   |                         |     |
| c5    | p1 timeout | *1*, **2**, *3*   |                         |     |
| c5    | send p1    | *1*, **2**, *3*   | all elements have acted |     |
| c6    | p3 timeout | *1*, **2**, 3     | --> then timeout        |     |
| c6    | send p3    | *1*, **2**, *3*   | --> then resend         |     |
| c7    | rec ack p1 | **1**, **2**, *3* | *remove* **1**, **2**   |     |
| c7    | send p4    | *3*, *4*          | stack is not full yet   |     |
| c8    | send p5    | *3*, *4*, *5*     |                         |     |
|       |            |                   |                         |     |
| s0    | ack p0     | 0                 |                         |     |
| s1    | ack p2     | 0, 2              |                         |     |
| s2    | ack p3     | 0, 2, 3           |                         |     |
| s3    | ack p1     | 0, 1, 2, 3        |                         |     |
| s4    | ack p3     | 0, 1, 2, 3        |                         |     |
| s5    | ack p4     | 0, 1, 2, 3, 4     |                         |     |
|       |            |                   |                         |     |

## Congestion window size graph

Congestion window is dynamic in size. It reduces size upon packet loss.
Each TCP sender maintains a congestion window 
- Max number of bytes to have in transit (not yet ACK’ d)

Adapting the congestion window 
- Decrease upon losing a packet: backing off
- Increase upon success: optimistically exploring 
- Always struggling to find right transfer rate

Tradeoff 
- Pro: avoids needing explicit network feedback 
- Con: continually under- and over-shoots “ right” rate

### AIMD
How much to adapt the size of the window?
Rule: Additive Increase, Multiplicative Decrease (**AIMD**)

Additive increase:
	On success of last window of data, increase window by 1 Max Segment Size (MSS)
Multiplicative Decrease
	On loss of packet, divide congestion window in half.

Much quicker to slow than speed up! 
- Over-sized windows (causing loss) are much worse than under-sized windows (causing lower throughput) 
- **AIMD**: A necessary condition for stability of TCP

![[Pasted image 20260120134037.png]]
### Receiver Window vs. Congestion Window
• Flow control 
	• Keep a fast sender from overwhelming a slow receiver 
• Congestion control 
	• Keep a set of senders from overloading the network

Different concepts, but similar mechanisms 
	• TCP flow control: receiver window 
	• TCP congestion control: congestion window 
	• Sender TCP window = min { congestion window, receiver window }

#### How Should a New Flow Start?
Start slow (a small [[#CWND]]) to avoid overloading network.
Could be pretty wasteful 
	• Might be much less than actual bandwidth 
	• Linear increase takes a long time to accelerate
Slow-start phase (really “ fast start” ) 
	• Sender starts at a slow rate (hence the name) 
	• … but increases rate exponentially until the first loss
![[Pasted image 20260120134614.png]]

So-called because TCP originally had no congestion control 
	• Source would start by sending an entire receiver window 
	• Led to congestion collapse!

## CWND

CWND = Congestion window.
How large is the window that needs to be filled up
# Loss

## Timeout

 Packet n is lost and detected via a **timeout** 
	 • When? 
		 n is last packet in window, or all packets in flight lost 
	 • After timeout, blasting entire [[#CWND]] would cause another burst 
	 • Better to start over with a low [[#CWND]]
![[Pasted image 20260120135010.png]]

Slow-start restart: 
Go back to [[#CWND]] of 1, but take advantage of knowing the previous value of [[#CWND]].
## Triple duplicate ACK

 Packet n is lost, but packets n+1, n+2, etc. arrive 
	 • How detected? 
		 Multiple ACKs that receiver waiting for n 
	 • When?
		Later packets after n received 
	• **After triple duplicate ACK**, sender quickly resends packet n 
	• Do a multiplicative decrease (half) and keep 
## Slow start after idle period

Suppose a TCP connection goes idle for a while; eventually, the network conditions change.
	Maybe many more flows are traversing the link.
Dangerous to start transmitting at the old rate 
	• Previously-idle TCP sender might blast network
	 • … causing excessive congestion and [[packet loss]]
 So, some TCP implementations repeat slow start 
	 • Slow-start restart after an idle period