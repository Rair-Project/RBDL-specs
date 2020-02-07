# Compound Types

Compound types are the main building blocks of RBDL document. Compound types **MUST** fall in one of two categories: either `enum` type or `struct` type. Both categories of compound types have the following structure

```rust,ignore
#[attr_1, /* More attributes as needed */ attr_n]
CompoundTypeName: Category {
    // Atrributes are optional unless required by `Type_1`
    #[field1_attr_1, field1_attr_n]
    fiald1: Type_1,
    field2: MetaType_2<Type_n>
    // more fields as needed
    field_n: Type_m
}
```

A *well-formed document* may have Compound types without attributes [the line `#[attr_1, /* More attributes as needed */ attr_n]`) are completely optional].

Category **MUST** be either the keyword `enum` or `struct`. Compound type name **MUST** be a unique identifier amongst all other compound types and primitive types.

Compound types **MAY** be template meta types, template meta types have syntax as follows:

```rust,ignore
#[attr_1, attr_n] // More attributes as needed
CompoundTypeName: Category<MT1, MT2> // more meta types are required
{
    // Atrributes are optional unless required by `Type_1`
    #[field1_attr_1, field1_attr_n]
    fiald1: Type_1,
    field2: MT1
    #[attr_i]
    field3: MT2
    // more fields as needed
    field_n: Type_m
}
```
`MT1` **MAY** be substituted by any type. `MT2` **MUST** be subsituted by only types that the
arbitrarily specified attribute `attr_i`.


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

## `enum`

`enum` compound types are used to combine types in a way that
allows selectively using only one of them. All fields pairs
in any given `enum` **MUST** be separable either internally
or externally. For an `enum` to be part of *well-formed
document*, if one pair of fields is externally separated,
then all fields pairs in that `enum` **MUST** be externally
separated, and if one pair of fields is internally separated,
then all fields pairs in that `enum` **MUST** be internally
separated.

### `enums` with internally separable fields.

Two fields of the same enum are said to be separable
IFF there exists `n` where the data stored at given nth
offset from the start of both members are both static and
different.

Example 1:

``` rust,ignore
X: enum {
    #[static=5]
    V: u8,
    #[static=7)]
    V2: U8,
}
```
the byte `0x05` will be parsed as `X::V` while the byte `0x07` will be parsed as `X::V2`

Example2:

``` rust, ignore
V1: struct {
    #[static="SIG", encoding="ASCII", count=3]
    magic: String,
    data1: u16,
    #[static="1", encoding="ASCII"]
    Version: char,
    u: u8,
}
V2 :struct {
    #[static="SIG", encoding="ASCII", count=3]
    magic: String,
    d1: u8,
    d2: c,
    #[static="2", encoding="ASCII"]
    version: char,
    #[encoding="ASCII"]
    c: char,
}

File: enum {
    v1: V1
    v2: V2
}
```
Attempting to parse hex byte sequence `53494741423243` as
`File` will result in `File::V2` with fields as follows:
- `magic` = `"SIG"`
- `d1` = `0x41`
- `d2` = `'B'`
- `version` = `'2'`
- `c` = `'C'`

On the other hand, attempting to parse  the hex byte
sequence `53494741423142` as `File` will result in `File::V1`
with fields as follows:
- `magic` = `"SIG"`
- `data` = `0x4241`
- `version` = `'1'`
- `u` = `0x43`