A function that has no return type specified will return nothing. In the 
example above, we return an integer. A function return type is denoted with 
a colon `:`, followed by the type that the function returns.

    // returns an integer
    func add(a: int): int {
        // return keyword specifies what to return from the function
        return a + 1;
    }