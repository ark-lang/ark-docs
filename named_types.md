Names can be bound to a type, you can declare custom types, or you can alias
existing types. Note that this is not a 'true' alias, and these types must be
cast to their core type.

A named type is denoted with the `type` keyword, followed by a name to bind it
to, and the type it aliases.

    type PersonAge int;
    type PersonWeight f32;
    
Each value in the initializer is the name of the value to initialise, followed by a colon `:` and the initial expression to assign the value. 

```
z: Vector = Vector {
    x: 23,
    y: 32,
};
```