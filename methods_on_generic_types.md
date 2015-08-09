# Methods on Generic Types
![Feature In Progress](Badge_InProgress.svg)

Continuing from the previous example you might notice something missing. How 
are you supposed to actually use the structure without copy-pasting code everywhere? Usually you would implement a method on the structure, but would 
that work here? Luckily methods can be declared on generic types aswell with 
almost no syntactical overhead. An example of defining a method an our `Map` 
is as follows:

```
func (Map<Key, Value>) Get(key: Key): Value {
    ...
}
```

When defining a method on a generic type, the type parameters given to the type carry over to the function that's being implemented. Thus the `Get` 
function has knowledge of `Map`s two type parameters, `Key` and `Value`, and 
can use them just like any other type. Note that the names do not have to 
match with the names used to define the type, so `Map<Key, Value>` might as 
well have been written `Map<K, V>` if the author felt that more fitting.
