# Function Receivers
You can specify the receivers of a function to make it exclusive to that particular
type. This means that in order to call the function, you need an instance of the
type that it wants in the receiver.

Function receivers are specified in parenthesis _before_ the functions identifier. A
function receiver is an "extra parameter", however the compiler will pass it to
the function implicitly in code gen. This means that functions can be called with the
dot operator.

A function that has a receiver is a method, since it "belongs" to a type.

```
type Foo struct {
    a: int,
};

func (a: Foo) bar() {
    // do stuff here
}
```

## Calling Methods
A method needs an instance of the function receiver in order to be called. It is
called with the dot operator like so:

```
foo: ^Foo;
foo.bar();
```

The `bar` function takes an instance of `Foo`, however it takes a copy of `Foo`,
and not a pointer to it. This is an important detail, because `Foo` will be copied
into the function, instead of a pointer to it.