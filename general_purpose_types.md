# General Purpose Types

These are the more general purpose types that we suggest you use for maximum
portability.

|Type|Description|
|----|-----------|
|int|register-sized signed integer|
|uint|register-sized unsigned integer|
|bool|unsigned 8 bits|
|rune|signed 32 bits, used for holding a Unicode codepoint|
|string|a pascal-style string, contains the string and length of the string|

The `C` pseudo-module contains the additional types `int` and `uint` which
correspond to the C `int` and `unsigned int` types. These are accessed as
`C::int` and `C::uint` respectively. More on modules later.