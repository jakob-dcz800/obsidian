A rainbow table is a precomputed table for [[Cache|caching]] the outputs of a cryptographic hash function, usually for cracking password hashes. 

Passwords are typically stored not in plain text form, but as [[Hashing|hash]] values. If such a database of hashed passwords falls into the hands of attackers, they can use a precomputed rainbow table to recover the plaintext passwords. 

A common defense against this attack is to compute the hashes using a key derivation function that adds a "[[Salting|salt]]" to each password before hashing it, with different passwords receiving different salts, which are stored in plain text along with the hash

---
From exam: 

A rainbow table is a precomputed list of inputs and their [[Hashing|hash]] output according to one or more different hashing algorithms. Usually the inputs will be a variety of common passwords. 

They could also be targeted against an individual or organisation, so in the case of a celebrity then you might hash their name, birthday or other public info etc. Unsecure applications might save and user details in plaintext, with a common fix being to save them as hashes instead. If an attacker gains access to the application or server, and obtains this login info then to derive passwords they will need to brute force each password in turn. 

This takes ages, which increases the chances that the attack is noticed and passwords changed. A rainbow table is computed ahead of time so matching hashes with pre-existing inputs can be trivially identified, meaning the attacker can ’legitimately’ log in as an authorised user.