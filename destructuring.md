# De-structuring

## De-structuring tuples

Tuples can be de-structured by binding values to an identifier:

```
pair := (0, -5);
match pair {
    pair(0, b) => /* do stuff with b */;
    pair(a, 0) => /* do stuff with a */;
    pair(a, b) => /* do stuff with a and b */;
}
```