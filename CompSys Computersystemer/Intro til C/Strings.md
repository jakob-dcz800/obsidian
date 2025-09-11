## Strings

Strings are special. There is a special kind of [[Aggregate data types#Arrays|array]] that we have encountered several times and that, in contrast to other arrays, even has literals: strings

**A string is a 0-terminated array of char.**

That is, a string like `"hello"` always has one more element than is visible, which contains the value 0, so here the array has length 6.

Like all arrays, strings can’t be assigned to, but they can be initialized from string literals:
```c
char jay0[] = "jay"; 
char jay1[] = { "jay" }; 
char jay2[] = { ’j’, ’a’, ’y’, 0, }; 
char jay3[4] = { ’j’, ’a’, ’y’, };
```

These are all equivalent declarations. Be aware that not all arrays of char are strings, such as the last two.

These both cut off after the `’y’` character and so are not 0-terminated:

### Functions

Functions that operate on `char` arrays are as follows:

• `memcpy(target, source, len)` can be used to copy one array to another. These have to be known to be distinct arrays. The number of chars to be copied must be given as a third argument len. 

• `memcmp(s0, s1, len)` compares two arrays in lexicographic order. That is, it first scans the initial segments of the two arrays that happen to be equal and then returns the difference between the two first characters that are distinct. If no differing elements are found up to len, 0 is returned. 

• `memchr(s, c, len)` searches array s for the appearance of character c.

String functions:

![[Pasted image 20250908124234.png]]

• strlen(s) returns the length of the string s. This is simply the position of the first 0 character and not the length of the array. It is your duty to ensure that s is indeed a string: that it is 0-terminated. 

• strcpy(target, source) works similarly to memcpy. It only copies up to the string length of the source, and therefore it doesn’t need a len parameter. Again, source must be 0-terminated. Also, target must be big enough to hold the copy. 

• strdup(source) and strndup(source, len) (since C23) work similar as strcpy, but they first allocate storage for the copy. We will see much later in section 13.1 how such allocated storage works. Again, for strdup, the argument source must be 0-terminated; for strndup, this requirement is a bit relaxed because the function will never read beyond the lenth character of source. 

• strcmp(s0, s1) compares two arrays in lexicographic order, similarly to memcmp, but it may not take some specialties of the language environment into account, for example at which position of the alphabet the character “ä” is considered. The comparison stops at the first 0 character that is encountered in either s0 or s1. Again, both parameters have to be 0-terminated. 

• strcoll(s0, s1) compares two arrays in lexicographic order, respecting language-specific environment settings. We will learn how to properly set this in subsection 8.7. 

• strchr(s, c) is similar to memchr, but the string s must be 0-terminated. 

• strspn(s0, s1) returns the length of the initial segment in s0 that consist of characters that also appear in s1.

• strcspn(s0, s1) returns the length of the initial segment in s0 that consist of characters that do not appear in s1.

**Using a string function with a non-string leads to program failure.**

### Pitfalls
In real life, common symptoms for such misuse include 
	• High execution times for `strlen` or similar scanning functions because they don’t encounter a 0-character 
	• Segmentation violations because such functions try to access elements after the boundary of the array object
	• Seemingly random corruption of data because the functions write data in places where they are not supposed to

In other words, be careful and make sure all your strings really are strings