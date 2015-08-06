To avoid the ownership semantics (which we will later discuss) you must cast
raw pointers references:

```
x: int = 5; // define x
y: ^int = ^int(&x); // reference x, cast to raw pointer of int
```