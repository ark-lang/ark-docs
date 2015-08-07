# Function Receivers
You can specify the receivers of a function to make it exclusive to that particular
type. This means that in order to call the function, you need an instance of the
type that it wants in the receiver.

Function receivers are specified in parenthesis _before_ the functions identifier. A
function receiver is an "extra parameter", however the compiler will pass it to
the function implicitly in code gen. This means that functions can be called with the
dot operator.