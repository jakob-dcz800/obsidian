
# OS managing

Most of memory management takes place in software.
Only the [[MMU]] exists in hardware.

Each process memory might have a structure like this:

![[Pasted image 20251004111756.png]]

Text is program code i.e. 'read only'.
Data is variables and dynamic declarations.
[[Dynamic memory#malloc|Malloc]] will occupy the space in between sl and data

## Virtual memory areas

Every vm area is backed up by a disk object (a location on disk) since we cannot write to virtual memory - as it is not writeable.

[[Address translation|terms]]
Translation between VA and PA is called **mapping**

### Backing

Any area can be **backed**
This is when we populate a vm area with initial values from a file on [[Hardware terms#Disk|disk]]
Anonymous file = empty file