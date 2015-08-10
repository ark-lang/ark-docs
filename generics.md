# Generics
![Feature In Progress](Badge_InProgress.svg)

Generics provide a method for creating functions and composite types that work 
across a wide range (read: all other) of types.

An example of a type definition using generics is the `Option` type:

```
type Option<T> enum {
    None,
    Some(T)
}
```

The definition tells us that the type `Option` takes a type parameter `T`, 
which after declaration can be used as if it was just a plain type. To declare 
an instance of the type you can explicitly pass a type parameter, or in most 
cases, let the compiler infer the type for you:

```
a: int = 0;
x := Option<int>::None()
y := Option::Some(a);
```

The other use case for generics is for defining functions that act on many 
types. An example of this could be a type-agnostic allocation function:

```
func alloc<T>() ^T {
    ptr := C::malloc(sizeof(T));
    ... // Check allocation success
    return ^T(ptr);
}
```

As with the `Option` type the definition tells us that `alloc` takes a type 
parameter `T`. The names of type parameters have the same limits as any other 
identifier, so `T` could've been named `TypeToAllocate` and the example 
would've worked just as well. Invoking the functions follow the same semantics 
as with using a generic type. It can either be done explicitly, or by letting 
the compiler infer the type:

```
x := alloc<SomeLargeStruct>();
y: ^SomeLargeStruct = alloc();
```
