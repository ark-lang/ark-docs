# Structures
![Feature Implemented](Badge_Implemented.svg)

We can define a structure with the `struct` keyword, followed by a block that
contains the structures members. Note that an anonymous `struct` is not a 
declaration, thus it is not terminated with a semi-colon.

```
// anonymous structure
struct {
    d: int,
    g: int,
}
```

We can bind a structure to a variable like so. Note that the structure itself
is not terminated with a semi-colon, but the variable declaration that is binding
this type does. 

We can also have default values for a structure. Default values are set in a 
similar fashion to variable declarations (name, colon, Type, assignment operator,
expression).

```
// bind structure to variable
mut x: struct {
    a: int = 2,
    b: int,
};
```

The dot operator - `.` - allows us to access the members of a structure:

```
// x is the structure
// a, b are the members
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

## Using Default Structure Values
There are two ways of using `default`. As an expression, or as a statement. The
`default` expression takes a Type `T`. The `default` statement takes an `access`, e.g.
a variable pointer, dereferenced pointer, structure member, array index, tuple index,
and so on.

### Default Expression
In this case, we use the `default` expression, which takes the Type `int`. This will
set `x` to the default value for an `int`, which is zero.

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
    
The above will set the person variable to use the Person type's default values. If 
we do not use the default statement on a structure, the structures members will not
have their memory zeroed out, thus causing them to contain random values.
