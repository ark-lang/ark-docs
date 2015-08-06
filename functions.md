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

## Function Parameters
Parameters can be passed to function, they must be specified in the functions
signature. 

```
// Parameter = Iden ":" Type
// ParameterList = { Parameter "," }
func print_value(a: int) {
    // do stuff with a
}
```

As you can see, the syntax is very similar to a variable. A parameter has a
name, followed by a colon `:`, and a type. However, there are differences. You 
must specify the parameters type, and the parameter **cannot** have a 
default value:

```
// note, these are examples that will ERROR!

func add(a: int = 5, b: int = 5) { // ERROR!
    ...
}

func add(a, b) { // ERROR!
    ...
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

## Function Prototypes

Functions do not have to specify a name; these are anonymous functions, i.e.
they are not bound to a name:

```
func do_stuff(fn: func(): int) {
    C::printf("%d\n", fn());
}

func main(): int {
    do_stuff(func(): int { return 123; });
    return 0;
}
```

As you can see, the first function took a function as a parameter. Functions
can be passed as first-class function pointers. This is mostly useful when
sorting lists, making callbacks, etc.