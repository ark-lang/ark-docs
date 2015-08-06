We can define a structure with the `struct` keyword, followed by a block that
contains the types that the structure made up of. Note that an anonymous
`struct` is not a statement, thus it is not typically terminated with a
semi-colon. In the example below, we end it the statement with a
semi-colon, not the type (even though it may look like we do). 

You can specify default values for structure values, these are used as a
fall-back in case the initial value is not specified when an instance of the 
structure is created.

```
// anonymous structure
struct {
    d: int,
    g: int,
}

// bind structure to variable
mut x: struct {
    a: int = 2,
    b: int,
};
```

To access values in a structure, simply write the structures name, followed by
the dot operator, and the members name to acces.

```
x.a = 100;
x.b = 100;
```