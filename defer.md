# Defer
![Feature Implemented](Badge_Implemented.svg)

Deferred statements are executed in FILO (first in last out) order, they occur
during lexical scoping, the arguments for defer are evaluated at the defer,
and not when the defer itself is actually executed.

Defer is very handy for things like resource allocation:

```
mod std::io::file;

func main() -> int {
    file: ^File = File::open("shoppinglist.txt");
    defer file.close();
    
    // do some stuff with file here
    mut file_contents: str = "";
    while !file.eof() {
        file_contents = std::string::append(file_contents, file.read_line());
    }
    
    // file.close() is done here.
}
```

