Functions do not have to specify a name; these are anonymous functions, i.e.
they are not bound to a name:

    func do_stuff(fn: func(): int) {
        C::printf("%d\n", fn());
    }

    func main(): int {
        do_stuff(func(): int { return 123; });
        return 0;
    }

As you can see, the first function took a function as a parameter. Functions
can be passed as first-class function pointers. This is mostly useful when
sorting lists, making callbacks, etc.