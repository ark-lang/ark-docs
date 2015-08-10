# Type Restrictions
![Feature In Progress](Badge_InProgress.svg)

It is not always the case that a generic function/type wishes to work with *all* types. To allow for the creation of functions/types like this we use the 
concept of **type restrictions**. A type restriction is, as the name suggests, 
a way to lock down the types that can be used with a generic type/function. To 
ease explaining we start with an example:

```
type Vector3<T: Number> struct {
    x: T, y: T, z: T
}
```

Again we have a type with a type parameter `T`, this time the parameter is 
followed by a colon and an identifier. This identifier, in our case `Number`, 
is the name of an interface. It means that, `T` **must** implement the 
interface `Number` to be usable in a `Vector3`.

Just like you can use multiple type parameters, you can also use multiple type 
restrictions. An example of this is the following:

```
type HashMapWithIteratorKeysForSomeReason<Key: Hash & Iterator, Value> struct {
    ...
}
```

This means that `Key` has to both interfaces, `Hash` **and** `Iterator`. 
Again, the limit to the amount of restrictions you can use is your 
imagination. And common sense.
