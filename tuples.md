# Tuple [implemented]

A tuple is a collection of values that can have irregular types. Tuples are similar
to an array, however an array is a collection of values, which have a **uniform type**.

Two parenthesis that contain types separated by commas will denote a tuple type. A
tuple expression is like a tuple type, but instead of specifying the type
in the parenthesis, you specify the values.

Tuple types are a list of types separated with commas, surrounded with parenthesis. A tuple expression is
similar, however it contains a list of expressions instead of types. Note that
the expression should correspond with the type, i.e. they should be ordered
correctly:

```
a: (int, f64) = (1, 2.3);
b: (int, f64) = (2.3, 1); // ERROR!
c: (int, f64, f64, f64, int) = (1, 2.3, 3.2, 4.1, 6);
```
