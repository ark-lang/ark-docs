# Match
![Feature In Progress](Badge_InProgress.svg)

Match is a control structure that takes an expression and will branch based
on its value. A match is denoted with the `match` keyword, followed by the
expression, and a block of conditions to check, or "arms". An arm is of the
form `val => expr`, and must be terminated with a semi-colon. 
When the value matches the given expression, that arms expression will be 
evaluated. Note that you can either have a single expression, or you can 
insert a block and have a group of them:
    
    match x {
        1 => ...;
        2 => ...;
        3 => ...;
        4 => {
            ...;
            ...;
            ...;
        };
    }

A match must have at least one arm, this arm is "fallback" arm; i.e. when none
of the arms match the given expression, it will evaluate whatever is in
that arm. The "fallback" arm matches the pattern `_`:

    match x {
        1 => ...; // if it' 1, do this
        _ => ...; // do this if it's anything other than 1
    }
