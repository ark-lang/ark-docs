# Modules [in progress]
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
A module is accessed using the `use` statement. If the module is a directory,
all of the children will be used. If the module is a file, all of the modules
contents will be used.

Functions and other members of the module being used are accessed with the 
double colon operator `::`.

```
use entities;

func main() -> int {
    player: ^entities::player::Player = entities::player::new();
    return 0;
}
```

Of course, that gets a bit tedious. So we can use just the `player` module:

```
use entities::player;

func main() -> int {
    player: ^Player = Player::new();
    return 0;
}
```

### Module Aliasing

Notice how we don't specify the module we access from on function calls? This
is because using a sub-module (or file module) will allow us to implicitly
call the children of said module. However, we can specify the `as` keyword
to be more explicit.

```
use entities::player as entity; // as player is fine too!

func main() -> int {
    player: ^entity::Player = entity::Player::new();
    return 0;
}
```

We can also specify to use more than one child-module with some syntactic
sugar:

```
use entities::{player, mob::slime};

func main() -> int {
    player: ^Player = Player::new();
    slime: ^Slime = Slime::new();
    return 0;
}

```

And again, we can use the as keyword. Since we are using the brace syntactic
sugar, we must also specify each "alias":

```
use entities::{player, mob::slime} as {player, slime};

func main() -> int {
    player: ^player::Player = player::Player::new();
    slime: ^slime::Slime = slime::Slime::new();
    return 0;
}
```


## Dependencies