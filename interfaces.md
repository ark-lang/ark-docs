# Interfaces
Interfaces are named collections of method signatures. In Ark, interfaces are implicit,
which means that if something has the methods defined in an interface `A`, it will
implicitly implement interface `A`. This allows for duck typing, or in
other words: 

> If it looks like a duck, and quacks like a duck, it's a duck"

The `interface` keyword, followed by a block that consists of method signatures
will denote an interface. Method signatures defined in an interface do not 
need to specify the `func` keyword.

```
interface {
    
}
```