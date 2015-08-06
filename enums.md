An enum in Ark is what some may refer to as a tagged union, this allows for
multiple variants: variants with no data, variants with named (tagged) data,
and variants with un-named data (anonymous data).

An enum is denoted with the `enum` keyword, followed by a brace, which contains
the variants that define the enum.

```
enum {
    NoData,
    AnonymousData(int, int, int),
    TaggedData { x: int, y: int },    
}
```