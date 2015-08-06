Before we proceed to one of the more advanced topics in the Ark language, we
need to know about pointers. Pointers are used to store (or 'point to')
addresses in memory. In Ark, we denote pointers with the caret, `^`.

> Note that a raw pointer is not memory safe in Ark.

This is allowed, and you probably won't have to do this unless you know what
you're doing:

    vga_start: ^u16 = ^u16(0xB8000);