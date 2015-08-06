Parameters can be passed to function, they must be specified in the functions
signature. 

    // Parameter = Iden ":" Type
    // ParameterList = { Parameter "," }
    func print_value(a: int) {
        // do stuff with a
    }

As you can see, the syntax is very similar to a variable. A parameter has a
name, followed by a colon `:`, and a type. However, there are a few key
differences. You must specify the parameters type, and the parameter **cannot**
have a default value:

```
// note, these are examples that will ERROR!

func add(a: int = 5, b: int = 5) { // ERROR!
    ...
}

func add(a, b) { // ERROR!
    ...
}
```