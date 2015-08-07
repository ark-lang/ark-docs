# Pointers [in progress]
Before we proceed to one of the more advanced topics in the Ark language, we
need to know about pointers. Pointers store (or point to) addresses in memory.

In Ark, we denote pointers with the caret symbol, `^`.

## Warning


## Meta
A raw pointer is not memory safe in Ark. Pointers work differently in the Ark 
language for memory safety (see ownership), but for behaviour similar to C we 
have raw pointers, which are described in this section.

## Pointing to Raw Memory
You may point to raw memory, yet you probably won't have to do this unless you 
know what you're doing:

    vga_start: ^u16 = ^u16(0xB8000);
    
As shown above, memory address (hex literals) should be cast to a pointer they
are being stored in.

## Referencing Memory
A reference to something is denoted with the address-of operator `&`. This is
expected to be stored in a reference type `&T = &xyz;`. However, this reference
will follow the rules of ownership, i.e. in this case a constant reference that
cannot be mutated, and must also not outlive the referrers lifetime. To avoid this
we can cast the reference to a pointer:

```
x: int = 5;

// avoid the ownership rules...
y: ^int = ^int(&x);

z: int = ^y; // get the value at y, store in x
```

## Dereferencing Pointers
To get the value at the given memory address, you simply dereference using
the caret:

```
x: int = 5;
y: ^int = ^int(&x);
z: int = ^y; // get the value at y, store in x
```
