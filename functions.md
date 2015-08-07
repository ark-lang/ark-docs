# Functions [implemented]

Ark programs will have, at the least, one function; the main function.
This is the entry point of the program, i.e. where the execution of the program
will begin.

    func main() -> int {
        ...
    }

## Declaring Functions
The `func` keyword, followed by the name of the function, a list of parameters, 
an _optional_ return value denotes a function signature. A function itself is
a function signature, followed by a block. A pair of curly braces `{}` denote
a block.

```
// "func" Iden "(" ParameterList ")" [ "->" Type ] Block;

// optional return value!
func do_stuff() {
    // this returns nothing
}

// return value!
func foobar() -> int {

}
```

## Function Parameters
An identifier, followed by a colon and a Type denote a function parameter. Function
parameters must go in the function signature, between the parenthesis after the
functions identifier (name).

```
// Parameter = Iden ":" Type
// ParameterList = { Parameter "," }
func print_value(a: int) {
    // do stuff with a
}
```

As you can see, the syntax is almost like a variable. A parameter has a
name, followed by a colon `:`, and a type. Yet there are differences. You 
must specify the parameters type, and the parameter **cannot** have a 
default value:

```
// note, these are examples that will ERROR!

// default values!
func add(a: int = 5, b: int = 5) { // ERROR!
    ...
}

// no types!
func add(a, b) { // ERROR!
    ...
}
```

## Function Return Types
A function that has no return type specified will return nothing. The function in the
example above returns an integer. An arrow operator `->` followed by the Type `T` to
return specifies a return type.

```
// returns an integer
func add(a: int) -> int {
    // return keyword specifies what to return from the function
    return a + 1;
}
```

## Single Line Functions
We've introduced some syntactic sugar for single line functions, instead of
using two curly braces to denote a block, you can use the association 
operator  `=>`:

    func add(a: int, b: int) -> int => return a + b;

## Function Prototypes
Function prototypes are mostly for interoperability with C. 

, however they don't specify what
instructions the function will perform. These are most commonly used to bind
C functions. The syntax is similar, yet, instead of specifying a block
with curly braces, you terminate the function signature with a semi-colon `;`.

```
// these are function prototypes
func function_prototype() -> int;
func function_prototype_returns_nothing();
```

## Anonymous Functions

Functions do not have to specify a name; these are anonymous functions, i.e.
they are not bound to a name:

```
func do_stuff(fn: func(): int) {
    C::printf("%d\n", fn());
}

func main() -> int {
    do_stuff(func(): int { return 123; });
    return 0;
}
```

As you can see, the first function took a function as a parameter. Functions
can be passed as first-class function pointers. This is useful when
sorting lists, making callbacks, etc.

## Variadic Functions
A variadic function is a function that can take a variable amount of arguments.
To declare a variadic function, an ellipses is used as the last parameter, for
example:

```
func do_stuff(a: int, ...) {

}
```

Will take a variable amount of arguments. Note that this is for compatibility
with C, for instance the `printf` function. This means that there is no way that
you can get the arguments in Ark.