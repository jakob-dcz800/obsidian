
**Hyper text transfer protocol**

- GET
- POST
- HEAD
- PUT
- DELETE

Stateless

## Request body

![[Pasted image 20251117155819.png]]

## HTTP Caching

![[Pasted image 20251117160126.png]]

Same principal as [[CompSys/Hardware/Memory hierarchy|caching]]

HTTP caches on proxy servers that are closer to the end point (client).

## DASH

Dynamic, Adaptive, Streaming over HTTP

• server: 
	• divides video file into multiple chunks 
	• each chunk stored, encoded at different rates 
	• manifest file: provides URLs for different chunks 
• client: 
	• periodically measures server-to-client bandwidth 
	• consulting manifest, requests one chunk at a time 
	• chooses maximum coding rate sustainable given current bandwidth 
	• can choose different coding rates at different points in time (depending on available bandwidth at time) 