# Option Types [in progress]

An option type represents the encapsulation of an optional value. An option type
can either contain `Some(x)`, where `x` is the value it contains, or `None`, i.e.
no value.

Option types are -- soon to be -- defined in the standard library. Option types
make use of Ark features for their implementation. In other words, an Option Type
is a tagged union that allows for a generic type `T`.

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
