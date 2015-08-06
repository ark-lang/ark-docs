# Tagged Unions

An enum in Ark is what some may refer to as a tagged union, this allows for
multiple variants: with no data, with named (tagged) data,
and variants with unnamed data (anonymous data).

An enum, denoted with the `enum` keyword, followed by a brace, contains
the variants that define the enum:

```
enum {
    NoData,
    AnonymousData(int, int, int),
    TaggedData { x: int, y: int },    
}
```