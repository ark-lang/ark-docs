# Arrays [implemented]
An array is a static collection of values that have a uniform type. Arrays are 
denoted with square brackets, or "blocks". Arrays are accessed using subscript
notation. An arrays size should be known at compile-time, you can specify this
in the initialiser by either setting the arrays initial values, and letting
the compiler deduce the size of the array, or using the size
initializer syntax:

> While this implemented, the syntax is currently being reviewed
> for change: [RFC #17](https://github.com/ark-lang/rfcs/issues/16)

```
a: []int = [0, 1, 2, 3, 4]; // size deduced, size in type is superfluous
b: []int; // ERROR! no initial value, no size!
mut c: [5]int; // compiler will zero out 5 contigiuos slots of memory

d: int = a[2]; // subscript notation for access
c[1] = a[2]; // and setting array values too
```

## Bounds Checking
Ark does some simple bounds checking for arrays, a segmentation fault will be
generated if you go out of the bounds of an array.