## Ark Reference
This document is an informal specification for Ark, a systems programming language.

## Table of Contents

- [Guiding Principles](#guiding-principles)
- [Comments](#comments)
- [Modules](#modules)
  - [Module Naming](#module-naming)
  - [Using Modules](#using-modules)
- [Primitive Types](#primitive-types)
- [Precision Types](#precision-types)
- [Variables](#variables)
- [Type Inference](#type-inference)
- [Type Casting](#type-casting)
- [Literals](#literals)
  - [Numeric Literals](#numeric-literals)
  - [Text Literals](#text-literals)
  - [Mutability](#mutability)
- [Tuples](#tuples)
- [Functions](#functions)
  - [Function Return Types](#function-return-types)
  - [Single-line Functions](#single-line-functions)
  - [Exporting Functions](#exporting-functions)
  - [Specifying Calling Conventions](#calling-conventions)
- [Structures](#structures)
  - [Default structure values](#default-structure-values)
- [Implementations & Methods](#implementations-and-methods)
- [Function Prototypes](#function-prototypes)
  - [Calling C Functions](#calling-c-functions)
- [File Inclusion](#file-inclusion)
- [Pointers](#pointers)
- [Managing Memory](#managing-memory)
- [Flow Control](#flow-control)
  - [If Statements](#if-statements)
  - [Match Statements](#match-statements)
  - [For Loops](#for-loops)
    - [Infinite Loop](#infinite-loop)
    - [Conditional Loop](#while-loop)
    - [Indexed For Loop](#indexed-for-loop)
- [Option Types](#option-types)
- [Enums](#enums)
- [Arrays](#arrays)
- [Documentation comments](#documentation-comments)
- [Attributes](#attributes)
- [Traits](#traits)
- [Generics](#generics)
- [Macro System](#macro-system)

## <a id="guiding-principles"></a> Guiding Principles
Ark is a systems programming language, intended as an alternative to C. It's main purpose is to modernize C, without deviating from C's original goal of simplicity. The official Ark compiler is written in Go, with the main code backend being LLVM.

The design is motivated by the following:

* Fast
* Multi-Paradigm
* Strongly Typed
* Concise, clean and semantic syntax
* **No** garbage collection

The language should be strong enough that it can be self-hosted.

## <a id="comments"></a> Comments
Single-line comments are denoted with two forward slashes:

	// vident pls give me some bread

Multi-line comments are denoted with a forward slash followed by an asterisks. They must be closed with an asterisks, followed by a forward slash. For instance:

	/*
		vident pls give me some bread
	 \*/

Both comment types have special variations for [documentation comments](#documentation-comments).

Comments cannot be nested.

## <a id="modules"></a> Modules
Ark treats every file as a module, where the name of the module is the name of the file. This means that there are a few guidelines that should be followed to make programming Ark easier for you. **Note that it is likely we will be changing to directory-based modules soon**, where all the .ark files in a directory make up a module.

### <a id="module-naming"></a> Module Naming
Modules should be in lower case, and preferably a single word. However, if you must have a module that
is two words (or more) they should be separated with underscores. For instance, `module_name` is preffered
over `modulename` or `module name`.

### <a id="using-modules"></a> Using Modules
Say you have a module A and B, you want to use module B's children, you would `use` a module, which then
means you can explicitly use a function from the B module. To access the children of the module, you would
use the scope operator `::`. First you specify the module, so in our case `B`, followed by the scope operator `::`,
and the member to access from that module, so in the example below we access `foo()`.

For instance:

    // A
    use B;

    func main() {
        B::foo();
    }

    // B

    func foo() {
        // do stuff here
    }

## <a id="primitive-types"></a> Primitive Types
Ark provides various primitive types:

|Type|Description|
|----|-----------|
|int|register-sized signed integer|
|uint|register-sized unsigned integer|
|bool|unsigned 8 bits|
|rune|signed 32 bits, used for holding a Unicode codepoint|

The `C` pseudo-module contains the additional types `int` and `uint` which correspond to the C `int` and `unsigned int` types.

## <a id="precision-types"></a> Precision Types
The precision types are there for when you want a data type to be a specific size. If you're writing portable code, we suggest that you use the primitive types, however the precision types are available for when you need them.
Note: the C `char` type corresponds to the `i8` type.

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

## <a id="variables"></a> Variables
Unlike languages like C or C++, variables are immutable unless otherwise preceeded by the `mut` keyword. A variable can be defined like so:

	name: type;

And declared as follows:

	name: type = some_val;

Variables whose type is to be inferred can be declared as follows:

    name := some_val;
More about type inference is discussed below.

## <a id="type-inference"></a> Type Inference
The syntax for type inference is nearly identical to a typical variable declaration, all you have to do is omit the type, for instance:

	my_type := 5;
	my_double := 5.3;

Type-inference is still an early implementation, decimal values will be stored as doubles as opposed to floats. This is so you don't lose precision. Type-inference works with variables, literals, and function calls. For instance:

	a := 5;
	b := 10;
	c := a + b * 2;

We can also infer types in the following manners:

    func add(a: int, b: int): int -> a + b;
    x := add(5, 5); // x is int

    struct Cat {
    	name: str,
    	weight: float,
    	age: int
    }
    pew: Cat;
    b := pew; // b is of type Cat and contains the values that the instance `pew` contains

    enum Wew {
    	WOW,
    	MEOW
    }

    mew := Wew::WOW;

    ar : []int = [ 1, 2, 3, 4 ];
    b := ar[2]; // b is of type int


## <a id="type-casting"></a> Type Casting
In Ark, type casting can be done as follows:

    mut my_val: float = 1.3;
    mut my_val_two: int = int(my_val); // my_val_two is now 1

To do type casting, the type its being casted to must be added, followed by the value being casted in parentheses.

    val: int = int(4.5); // val is now 4

## <a id="literals"></a> Literals

### <a id="numeric-literals"></a> Numeric Literals
Integer literal:

	1234

You can use underscores in integer literals to improve readability:

	1_234

Binary literal:

	0b10011010010

Hex literal:

	0x4d2

Octal literal:

	0o2322

Floating-point literals contain a period. If a literal lacks a period, or you want to specify the precision, use the `f` suffix for 32 bits (`f32`), the `d` suffix for 64 bits (`f64`), or the `q` suffix for 128 bits (`f128`):

	12.34

### <a id="text-literals"></a> Text Literals
A string literal is enclosed with double-quotes:

    "Hello!"

A character literal is enclosed with single-quotes:

    'a'

The following escape sequences are available:

|Sequence|Description|
|--------|-----------|
|`\a`|alarm/bell|
|`\b`|backspace|
|`\f`|formfeed|
|`\n`|newline|
|`\r`|carriage return|
|`\t`|horizontal tab|
|`\v`|vertical tab|
|`\\`|backslash|
|`\'`|single quotation mark|
|`\"`|double quotation mark|
|`\?`|question mark|
|`\oNNN`|octal number|
|`\xNN`|hex number|

### <a id="mutability"></a> Mutability
When a variable is mutable, it can be mutated or changed. When a variable is immutable, it cannot be changed. By default, Ark assumes that a variable you've defined is immutable. You can however, specify the `mut` keyword before the declaration. This will inform the compiler that you intend to modify the variable later in the program.
For instance:

	x: int = 5;
	x = 10;         // ERROR: x is constant!

We can also error it like so:

	x: int;         // ERROR: no value assigned for constant!

Why? Because variables are treated as constants unless otherwise specified; therefore they must have a value assigned on definition.

## <a id="tuples"></a> Tuples
A tuple is defined in a manner similar to a variable. However you specify the type and the values it contains within the pipe symbol (`|`). For instance:

	mut my_tuple: |int, int|;

To initialize the tuple with values, we use a similar notation to the tuples signature, and we wrap the values in pipes. The order should be the same as the order used in signifying the types in the signature.
For instance:

	// this is valid
	mut my_type: |int, double| = |10, 3.4|;

	// the following errors, note the order of the types/values.
	// the int must come before the double in the values
	mut another_type: |int, double| = |3.4, 10|;

## <a id="functions"></a> Functions
A function defines a sequence of statements and an optional return value, along with a name, and a set of parameters. Functions are declared with the keyword `func`, followed by a name to identify the function, and then a list of parameters. Finally, an optional colon `:` followed by a return type, e.g. a struct, data type or `void` can be added. Note that if you do not specify a colon and a return type, it is assumed that the function returns the `void` type. **Note
that the default calling convention for function in Ark is fastcc!**

An example of a function:

	mut int result;

	// if the function returns void,
	// the return type is optional, thus
	// func add(x: int, y: int) { }
	// is perfectly valid.
	func add(x: int, y: int): void {
		result = x + y;
	}

### <a id="function-return-types"></a> Function Return Types
We can simplify this using a return type of `int`, for instance:

	func add(x: int, y: int): mut int {
		return x + y;
	}

### <a id="single-line-functions"></a> Single-line Functions
If you have a function that consists of a single statement, it's suggested that you use the `->` operator instead of an entire block. Single line functions also take the last expression and return it, so you do not have to specify a return statement.

	func add(a: int, b: int): int -> a + b;

You can still write normal functions that have no return type like so:

    func sayHello(name: str): void -> C::printf("Hello %s\n", name);
    // same as
    func sayHello(name: str) -> C::printf("Hello %s\n", name);

### <a id="exporting-functions"></a> Exporting Functions
To allow external linkage to a function, you define the function as you would typically, however before the `func` keyword, you specify the function is external by writing the `export` modifier:

    export func do_stuff() {
        // do stuff here
    }

### <a id="calling-conventions"></a> Specifying Calling Conventions
You may also specify a calling convention **if you are exporting a function**. To do so you would use
an attribute, specifically the "call_conv" attribute. In the attribute value, you would specify the calling
convention:

    [call_conv="fastccc"]
    export func do_stuff() {

    }

### <a id="calling-c-functions"></a> Calling C Functions
You can bind a C function by simple declaring a function prototype, i.e. a function without a body and tag
the function with the `c` attribute. This will tell the compiler that the function you have defined is a C
function. When you specify this attribute, the compiler will store the function inside of a C module. This
means that when you call a c-binded function, you must prefix the call with `C::` as you are accessing the
function from the C module. Note that every module has its own private C module, in which all of the bindings
specified are stored.

    [c] func printf(fmt: str, ...): int;

The above snippet will create a binding for the `printf` function, which can be called as follows:

    func main(): int {
        C::printf("hello world %d!\n", 5);
        return 0;
    }

## <a id="structures"></a> Structures
A structure is a complex data type that defines a list of variables all grouped under one name in memory:

	struct Cat {

	}

A structure contains variable definitions separated by commas. Trailing commas are allowed. For example, we can write a structure to define a Cat's properties like so:

	struct Cat {
		name: str,
		age: int,
		weight: float
	}

While structures are more complex types, they are instantiated just as any ordinary type, such as an integer or a float:

	mut terry: Cat;

Note how the structure declared is mutable. This is because we aren't declaring any of the fields in the structure. We can define the contents of the structure like so:

	terry: Cat = {
		name: "Terry",
		age: 2,
		weight: 3.12
	};

The struct initializer is a statement, therefore it must be terminated with a semi-colon. Note that the values in the struct initializer do not have to be in order, but we suggest you do to keep things consistent.

### <a id="default-structure-values"></a> Default structure values
A structure's members can also be assigned default values:

	struct Cat {
		name: str = "Terry",
		age: int = 0
	}

In this example, upon creation of an instance of the `Cat` structure, the value of the `name` member will by default be `"Terry"`, provided a custom value has not already been assigned. Below, we create an instance of the structure `Cat`, called `cat`, and *only* give its `age` member a value. This means that the `name` member of the instance already holds the default value "Terry".

	cat: ^Cat = {
		age: 12
	};

Therefore running

	C::printf("%s is %d years old\n", cat.name, cat.age);

will give us:

	Terry is 12 years old

## <a id="implementations-and-methods"></a> Implementations & Methods
An `impl` is an implementation of the given `struct`, or structure. An implementation contains methods zthat 'belong' to the structure, i.e you can call these methods through the given structure and the methods can manipulate their owners data. First we must have a struct that will be the owner of these methods:

	struct Person {
		name: str,
		age: int,
		gender: Gender
	}

We can then define various methods for this structure. To do so, they must be wrapped in an `impl`. The `impl` or implementation, must declare what it is implementing. In this case `Person`.

	impl Person {
		...
	}

The functions for `Person` are declared inside of this `impl`:

	impl Person {
		func say() {
			println("Hi my name is %s and I'm %d years of age.", self.name, self.age);
		}
	}

To access the structure that the we're implementing, you use the `self` keyword. To call the `say` function we defined, you need to have an instance of the structure. Functions can then be accessed via the dot operator:

	func main(): int {
		p: Person;
		p.say();
	}

## <a id="pointers"></a> Pointers
The caret (`^`) is what we use to denote a pointer, i.e something that points to an address in memory. The ampersand (`&`) symbol is the **address of** operator. For instance:

	x: int = 5;
	y: ^int = &x;

In the above example, we create an integer `x` that stores the value `5` somewhere in memory. The variable `y` is pointing to the address of `x`. Printing out the value of `y` will give you random gibberish denoting the memory chunk in which `x` is located. This is because it just stores the address to `x`. Now if we want to access the value at the address of x, we must *dereference* the pointer that points to it. This is again done with the caret (`^`), for example:

	x: int = 5;     // 5
	y: ^int = &x;   // 0xDEADBEEF       (somewhat arbitrary address)
	z: int = ^y;    // 5                (get the value at our address 0xDEADBEEF)

We've introduced a new variable `z`, that stored the value at the address `y`, in other words, the value of `x`.

## <a id="managing-memory"></a> Managing Memory
Ark is not a garbage collected language, therefore when you allocate memory, you must free it after you are no longer using it. We felt that, as unsafe as it is to rely on the user to manage the memory being allocated, performance takes a higher precedence. Although garbage collection makes things fool-proof and removes a significant amount of workload from the user, it inhibits the performance we were going for.

Memory is allocated, freed, and re-allocated using the standard library, specifically `mem`. You would import this into your code, and use the respective methods to manage your memory. The `mem` library contains three methods, namely "free", "alloc", "realloc", and "size_of".

    // use the mem library!
    !use "mem"

    func main() {
        // allocate a block of memory that can store
        // 32 integers.
        x: ^int = Block::alloc(Block::size_of(int) * 32);

        // realloc
        x = Block::realloc(x, Block::size_of(int) * 64);

        // free the memory we allocated
        Block::free(x);
    }

## <a id="flow-control"></a> Flow Control
### <a id="blocks"></a> Blocks
There are two kinds of blocks, `do` blocks, and a typical block. The difference between
the two is scope. The first kind of block, a `do` block introduces no scope, whereas
a normal block **does** introduce scope. They are almost syntactically identical, however
a `do` block has the keyword `do` before the curly braces:

    do {
        // no scope!
    }

    {
        // scope!
    }

### <a id="deferred-statements"></a> Deferred Statements
Deferred statements occurr in lexical scoping, in other words, a deferred statement is
"set back" till the scope in which the deferred statement was declared is popped. They are
executed in first in last out order, and arguments are evaluated _at_ the defer statement.

    [c] func printf(fmt: str, ...): int;

    func println(mess: str) {
        C::printf("%s\n", mess);
    }

    func main(): int {
        defer println("printed last");
        defer println("printed second-to-last");

        if true {
            defer println("printed second");
            defer println("printed first");
        }

        return 0;
    }

### <a id="if-statements"></a> If Statements
If statements are denoted with the `if` keyword followed by a condition. Parenthesis around the expression/condition are optional:

	if x == 1 {
		....
	}

### <a id="match-statements"></a> Match Statements
Match statements are very similar to C's `switch` statement. Note that by default, a match clause will break instead of continuing to other clauses. A match is denoted with the `match` keyword, followed by something to match and then a block:

	match some_var {
		...
	}

Within the match statement are match clauses. Match clauses consist of an expression, followed by a single statement operator `->`, 
or an arrow **and** a block if you want to do multiple statements:

	match x {
		0 -> ...;
		1 -> {
			...
		};
	}

Each clause must end with a semi-colon, including blocks.

### <a id="for-loops"></a> For Loops
For loops are a little more different in Ark. There are no while loops, or do-while loops.

#### <a id="infinite-loop"></a> Infinite Loop
If you want to just loop till you break, you write a for loop with no condition, for instance:

	for {
		C::printf("loop....\n");
	}

#### <a id="while-loop"></a> Conditional Loop
If you want to loop while a condition is true, you do the same for loop, but with a condition after the `for` keyword:

	for x {
		C::printf("loop while x is true\n");
	}

#### <a id="indexed-for-loop"></a> Indexed For Loop
Finally, if you want to iterate from A to B or vice versa, you write a for loop with two conditions - the first being the range and the second being the step. For instance:

	for x < 10, x++ {
		...
	}

Also note that `x` is not defined in the for loop; it must be defined outside of the loop. For instance:

	mut x: int = 0;
	for x < 10, x++ {
		...
	}

## <a id="option-types"></a> Option Types
Option types represent an optional value- they can either be `Some` or `None`, i.e. they can either have a value, or not have a value -- they are often paired with a `match` statement. An option type is denoted with an open angular bracket, the type that is optional, and a closing angle bracket.

	func example(a: ?int) {
		match a {
			Some -> C::printf("wow!\n");
			None -> C::printf("Damn\n");
		}
	}

Here's an example with an `Option` type as a function return type. These are especially useful for cleanly checking for errors in your code. Note that the example below is semi-pseudo code, i.e. the functions that it calls do not exist, since we haven't written any file IO libraries for Ark yet.

	func read_file(name: str): ?str {
		read = non_existent_file_reading_function(str, ...);
		if read {
			return Some(read.contents);
		}
		return None;
	}
	func main() {
		file_name: str = "vident_top_ten_favorite_bread_types.md";
		file_contents: str = read_file(file_name, ...);

		match file_contents {
			Some -> C::printf("file %s contains:\n %s", file_name, file_contents),
			None -> C::printf("failed to read file!"),
		}
		return 0;
	}

## <a id="enums"></a> Enums
**TODO UPDATE FOR TAGGED UNIONS**
An enumeration is denoted with the `enum` keyword, followed by a name and a block. The block contains the enum items, which are identifiers (typically uppercase) with an optional default value. Enum items must be terminated with a comma (excluding the final item in the enumerion). For example:

	enum DogBreed {
		POODLE,
		GRAYHOUND,
		SHIH_ZU,
	}

To refer to the enum item, you need to specify the name of the enumeration, followed by two colons `::`, and finally the enum item.

	func main(): int {
		match x {
			DogBreed::POODLE -> ...;
		}
	}

## <a id="arrays"></a> Arrays
**TODO DYNAMIC ARRAYS**
An array is a collection of data that is the same type. They are defined as follows:

	mut name_of_array: [size]type;

Note that the size of the array is a must if you are not statically initializing the array. For instance, an array of points would be defined as follows:

	mut points: [5]int; // can hold up to 5 points.

You can then set the values of the array by specifying the name of the array to modify, an opening square bracket, the index of the array that you are changing, and a closing bracket:

	// set the first value in the array to be 10.
	points[0] = 10;

To retrieve a value in an array, you do the same syntax, but you do not assign a value. For instance, I could store the value in another variable like so:

	x: int = points[0]; // x is now 10

### Statically Initializing an array
If you already know what data needs to be stored in the array, you can simply initialize the array on its declaration:

	some_array: []int = [
		0, 1, 2, 3, 4
	];

Note that I did not specify a size in the block this time, and that there is also a semi-colon `;` at the end of the initializing block, this is because it's still a statement.

## <a id="documentation-comments"></a> Documentation Comments
Block comments and single-line comments both special syntax for documentation comments. They are `/** */` and `///` respectively.

The following can be documented by having doc comments placed above them (*with no empty lines*):

* public function/method declarations
* public variable/constant declarations
* public struct/enum declarations (note that you can also use doc comments on individual struct members)
* module declarations [TODO how will this work?]

Markdown is supported.

## <a id="attributes"></a> Attributes
Attributes describe a unique quality that belongs to something, be it a function, structure,
variable, trait, etc. Attributes are a guide to the compiler, they clarify something, or they
tell the compiler what to do. Currently, there are only a few simple attributes. An attribute
is denoted with square brackets, typically before the statement it belongs to.

For instance, I could tell the compiler that the given function is deprecated and should not be
used, it will also warn the programmer if they are using a deprecated function/variable/etc:

    [deprecated]
    func something(): bool {
        // something here
    }

If this function is called, the user will be warned that it is deprecated.

Below is a list of current attributes and their actions:

| unused | the compiler will not complain if the following declaration is unused. |
|-------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `deprecated` | if the following declaration is used in any of  your code, then the compiler will complain that it is deprecated and should not be used. |
| `c` | the following declaration is a c-binding, this will also store the declaration in the modules private C module. |
| `call_conv="value"` | this will set the calling convention for the following function. Legal values include: `"fastcc"`, `"ccc"`, `"coldcc"`, `"cc 10"`, `"cc 11"`, `"webkit_jscc"`, `"anyregcc"`, `"preserve_mostcc"`, `"preserve_allcc"`, `"cc <number>"`. |
| `packed` | the following structure will not be aligned by the compiler. |

## <a id="traits"></a> Traits
Traits are a set of functions that can be inherited by a structure. Traits must be explicitly
implemented for a given structure using the `impl` (implementation) we discussed earlier in this
document.

A trait is defined like so:

    trait TraitName {
        func foo();

        func defaultFunc() {
            // do stuff
        }
    }

They are then implemented for a stricture, e.g:

    struct Bar {

    }

    trait Foo {
        func fooBar();
    }

    impl Foo for Bar  {
        func fooBar() {

        }
    }

We can then call these functions like so:

    func main(): int {
        bar: Bar;
        bar.fooBar();
        bar.defaultFunc();
        return 0;
    }

Something like a Trait can be passed around, but we don't know the
size of the trait at compile-time, for instance, given the previous
example of Traits

    trait Foo {

    }

    impl Foo for Bar {

    }

And we want to pass something to a function as long as it inherits
the trait `Foo`. Right, so let's just use that trait in a parameter:

    func doStuff(a: Foo) {

    }

Well unfortunately, that won't work out too well. The trait doesn't
have a constant size that is known at compile time. So we need to use
generics!

Currently, generics are defined using the attributes we discussed
earlier. So we have to define that `T` can be `Foo`, and then we can
use `T` in the next declaration:

    [T: Foo] // this syntax is under debate
    func doStuff(a: T) {
        // yay it works!
    }

## <a id="generics"></a> Generics
**TODO**
Generics is the idea of generalizing types to be more diverse, as opposed
to constraining yourself to a specific type. Generics are great for making
code concise and avoiding code duplication.

## <a id="macro-system"></a> Macro System
We're still thinking about this, want to suggest an idea/have your say? Post an issue, or comment
on an existing one (relevant to the topic) [here](https://github.com/ark-lang/ark/issues).
