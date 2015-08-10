# Slices
![Feature Planned](Badge_Planned.svg)

> note this feature is still under review, check [RFC #8](https://github.com/ark-lang/rfcs/issues/8) if you are interested in helping
iron out this feature.

Slices are (as the name suggests) a "slice" borrowed from an array, this is a
great way for safely, and efficiently accessing a portion of an array without
copying any memory. A slice is a two-word object, the first word being a
pointer to the data that it refers to, and the second being the length of
the slice.

A slice is denoted with an ampersand, followed by the array to access, and
subscript notation specifying what segment of the array you wish to borrow.

```
a: [int] = [2, 4, 6, 8, 10, 12, 16, 18];
b: &[int] = &a[1..5]; // refers the slice [4, 6, 8, 10]
```