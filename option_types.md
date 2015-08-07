# Option Types [in progress]

An option type represents the encapsulation of an optional value. An option type
can either contain `Some(x)`, where `x` is the value it contains, or `None`, i.e.
no data.

Option types are in the standard library, they are
represented with a tagged union, and can take any type `T`.

```
mut x: Option<int> = None;
x = Some(23);
```

We can then match options like so:

```
match x {
    Some(x) -> println("hey our integer is %d", x);
    None -> println("Nothing there! :(");
}
```
