# Borrowing
![Feature Implemented](Badge_InProgress.svg)

One problem with the example above is if we keep transferring ownership
back and forth, it can get really messy. Take the following example:

```
func do_stuff(a: ^int) {
    // stuff
}

func main() {
    mut a: ^int = mem::malloc(mem::size_of(^a)); // alloc
    do_stuff(a); // pass to do_stuff
    ^a = 21; // ERROR!
}
```

The above example will give us an error- the same one as before. Why? Because
we are using a value that has its ownership transferred. There are however a few
ways we can avoid this:

* return the ownership back
* "borrow" the owned resource

If we did this, we would have to introduce a return type to our function, then
re-assign the memory again:

```
func do_stuff(a: ^int): ^int {
    // stuff
    return a; // done here, pass it back
}

func main() {
    mut a: ^int = mem::malloc(mem::size_of(^a)); // alloc
    a = do_stuff(a); // pass to do_stuff, return ownership
    ^a = 21; // yay, it works!
}
```

Would this work out well? Probably not. In a larger scale program, this will 
get very messy. If you were dealing with more resources, you would have to
handle their ownership too.
