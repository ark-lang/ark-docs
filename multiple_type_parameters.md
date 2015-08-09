# Multiple Type Parameters
![Feature In Progress](Badge_InProgress.svg)

When using generics you are not limited to one type parameter. This allows for 
even more complicated, but often even more useful, constructs. An example of 
using more than one type parameter could be a map:

```
type Map<Key, Value> struct {
    ...
}
```

The example works exactly like you might expect. Both type parameters can be 
used as if they were types within the body of the struct.
