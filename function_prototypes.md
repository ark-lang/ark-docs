Function prototypes are similar to a function, however they dont specify what
instructions the function will perform. These are most commonly used to bind
C functions. The syntax is very similar, however, instead of specifying a block
with curly braces, you terminate the function signature with a semi-colon `;`.

```
// these are function prototypes
func function_prototype(): int;
func function_prototype_returns_nothing();
```