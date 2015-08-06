To get the value at the given memory address, you simply dereference using
the caret:

    x: int = 5;
    y: ^int = ^int(&x);
    z: int = ^y; // get the value at y, store in x