# Memory Allocation
Memory allocation is handled in the standard library, there are a few functions
used for allocating memory, namely `alloc`, `alloc_raw`, `sizeof`, and `dealloc`.

## `alloc`
The `alloc` function takes a generic type `T`, and no arguments This function
will allocate enough memory to store the size of the generic type you pass in.

## `alloc_raw`
The `alloc_raw` function will allocate raw memory, it takes the amount of memory to
allocate as an unsigned integer.

## `sizeof`

## `dealloc`