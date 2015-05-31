# Ideas
These are ideas for the language, syntax designs, etc.

## Traits
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