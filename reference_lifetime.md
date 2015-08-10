# Reference Lifetime
![Feature In Progress](Badge_InProgress.svg)

In the examples shown above, where references were used, they were
typically introduced in their own scope. So if we didn't introduce
a scope, we would have a collision:

```
x: ^int = std::mem::alloc(std::mem::sizeof(^x));
y: &int = &mut x; // reference to x here

C::printf("bread %d\n", ^x); // try to borrow x here
                             // y lifetime ends here
```

Note that the lifetimes of `x` and `y` collide, so we cannot borrow `x`
while `y` is in scope. To avoid this, we introduce a new scope:

```
x: ^int = std::mem::alloc(std::mem::sizeof(^x));
{
    y: &int = &mut x; // reference to x here
    // y's lifetime ends here
}

C::printf("bread %d\n", ^x); // it works!
```
