# Types
![Feature Implemented](Badge_Implemented.svg)

There are many primitive types in Ark, as well as structures that allow you to
define custom types in the language, and binding a type to a name.

## General Purpose Types

These are the more general purpose types that we suggest you use for maximum
portability.

|Type|Description|
|----|-----------|
|int|register-sized signed integer|
|uint|register-sized unsigned integer|
|bool|1 bit (though it will possibly expand to 8 bit on x64, and 4 bit on x32)|
|rune|signed 32 bits, used for holding a Unicode codepoint|
|string|a pascal-style string, contains the string and length of the string|

The `C` pseudo-module contains the additional types `int` and `uint` which
correspond to the C `int` and `unsigned int` types. These are accessed as
`C::int` and `C::uint` respectively.

## Precision Types

Precision types are usually used in embedded systems, or when you need just
a little bit more control, or you need to worry about how much memory you use.

|Type|Description|
|----|-----------|
|f32|IEEE 754 single-precision binary floating-point|
|f64|IEEE 754 double-precision binary floating-point|
|f128|IEEE 754 quadruple-precision binary floating-point|
|s8|signed 8 bits|
|s16|signed 16 bits|
|s32|signed 32 bits|
|s64|signed 64 bits|
|s128|signed 128 bits|
|u8|unsigned 8 bits|
|u16|unsigned 16 bits|
|u32|unsigned 32 bits|
|u64|unsigned 64 bits|
|u128|unsigned 128 bits|

## Type Casting

A type cast is denoted with the name of the type, followed by parenthesis, 
which contain the value to cast: `T(E)`, where T is the Type, and E is the
expression to cast.

    x: int = int(4.5); // becomes 4
    
Variables can also be casted:

    y: f64 = 4.5;
    x: int = int(y);
