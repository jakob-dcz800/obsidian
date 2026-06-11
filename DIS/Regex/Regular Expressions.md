
# Regular Expressions
> The Swiss Army Knife of the Working Programmer

• `Ø` is a regular expression (does not match anything) 
• `e` is a regular expression (matches the empty string "") 
• `a` is a regular expression (matches the string "a") 
• `r+s` is a regular expression if and are regular expressions 
	(matches any string that `r` or `s` match) 
• `rs` is a regular expression if and are regular expressions 
	(matches any string that can be split into a prefix that matches `r` and a suffix that `s` matches) 
• `r*` is a regular expression if is a regular expression 
	(matches the empty string "" and any string that can be split into substrings each of which `r` matches)
## Example
![[Pasted image 20260423145034.png]]


>[!DEFINITION] Language of an expression
>Language of a regular expression r = set of strings that r matches
>Regular language = infinite set that can be represented finitely by a regular expression

a regular expression cannot count
Time complexity: linear in the size of `regular expression` and `string`

# Tools

## Bash

**grep**: find matching substrings in a text 
**sed**: replace matching substrings in a text

## Python

**re** library https://docs.python.org/3/library/re.html

```python
re.fullmatch(r'(a+b)*baa','abbaa') 
# -> <re.Match object; span=(0, 5), match='abbaa'>
re.findall(r'w[a-z]*', 'whisper words of wisdom let it be') 
# -> ['whisper', 'words', 'wisdom']

```

