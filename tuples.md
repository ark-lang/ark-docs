# Tuple
![Feature Implemented](Badge_Implemented.svg)

A tuple is a collection of values that can have irregular types. Tuples are similar
to an array, though an array is a collection of values in which their types are
uniform with one and another.

Two parenthesis that contain types separated by commas will denote a tuple type. A
tuple expression is like a tuple type, but instead of specifying the type
in the parenthesis, you specify the values instead. A tuple expression should have
the values specified in the same order that the type expects:

```
a: (int, f64) = (1, 2.3);

// here we expect an int and a float, but we get
// a float and an int
b: (int, f64) = (2.3, 1); // ERROR!

c: (int, f64, f64, f64, int) = (1, 2.3, 3.2, 4.1, 6);
```

## Accessing Tuple Values
Pipe operators denote tuple access. For instance, to access the values in a tuple
`x`, we write `x|n|` where `n` is the index of the item to access in the tuple.

> this syntax is under review

```
a: (int, f64) = (1, 2.3);
y := a|0|;
z := a|1|;
```