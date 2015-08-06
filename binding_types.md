Ark has a shorthand for initialising a structure with some default values.
This shorthand is denoted with the name of the structure to initialize,
followed by a brace, which contains the values to initialize. Each value in the
intiailizer is the name of the value to initialise, followed by a colon `:` and
the initial expression to assign the value. 

```
z: Vector = Vector {
    x: 23,
    y: 32,
};
```