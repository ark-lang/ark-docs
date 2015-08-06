# Option Types [in progress]

An option type is used in replace of a null pointer, an object can either be
`Some(x)` or `None`. Option types are in the standard library, they are
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
