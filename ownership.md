# Ownership
![Feature In Progress](Badge_InProgress.svg)

Ownership is a set of rules that Ark will enforce to ensure
memory safety. This will allow for zero-cost abstractions and help make 
features such as dynamic arrays, operator overloading etc. potentially safer.

When allocating memory, the variable that is associated with it has ownership 
of it. When this variable goes out of scope, the aforementioned memory that it 
points to is de-allocated. Take the following example:

```
{
    x: ^int = std::mem::alloc(std::mem::sizeof(^x));
    // x now holds a pointer to the allocated memory

    // the memory that x points to is de-allocated here
}
```

In the example above, when `x` comes into scope, memory is allocated on the 
heap and the address is stored in `x`. When this variable goes out of scope,
Ark will de-allocate the memory associated with said variable as it is no 
longer needed.
