C is a compiled language
What you write is not what is run on the machine

## Statements

You can only ever give two arguments to your `main()` [[Functions|function]].
Those are 
```c
int main(int argc, char* argv[]) {}
```

`argc`: argument count
`argv`: argument values
These are taken from cmd

The path of the file is always the first argument


## Shortcuts

```c
int main(int argc, char* argv[]) {
  int a = 1;
  int b = 2 + a;
  a += b; // a = a + b
  a *= 2; // double
  a++; // a = a + 1
  a--; // a = a - 1
  ++a; // a = a + 1
}
```

Beware of side effects though
```c
int main(int argc, char* argv[]) {
  int a = 3;
  int b = 5;
  int c = a++ + ++b; // ordering matters!
  printf("a_=_%d\n", a) // 4
  printf("b_=_%d\n", b) // 6
  printf("c_=_%d\n", c) // 9
}
```

*Informally*, `++a` first increments `a`, then returns its value
*Informally*, `b++` first returns the value of `b`, and then increments

```c
int main(void) {
  int a = 3; 
  int b = 5;
  int c = -2;
  a += (c = a++ - (b += --c)) + ++b; // never do this
  printf("a = %d\n", a);
  printf("b = %d\n", b);
  printf("c = %d\n", c);

}
```

## Arrays

C doesn't have complex support for arrays nor many higher order [[functions]]

```c
int main(int argc, char* argv[]) {
  int a[16]; // specify value type and length of array
  a[0] = 1;
  for (int i = 1; i < 16; i++) {
    a[i] = a[i-1] + 1;
  }
  printf("final_=_%d\n", a[15])
}
```

- Arrays cannot be compared
- Arrays cannot be assigned to
- No check for out of bounds

## String formatting

### Writing to `stdout`
![[Pasted image 20250830190819.png]]

### Reading from `stdin`
```c
int main(int argc, char* argv[]) {
  char input[20];
  printf("Give me a string\n");
  scanf("%s", input); // not used commonly since size can be exceeded
  printf("You wrote: &s\n", input);
}
```

Rather use `fgets` for strings. `scanf` is also used for `int` inputs.

```c
int main(int argc, char* argv[]) {
  char input[20];
  printf("Give me a string\n");
  fgets(input, sizeof(input), stdin) // only takes first 20 char
  printf("You wrote: &s\n", input);
}
```

[[Numbers#Representation of integers|Int]] input:
```c
int main(int argc, char* argv[]) {
  int input;
  printf("Give me an integer!\n");
  scanf("%d", &input);
  printf("You wrote: &s\n", input);
}
```

`&` signs a [[Pointers|pointer]] and thus passes the address for the variable
Detailed scan of integer from arguments:

```c
int main(int argc, char* argv[]) {
  int input;
  if (argsc == 2) {
    int res = sscanf(argv[1], "%d", &input); // converts argument to int
    if (res == 0) {
      printf("Bad value\n");
    } else {
      printf("Input was %d\n", input);
    }
  }
}
```

![[Pasted image 20250831225537.png]]

## Pointers and addresses

![[Pasted image 20250904204817.png]]