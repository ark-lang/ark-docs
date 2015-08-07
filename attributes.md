# Attributes [implemented]
Attributes allow the developer to modify or restrict behaviour for certain
declarations. An attribute is specified with square brackets surrounding an
identifier where the identifier is the attribute to enforce.

## Allowed Attributes
Here's a table of allowed attributes and *where* they're allowed:

Attribute Name | Restricted To | Options | What it does |
---------------|---------------|------------------------|
deprecated | declarations | n/a | warns the developer if they use the deprecated declaration in their code |
packed | structures | n/a | doesn't pad the given structure |
unused | declarations | n/a | supresses compiler warning on unused declarations |
c | functions | n/a | places function in C module, sets appropriate settings in the compiler for C binding |
target_os | declarations | "linux", "windows", "mac" | the tagged declaration only gets compiled on the given platform |
target_arch | declarations | "x86_64" | |
inline |
export |
call_conv |