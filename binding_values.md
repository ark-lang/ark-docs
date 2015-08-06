If we directly match something, like the return value from a function, we
can bind it in the arm instead of re-evaluating the expression or binding it
beforehand:

```
func age() -> s32 => return 17;

match age() {
    age @ 17 -> println("felix's age is %d", age);
    age -> println("vedant's age is ", age);
}
```