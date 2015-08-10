# Comments
![Feature Implemented](Badge_Implemented.svg)

There are two types of comments in Ark:

* single line comments
* multiple line comments

However there are a few rules when commenting that you should follow, as
well as a few extra things Ark allows you to do.

## Single Line Comments
A single line comment is denoted with two forward slashes `//`.

```
// this is my comment
// woah, here's another one!
```

Documentation comments are specified with _three_ forward slashes, this is
for the documentation generator.

```
/// this does a thing
```

## Multiple Line Comments
Comments that span over multiple lines are denoted with a forward slash,
followed by an asterisks, and they must be closed with an asterisks and
a backwards slash.

```
/*
    this is my comment!
*/
```

Documentation comments are specified with two opening asterisks, and you can 
close with two to make it look pretty.

```
/**
    This does a thing
    nice!
**/
```

### Nested Comments
Comments _can_ be nested:

```
/*
    /* hi there */
    
    /* this is my nested comment */
*/
```