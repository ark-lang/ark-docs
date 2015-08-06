Given the following enum:

```
type Whatever enum {
    Foo,
    Colour(s32, s32, s32),
    Move {
        x: s32,
        y: s32,
    },
};
```

We can destructure it by binding the values to given identifiers, for instance:

```
something := Whatever::Colour(255, 0, 255);

match something {
    Whatever::Foo -> {
        ...;
        ...;
    };
    Whatever::Colour(r, g, b) => println("you chose %d, %d, %d", r, g, b);
    Whatever::Position {x: x, y : y} => println("you are at %d %d", x, y);
    _ -> ...;
}
```