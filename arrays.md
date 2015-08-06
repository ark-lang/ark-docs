# Arrays
An array is a static collection of values that have a uniform type. Arrays are 
denoted with square brackets, or "blocks". Arrays are accessed using subscript
notation. An arrays size should be known at compile-time, you can specify this
in the initialiser by either setting the arrays initial values, and letting
the compiler deduce the size of the array, or using the size
initializer syntax:

```
a: [int; 5] = [0, 1, 2, 3, 4]; // size deduced, size in type is superfluous
b: [int]; // ERROR! no initial value, no size!
mut c: [int; 5]; // compiler will zero out 5 contigiuos slots of memory

d: int = a[2]; // subscript notation for access
c[1] = a[2]; // and setting array values too
```