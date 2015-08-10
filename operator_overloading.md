# Operator Overloading
![Feature Planned](Badge_Planned.svg)

Ark allows operator overloading, however there are a few restrictions enforced 
for safety. You can overload the following operators:

* `+` => addition
* `-` => subtraction
* `/` => division
* `*` => multiplication
* `%` => modulo

The `operator` keyword, followed by the operator to overload, a set of parameters
and a return type denote an operator overload. This syntax is very similar to a
function, however the `operator` keyword is used in replace of `func`, and the symbol
to overload in replace of a function name.

```
operator +(a: Vector2, b: Vector2) -> Vector2 {
    ...
}
```

By default operator implementations are unordered, for example:

```
operator *(a: Vector2, b: f32) -> Vector2 {
    ...
}
```

This will allow both `Vector2 * f32` and `f32 * Vector2`. You can force an operator
overload to be ordered using the `ordered` attribute:

```
[ordered]
operator *(a: Vector2, b: f32) -> Vector2 {
    ...
}

[ordered]
operator *(a: f32, b: Vector2) -> Vector2 { 
    ... 
}
```