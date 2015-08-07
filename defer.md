# Defer
Deferred statements are executed in FILO (first in last out) order, they occur
during lexical scoping, the arguments for defer are evaluated at the defer,
and not when the defer itself is actually executed.

Defer is very handy for things like resource allocation:

```
mod std::io::file;

func main() -> int {
    file: ^File = File::open("shoppinglist.txt");
    defer file.close();
}
```