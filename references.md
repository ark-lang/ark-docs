# References
![Feature In Progress](Badge_InProgress.svg)

How do we solve this issue? We use something called "borrowing". Instead of
moving these values to the function, we pass a reference to these values.
A reference has a few extra properties:

* it cannot mutate what resource it refers to
* it is **not** de-allocated at the end of scope

A reference is denoted with an ampersand (`&`), followed by the resource it
is referring to. This means that the above example becomes the following:

```
func do_stuff(a: ^int) {
    // do stuff with a (kind of...)
    // remember it's not freed here because
    // it's a reference!
}

func main() {
    mut a: ^int = std::mem::alloc(std::mem::sizeof(^a)); // alloc
    do_stuff(&a); // no re-assignments necessary
    ^a = 21; // yay, it works!
}
```

And all should work well! However, note my little comment "do stuff with a (kind of...)". I say "kind of" because we are passing a reference, and if you
remember one of the properties of a reference is that you cannot mutate the
resource that it is borrowing or refers to.

To work around this, we can use a "mutable reference", denoted in a similar manner to
immutable references, except we put the `mut` keyword after the ampersand,
like so: `&mut T`. This gives us the ability to "mutate" the memory that we pass a reference to.

However, there are a few rules with regards to mutable references:

* you can have **only one** mutable reference to a resource at a time
* you can have N number of immutable references
