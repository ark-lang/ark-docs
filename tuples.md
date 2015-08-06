# Tuple [implemented]

A tuple is similar to an array, however it is a collection of values that can
have irregular types, whereas an array is a collection of values in which their
types are consistent with each-other.

Tuples are surrounded with parenthesis. Tuple types are a list of types
separated with commas, surrounded with parenthesis. A tuple expression is
similar, however it contains a list of expressions instead of types. Note that
the expression should correspond with the type, i.e. they should be ordered
correctly:

```
a: (int, f64) = (1, 2.3);
b: (int, f64) = (2.3, 1); // ERROR!
c: (int, f64, f64, f64, int) = (1, 2.3, 3.2, 4.1, 6);
```
