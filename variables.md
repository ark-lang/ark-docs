# Variable Declarations

A variable is a binding of an expression to a pattern, a variable can either be
_mutable_ or _immutable_. Ark treats mutability differently than other
languages, variables are immutable by default, i.e. they are constant and
cannot be changed.

Variables are defined in two ways:

* the type is labelled explicitly
* the type is excluded, and the compiler infers it 

The syntax for a variable is the name of the variable, followed by a colon (`:`
), an optional type, an assignment operator (`=`), and an expression to assign 
to the variable. Note that because variables are __immutable__ by default, 
they **must** have an assignment.

Mutability can be toggled with the `mut` keyword, this must be before the
variable declaration. If a variable is mutable, it does **not** need an initial
expression to be assigned to it.

```
// constant variable, must have an initial value
x: int = 5; // [ "mut" ] Iden ":" Type [ "=" Expr ];
// mutable variable, initial value is optional
mut x: int;
// constant inferred variable, the type is inferred from the expression
x := 5;
// mutable inferred variable, the type is inferred from the expression
mut x := 5;
```

Remember that because something is mutable, it can later be re-assigned to
another value:

```
mut x: int = 5;
x = 10;

y: int = 10;
y = 20; // ERROR!
```

In the second example above, it causes a compile-time error because we are
trying to re-assign an immutable variable.