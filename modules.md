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

If you use a directory module, you will have to specify

## Dependencies