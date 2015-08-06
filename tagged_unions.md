We can define powerful types using tagged unions. Below is an example that
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