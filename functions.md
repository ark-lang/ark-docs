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