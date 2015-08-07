# Defer
Deferred statements are executed in FILO (first in last out) order, they occur
during lexical scoping, the arguments for defer are evaluated at the defer,
and not when the defer itself is actually executed.