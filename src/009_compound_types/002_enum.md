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

Two fields of the same enum are said to be internally separable
IFF there exists `n` where the data stored at given nth
offset from the start of both members are both static and
different.

Example 1:

``` rust,ignore
X: enum {
    #[static=5]
    V1: u8,
    #[static=7]
    V2: U8,
}
```
the byte `0x05` will be parsed as `X::V` while the byte `0x07` will be parsed as `X::V2`

Example 2:

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
    d2: char,
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

### `enums` with externally separable fields.

`enum` compound types with externally separable fields **MUST** use
`shadow`, `selector` and `selector_args` attributes to define how
member fields are to be separated.

`shadow` attribute is used on externally separable `enum` to create minimal externally separable `enum` (or the nearest equivalent in the *target language*) that resembles the structure of the `enum` to be shadowed.

`selector` attribute represents the name of a function written in *target language* that takes arguments specified by `selector_args` and return a variable of a type specified by `shadow`. Unlike `shadow`, both `selector` and `selector_args` are not used when an `enum` with externally separable fields is defined, but instead, they are used when then `enum` is used.

`selector_args` takes a list of fields all of which must be drawn from the parent of our `enum` with externally separable fields.


Example:


File: *grammar.rbdl*

```rust,ignore
Version: enum {
 #[static=0]
 V0: u8
 #[static=1]
 V1: u8
}
#[shadow=DataShadow]
Data : enum {
 D8: u8,
 D16: u16,
}

FullFile: struct {
 version_a: Version,
 version_b: Version,
 #[selector=version_sel, selector_args=[version_a]]
 data_a: Data,
 #[selector=version_sel, selector_args=[version_b]]
 data_b: Data,
}
```

File: *grammar.rs*
```rust,ignore
rbdl_include!("grammar.rdbl")

fn version_sel(version: &Version) -> DataShadow {
 match version {
 Version::V0 => DataShadow::D8,
 Version::V1 => DataShadow::D16
 }
}
```
The snippet above defines file type with 4 completely different versions namely `0.0`, `0.1`, `1.0`, `1.1`. Where in the `X.Y` format, `data_a` of the `FullFile` struct depends on the `X` part while `data_b` depends on the `Y` part.

In file *grammar.rbdl*, we first define an enum with internally separable variables to represent both the `X` and the `Y` part of the version. The `Data` enum represents the data that is either depending on `X` or `Y`. `shadow=DataShadow` creates another `enum` called `DataShadow` that mimics the same structure and members name of `Data`.

In rust, `DataShadow` will look like this:

```rust
enum DataShadow {
    D8,
    D16
}
```

The `selector` attribute applied to both `data_a` and `data_b` sets the function that will externally determine which version of `Data` they are to be called `version_sel`. The function identified by `selector` (which is `version_sel`) always returns datatype specified by `shadow` (which is `DataShadow`). The arguments sent to the `version_sel` function are set via the attribute `selector_args` which happens to be `version_a` in case of `data_a` and `version_b` in case of `data_b`.