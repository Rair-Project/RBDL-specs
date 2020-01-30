# Primative Types

RBDL has various primative types, all of which **MUST** be supported by
*rbdlc*. These types represent fundemental building blocks that can be
lated user to construct compound types in rbdl document.


## Types representing Integers

All types in this category support the following attributes:

- `alignment`
- `discard`
- `padding`
- `static`
- `unreliable`

And all of them except for [`i8`](#i8) and [`u8`](#u8) support
`endianness` attribute.

### `i8`

Signed 8-bits integer \\(i\\) where \\( -128 \le i \lt 128 \\).

### `i16`

Signed 16-bits integer \\(i\\) where \\( -32768 \le i \lt 32768 \\).

### `i32`

Signed 32-bits integer \\(i\\) where \\( -2147483648 \le i \lt 2147483648 \\).

### `i64`

Signed 64-bits integer \\(i\\) where
\\( -9223372036854775808 \le i \lt 9223372036854775808 \\).

### `i128`

Signed 128-bits integer \\(i\\) where \\( -170141183460469231731687303715884105728
\le i \lt 170141183460469231731687303715884105728 \\).

### `u8`

Unsigned 8-bits integer \\(i\\) where \\( 0 \le i \lt 256 \\).

### `u16`

Unsigned 16-bits integer \\(i\\) where \\( 0 \le i \lt 65536 \\).

### `u32`

Unsigned 32-bits integer \\(i\\) where \\( 0 \le i \lt 4294967296 \\).

### `u64`

Unsigned 64-bits integer \\(i\\) where \\( 0 \le i \lt 18446744073709551616 \\).

### `u128`

unSigned 128-bits integer \\(i\\) where \\( 0 \le i \lt
340282366920938463463374607431768211456 \\).


## Types representing floating point numbers.

Floating point representation is based on IEEE 754. All types in this category support the following attributes:

- `alignment`
- `discard`
- `padding`
- `static`
- `unreliable`

### `f32`

Single-precision float.

### `f64`

Double-precision float.

## Miscellaneous Types

### `char`

Characters selected from alphabet encoded via attribute
`encoding`. Each `char` type **MUST** have `encoding` attribute.

`char` supports the following attributes:
- `alignment`
- `discard`
- `encoding`
- `padding`
- `static`


## Array Based types

All types in this category support the following attributes:

- `alignment`
- `discard`
- `padding`
- `static`
- `unreliable`
- `count`

`Vec` and `String` types additionally have the following attribute:
- `delimiter`

### `bin`

one or more unsigned *binary-digit* encoded via attribute
`encoding`. Each `bin` type **MUST** have `encoding` and `count`
attribute. The value of `count` attribute **MUST** be between 0
and 128.

### `dec`

one or more unsigned *decimal-digit* encoded via attribute
`encoding`. Each `dec` type **MUST** have `encoding` and `count`
attribute. The value of `count` attribute **MUST** be between 0
and 39.

### `hex`

one or more unsigned *hex-digit* encoded via attribute
`encoding`. Each `hex` type **MUST** have `encoding` and `count`
attribute. The value of `count` attribute **MUST** be between 0
and 32.

### `oct`

one or more unsigned *octal-digit* encoded via attribute
`encoding`.  Each `oct` type **MUST** have `encoding` and `count`
attribute. The value of `count` attribute **MUST** be between 0
and 42.

### `String`

Zero or more [`char`](#char) encoded via attribute `encoding`.
Each `String` **MUST** have `encoding` attribute. Also, each `string` must have at least either `delimiter` attribute or `count` attribute. A `string` type may have both `delimiter` and `count`, in that case a string is terminated whenever `delimiter` is met or `count` is reached whichever comes first.

### vec<T>

`TODO`
Zero or more occurences of `T`

