# Tagged Unions
![Feature Implemented](Badge_Implemented.svg)

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

Tagged union values are set and accessed with the double colon operator `::`.

```
type Tree enum {
    Node{left: ^Tree, right: ^Tree},
    Leaf(int)
};

func main() -> int {
    // make a leaf with the value 42
	x := Tree::Leaf(42);
	
	// make a leaf with the value 36
	y := Tree::Leaf(36);
	
	// make a node which contains two pointers to
	// the child leaves
	z := Tree::Node{left: &x, right: &y};

    // print out the tree contents.
    C::printf("Leaf-tag: %d\n", x);
    C::printf("Leaf-tag: %d\n", y);
    C::printf("Node-tag: %d\n", z);
    return 0;
}
```