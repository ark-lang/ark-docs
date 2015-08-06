Names can be bound to a type, you can declare custom types, or you can alias
existing types. Note that this is not a 'true' alias, and these types must be
cast to their core type.

A named type is denoted with the `type` keyword, followed by a name to bind it
to, and the type it aliases.

    type PersonAge int;
    type PersonWeight f32;
    
A type is a declaration, so it must be terminated with a semi-colon.