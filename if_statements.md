# If Statements
![Feature Implemented](Badge_Implemented.svg)

An if statement is denoted with the `if` keyword, followed by a condition and
a block of statements to execute.

Parenthesis are optional as they are part of the expression rather than the
statement, though it is preferred that you exclude the parenthesis in an
if statement.

```
if x == 5 && y == 10 && z == 21 {
    ...
}
```

## Else If
An else if is denoted with an `else` keyword, followed by another if block,
these can be daisy chained.

```
if x == 5 {

}
else if y == 10 {

}
else if z == 21 {

}
```

## Else
This is performed if the previous if statements conditions are false. It is
denoted with the `else` keyword and a block.

```
if x == 5 {

}
else if y == 10 {

}
else {

}
```
