The compiler will run all computations at compile time. If a calculation is unused in the program but only used, the compiler will write
```c
printf("x is 4.5\n");
```

From the code:
```c
double x = 5.0; 
double y = 3.0; 
... 
x = (x * 1.5) - y; 
printf("x is \%g\n", x);
```