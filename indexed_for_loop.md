An indexed for loop is similar to the traditional for loop, it has a condition
and a step. It will loop till the condition given is no longer true, and it
will perform the step at the end of each iteration:

```
mut x := 0;
for x < 5, x = x + 1 {
    ...
}
```