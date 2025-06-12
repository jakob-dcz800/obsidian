# Object adapter pattern
Much related to class adapter.
Difference is: 

![[Pasted image 20250612112616.png]]
1. The **Client Interface** describes a protocol that other classes must follow to be able to collaborate with the client code.
2. The **Service** is some useful class (usually 3rd-party or legacy). The client can’t use this class directly because it has an incompatible interface.
3. The **Adapter** is a class that’s able to work with both the client and the service: it implements the *client interface*, while wrapping the *service* object. The adapter receives calls from the client via the client interface and translates them into calls to the wrapped service object in a format it can understand.
4. The client code doesn’t get coupled to the concrete adapter class as long as it works with the adapter via the client interface.



## Compared to class adapter

Class Adapter pattern  
• consists of only one object,  
• which can carry out the requested tasks itself.

Object Adapter pattern  
• comprises several objects,  
• of which the actual adapter produces only the appropriate interface  
• and distributes the actual "work" to other objects (delegation).  

Actually, the adapter object in the object adapter pattern does little by itself, but only knows objects, which can fulfil the required tasks together