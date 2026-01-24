[slides](obsidian://open?vault=compSys-e2025&file=material%2F25_10_29__HTTP_Caching_and_Content_Distribution%2FHTTP_Caching_and_Content_Distribution.pdf)
**Hyper text transfer protocol**

- GET
- POST
- HEAD
- PUT
- DELETE
## Stateless

HTTP is stateless - no persistent connections.
Consists of requests and responses

The server does not keep any information about the client, each request is treated as its own transaction. 
Avoids a lot of server side logic of keeping track of clients, more [[Concurrency|concurrent]] requests possible, using very little buffer space on server side

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