# Memory Allocation
![Feature In Progress](Badge_InProgress.svg)

Memory allocation is handled in the standard library, there are a few functions
used for allocating memory, namely `alloc`, `alloc_raw`, `sizeof`, and `dealloc`.

## `alloc`
The `alloc` function takes a generic type `T`, and no arguments This function
will allocate enough memory to store the size of the generic type you pass in.
The `alloc` function returns a pointer to the memory block that it allocates as the type `T`.

```
foo: ^int = std::mem::alloc<int>();
```

## `alloc_raw`
The `alloc_raw` function will allocate raw memory, it takes the amount of memory to
allocate as an unsigned integer. Like the `alloc` function, the `alloc_raw` function
will also return a pointer of bytes to the memory block that it allocates.

```
foo: ^u8 = std::mem::alloc_raw(256);
```

## `sizeof`
`sizeof` is an expression that will get the size of the given type `T` or expression
`E`. Since `alloc` handles memory allocation for types for you, we suggest not using
this in pair with `alloc_raw`. However, it is available for when you need the size
of an expression or type.

```
foo: ^u8 = std::mem::alloc(std::mem::sizeof(int) + std::mem::sizeof(f64));
```

## `dealloc`
`dealloc` will de-allocate the memory that is given to it, this must be called after
allocating any memory, otherwise you will get a memory leak. Note that you should
*not* use this on memory that isn't stored on the heap. The `dealloc` function takes
a pointer to the memory that it should deallocate.

```
x: ^int = std::mem::alloc<int>();
defer std::mem::dealloc(x);
```

In the example above we defer, which means that at the end of scope, call dealloc on `x`. The defer expression is very handy with resource allocation.