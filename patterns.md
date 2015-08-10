# Patterns
![Feature Planned](Badge_Planned.svg)

## Ranges
An exclusive range is denoted with two dots, e.g: `0 .. 5`, this will match 0
to 4. An inclusive range is denoted with two dots and an equals symbol, e.g.
`0 ..= 5`, this will match 0 to 5.

## Multiple Values
Multiple values can be matched using commas:

    match x {
        1, 2 => ...; // both 1 and 2
        _ => ...; // everything else
    }

## Underscore
The underscore `_` is a "default" match, in other words, it matches anything
that isn't covered in the other arms.

## Binding Values
If we directly match something, like the return value from a function, we
can bind it in the arm instead of re-evaluating the expression or binding it
beforehand:

```
func age() -> s32 => return 17;

match age() {
    age @ 17 => println("felix's age is %d", age);
    age => println("vedant's age is ", age);
}
```
