# Attributes
![Feature Implemented](Badge_Implemented.svg)

Attributes allow the developer to modify or restrict behaviour for certain
declarations. An attribute is specified with square brackets surrounding an
identifier where the identifier is the attribute to enforce.

## Allowed Attributes
Here's a table of allowed attributes and *where* they're allowed:

_**declarations** are: function declarations, variable declarations, type declarations,
operator overload declarations, and function prototypes_

Attribute Name | Restricted To | Options | What it does |
---------------|---------------|---------|--------------|
deprecated | declarations | n/a | warns the developer if they use the deprecated declaration in their code
packed | structures | n/a | doesn't pad the given structure
unused | declarations | n/a | supresses compiler warning on unused declarations
c | functions | n/a | places function in C module, sets appropriate settings in the compiler for C binding 
target_os | declarations | "darwin", "msdos", "os/2", "win32", "wince", "cygwin", "solaris", "linux", "freebsd", "bsd/os", "bsd4", "unix" | the tagged declaration only gets compiled on the given platform 
target_arch | declarations | "x86_64", "x86" | the tagged declaration only gets compiled on the given arch 
inline | functions | "always", "never" | will inline the given function always or never
export | functions | n/a | will set external linkage to the tagged function
call_conv | functions | "fastcc", "ccc", "coldcc", "cc 10", "cc 11", "webkit_jscc", "anyregcc", "preserve_mostcc", "preserve_allcc", "cc <n>" | sets the calling convention for the tagged function 
