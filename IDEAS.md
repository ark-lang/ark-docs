# Ideas
These are ideas for the language, syntax designs, etc.

## Traits + Generics
Traits are very similar to Rust, they define the methods of the given
structure, and can be implemented by an `impl`. Traits differ from say
instances in Go, as you have to explicitly implement the trait.

    struct Bar {
        name: str;
    }

    struct Baz {
        name: str;
    }

    trait Foo {
        func fooBar();
    }

    impl Foo for Bar {
        func fooBar() {
            println("foobar method in foo for bar %s!", name);
        }
    }

    impl Foo for Baz {
        func fooBar() {
            println("foobar method in foo for baz %s!", name);
        }
    }


    // attributes look cool
    // basically generics, we need to use
    // them in this case instead of saying `value: Foo` as
    // a param, because a trait does not have a constant
    // size that is known at compile time, so the generic
    // will basically compile down to [in this case] two
    // functions one for Bar, and one for Baz, then it
    // will know the size of the given value.
    // this might be weird to understand but its 1am and im
    // ill and tired. jah bless xx
    func [T: Foo] callFooBar(value: T) {

    }

    func main() {
        // monomorphisation????
        baz: Baz = {
            name: "baz",
        };

        bar: Bar = {
            name: "bar",
        }

        callFooBar(baz);
        callFooBar(bar);
    }
