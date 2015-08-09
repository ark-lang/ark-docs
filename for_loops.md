# For Loops
![Feature Implemented](Badge_Implemented.svg)

A for loop is specified with the `for` keyword, there are a few types of for
loops that you can do:

## Infinite For Loop
An infinite for loop is an infinite loop that performs the contents of the
block over and over until it is broken out of with either `break`, or `return`.

This loop is denoted with the `for` keyword and a block:

```
for {
    println("it never stops!");
}
```

## Conditional For Loop
An indexed for loop is similar to the traditional for loop, it has a condition
and a step. It will loop till the condition given is no longer true, and it
will perform the step at the end of each iteration:

```
mut x := 0;
for x < 5, x = x + 1 {
    ...
}
```

## Indexed For Loop
An indexed for loop is similar to the traditional for loop, it has a condition
and a step. It will loop till the condition given is no longer true, and it
will perform the step at the end of each iteration:

```
mut x := 0;
for x < 5, x = x + 1 {
    ...
}
```
