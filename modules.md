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