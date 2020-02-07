## `struct`

`struct` compound types are used to concatenate one or more types into one bigger type.

Example:

```rust,ignore
RGB: struct {
    #[encoding="ASCII", static='#', discard]
    hash: char,
    #[encoding="ASCII", count=2]
    r: hex,
    #[encoding="ASCII", count=2]
    g: hex,
    #[encoding="ASCII", count=2]
    b: hex,
}
```
The `struct` defined above is capable of successfully parsing
`#a1b2c3` where:
-  `hash` will be set to `#` but will be later discarded.
-  `r` will be set to `0xa1`.
-  `g` will be set to `0xb2`.
-  `b` will be set to `c3`.
