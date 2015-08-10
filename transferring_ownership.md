# Transferring Ownership
![Feature In Progress](Badge_InProgress.svg)

Consider the following example:

    {
        x: ^int = std::mem::alloc(std::mem::sizeof(^x));
        y: ^int = x;
    }

In the example above, we set `y` to point to `x`. This has some subtle 
semantics- it will transfer the ownership from `x` to `y`, which means that `y`
now has "ownership" of the memory that `x` previously pointed to.

If this is tricky to wrap your head around, consider this real-life analogy. 
Say I had a loaf of bread. If I were to give to my friend Vedant this loaf of 
bread, I don't own it any more, which means I cannot eat the bread, and I 
can't give it to someone else as I am no longer in possession of said loaf of bread. 

Note that you cannot mutate or use something that no longer has ownership of 
the resource that it previously pointed to. This means that if we use `x` after 
transferring its ownership to `y`, it won't work because it is no longer in 
possession of the resource it is bound to as it has been transferred to `y`.

This means that the following example would **not** work:

```
{
    x: ^int = std::mem::alloc(std::mem::sizeof(^x));
    y: ^int = x;
    C::printf("the value at at x is %d\n", ^x); // ERROR!
}
```

The last line would error because we have already transferred 
ownership from `x` to `y`, so we can no longer use `x` until its ownership
is restored.

To restore ownership from `y` to `x`, we just do the reverse, that is, we
move `y` to `x` like so:

```
{
    mut x: ^int = std::mem::alloc(std::mem::sizeof(^x));
    y: ^int = x;
    x = y; // give back the ownership
    C::printf("the value at at x is %d\n", ^x); // This works fine! :)
}
```

However, one slight change: I made `x` a mutable variable. This is to
avoid an error when we re-assign `x` later on to be `y`, as otherwise it wouldn't
compile.
