# Named Types [implemented]

Names can be bound to a type, you can declare custom types, or you can alias
existing types. 

The `type` keyword, followed by a name to bind it to, and the type it aliases, denotes
a Named Type. Here are some examples:

```
type PersonAge int;
type PersonWeight f32;
```
    
A type is a declaration, so it must be terminated with a semi-colon. You can have
unnamed types, i.e. you do not have to bind a type to a name:

```
something: struct {
    a: int,
    b: int
};
```

It's important to know that this isn't a true alias, it's a new type, which means
that it must be cast. For example:

```
type Foo int;

a: int = 10;
b: Foo = Foo(a); // we have to cast a to Foo.
```