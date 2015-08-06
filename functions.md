# Functions

Ark programs will have, at the bare minimum, one function; the main function.
This is the entry point of the program, i.e. where the execution of the program
will begin.

    func main() -> int {
        ...
    }
  
## Function Signatures
    
A function is denoted with the `func` keyword, followed by the name of the
function, a list of parameters, an optional return value, and block or semi-colon. 

```
// "func" Iden "(" ParameterList ")" [ "->" Type ] Block;
func do_stuff() {
    // this returns nothing
}
```

## Function Return Types
Function prototypes are similar to a function, however they don't specify what
instructions the function will perform. These are most commonly used to bind
C functions. The syntax is similar, yet, instead of specifying a block
with curly braces, you terminate the function signature with a semi-colon `;`.

```
// these are function prototypes
func function_prototype() -> int;
func function_prototype_returns_nothing();
```