```c
#include <stddef.h>
#include <stdint.h>
#include <stdio.h>

// prints four different memory addresses in the stack
// the addresses are within one word
void show_bytes(unsigned char* start, size_t len) { 
// start could be anything - its just bytes
	size_t i;
	for (i = 0; i < len; i++) {
		printf("%p\t0x.2x\n", start+i, start[i]);
		// %p is to insert the pointer
		// \t is tab
		// 0x is string literal to show that we're printing hex
		// %.2 means print two decimals
	}
	printf("\n);
}

int main() {
	int a = 15213;
	printf("a = 15213;\n");
	show_bytes((unsigned char*) &a, sizeof(int));
	
}
```