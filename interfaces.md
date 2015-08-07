# Interfaces
Interfaces are named collections of method signatures. In Ark, interfaces are implicit,
which means that if something has the methods defined in an interface `A`, it will
implicitly implement interface `A`. This allows for duck typing, or in
other words: 

> If it looks like a duck, and quacks like a duck, it's a duck"

The `interface` keyword, followed by a block that consists of method signatures
will denote an interface. Method signatures defined in an interface do not 
need to specify the `func` keyword.

```
type Geometry interface {
    area() -> f64;
    perimeter() -> f64;
};
```

Now if we introduce some structures that implement the same methods in the interface
we defined, they will implement `Geometry` implicitly.

```
type Rectangle struct {
    width: f64,
    height: f64,
};

type Circle struct {
    radius: f64,
};

func (r ^rect) area() -> f64 {
    return r.width * r.height;
}

func (r ^rect) perimeter() -> f64 {
    return (r.width * 2) * (r.height * 2);
}

func (c ^circle) area() -> f64 {
    return std::math::PI * c.radius * c.radius;
}

func (c ^circle) perimeter() -> f64 {
    return 2 * std::math::PI * c.radius;
}
```