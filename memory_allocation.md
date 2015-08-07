# Memory Allocation
Memory allocation is handled in the standard library, there are a few functions
used for allocating memory, namely `alloc`, `alloc_raw`, `sizeof`, and `dealloc`.

## `alloc`
The `alloc` function takes a generic type `T`, and no arguments This function
will allocate enough memory to store the size of the generic type you pass in.
The `alloc` function returns a pointer to the memory block that it allocates.

```
func main() -> int {
    foo: ^int = std::mem::alloc<int>();
}
```

## `alloc_raw`
The `alloc_raw` function will allocate raw memory, it takes the amount of memory to
allocate as an unsigned integer. Like the `alloc` function, the `alloc_raw` function
will also return a pointer to the memory block that it allocates.

## `sizeof`

## `dealloc`