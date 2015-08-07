# Tagged Unions [implemented]

An enum in Ark is what some may refer to as a tagged union, this allows for
many variants: with no data, with named (tagged) data,
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

We can define powerful structures using tagged unions. Below is an example that
represents a small extract for an abstract syntax tree.

```
type Node struct {
    children: ^Node,
    kind: NodeKind,
};

type NodeKind enum {
    Variable(VariableData),
};

type VariableData struct {
    name: string,
    // some values here that
};
```
