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

Since a `type` is a statement, it must be terminated with a semi-colon.
