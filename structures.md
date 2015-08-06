# Structures

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
the dot operator, and the members name to access.

```
x.a = 100;
x.b = 100;
```

We can define custom types by binding an anonymous structure to a named type:

```
type Vector struct {
    x: f64,
    y: f64,
}; // note the semi-colon

v: Vector;
v.x = 23;
v.y = 32;
```

Since a `type` is a statement, it must end with a semi-colon.

## Using Default Structure Values
### Default Expression
Note that default can also be an expression, this will set the default for a
given type:

```
x: int = default(int);
```

### Default Statement
In order to use any default values specified in a structure, you must initialize
a structure using the default statement:

    type Person struct {
        a: int = 0,
        b: int = 0,
    };
    person: Person;
    default(person);
    
The above will set the person variable to use the Person types default values, if
you do not set a default to structure, it will be initialized with garbage values.