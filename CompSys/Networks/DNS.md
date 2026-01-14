**Domain name system**

Runs on [[Transfer protocols#UDP service|UDP]]

• Computer science concepts underlying DNS 
	• Indirection: names in place of addresses. There is translation happening.
	• Hierarchy: in names, addresses, and servers. The DNS service also has a hierarchy. 
	• Caching: of mappings from names to/from addresses 

• DNS software components 
	• DNS resolvers 
	• DNS servers 
• DNS queries 
	• Iterative queries 
	• Recursive queries 
• DNS caching based on time-to-live (TTL)

# How does it work

There is some caching happening on the client.
Most of it is resolved on the network.
Too much information for the client. 

• Hierarchical name space divided into zones 
• Distributed over a collection of DNS servers 

• Hierarchy of DNS servers 
	• Root servers (knows where the .dk, .com etc. server is)
	• Top-level domain (TLD) servers  (.dk, .com, .io and so on...)
	• Authoritative DNS servers (forenika, amazon, facebook, and so on... knows all subpages /laes-mere...)

• Performing the translations 
	• Local DNS servers 
	• Resolver software
![[Pasted image 20251117163946.png]]

client wants IP for www.amazon.com; 1st approx: 
	• client queries a root server to find com DNS server 
	• client queries com DNS server to get amazon.com DNS server 
	• client queries amazon.com DNS server to get IP address for www.amazon.com

![[Pasted image 20251117165255.png]]

### Recursive version (standard)
![[Pasted image 20251117165413.png]]

## DNS Caching

Performing all these queries take time 
	• And all this before the actual communication takes place 
	• E.g., 1-second latency before starting Web download

Caching can substantially reduce overhead 
	• The top-level servers very rarely change 
	• Popular sites (e.g., www.cnn.com) visited often 
	• Local DNS server often has the information cached

How DNS caching works 
	• DNS servers cache responses to queries 
	• Responses include a “time to live” (TTL) field 
	• Server deletes the cached entry after TTL expires

Negative Caching: Remember things that do not work 
	• Misspellings like www.cnn.comm and www.cnnn.com 
	• These can take a long time to fail the first time 
	• Good to remember that they don’t work 
	• … so the failure takes less time the next time around

## Records

DNS: distributed db storing resource records (RR) 
RR format: (name, value, type, ttl)
### A
• name is hostname 
• value is IP address
### CNAME
• name is alias name for some “canonical” (the real) name 
• www.ibm.com is really servereast.backup2.ibm.com 
• value is canonical name
### NS
• name is domain (e.g., foo.com) 
• value is hostname of authoritative name server for this domain
### MX
• value is name of mailserver associated with name

## DNS Protocol

**Query** and **reply** messages, both with same message format.

msg header 
	• identification: 16 bit # for query, reply to query uses same # 
	• Flags: 
		• query or reply 
		• recursion desired 
		• recursion available 
		• reply is authoritative

![[Pasted image 20251117170028.png]]