# Modules
![Feature In Progress](Badge_InProgress.svg)
> This is under debate, check out the [RFC #3](https://github.com/ark-lang/rfcs/issues/3)
for modules to help.

Modules can be in two forms, a file, or a directory. Consider the
following structure:

```
    - main.ark
    - entities/
        - entity.ark
        - player.ark
        - mob/
            - slime.ark
```

All of the ark files are modules, all of the directories are modules. If a file
is inside of a directory, we refer to it as a sub-directory, however this is more
for the sake of simplicity.

Ark will determine the name of the module based on the files name and the directory
it is a child of.

## Module Access
A module is accessed using the `mod` statement. If the module is a directory,
all of the children will be used. If the module is a file, all of the modules
contents will be used.

Functions and other members of the module being used are accessed with the 
double colon operator `::`.

```
mod entities;

func main() -> int {
    player: ^entities::player::Player = entities::player::new();
    return 0;
}
```

Of course, that gets a bit tedious. So we can use just the `player` module:

```
mod entities::player;

func main() -> int {
    player: ^player::Player = player::Player::new();
    return 0;
}
```

### Implicit Modules
When you have a lot of nested modules, things can get a bit messy. To inject
modules into scope (which is not advised), you can specify multiple modules
to inject, or to inject all modules. This means you do not have to specify
the module that is being accessed:

```
mod entities::mob::*; // injects all children of the mob module
// don't use both obviously...
// mod entities::mob::{slime, cat}; // injects selected children of mob module

func main() -> int {
    slime: ^Slime = Slime::new();
}
```


## Dependencies
Dependencies will be located in a `_deps` directory. This will be in the root
of your project. The compiler will search for the `_deps` directory in the
current directory, and keep going up a directory till it finds a `_deps` folder.

Dependencies are used almost identically to modules, however you use the `dep`
keyword instead of a `mod` keyword. For instance:

```
dep mysql;

func main() -> int {
    connection: ^mysql::Connection = mysql::connect(...);
    defer connection.close();
}
```

You can also tell the compiler where your `_deps` directory is located explicitly
using the `--deps` flag, e.g. `--deps=../../_deps`.