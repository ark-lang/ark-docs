# De-structuring
![Feature In Progress](Badge_InProgress.svg)

## De-structuring Tuples

Tuples can be de-structured by binding values to an identifier:

```
pair := (0, -5);
match pair {
    pair(0, b) => /* do stuff with b */;
    pair(a, 0) => /* do stuff with a */;
    pair(a, b) => /* do stuff with a and b */;
}
```

## De-structuring Tagged Unions
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

We can de-structure it by binding the values to given identifiers, for instance:

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
