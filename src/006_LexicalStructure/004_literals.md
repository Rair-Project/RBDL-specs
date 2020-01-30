## Literals
RBDL supports several types of literals:
- [*boolean*](#bolean-literals)
- [*byte-character*](#byte-character-literal)
- [*byte-string*](#byte-string-literals)
- [*character*](#character-literals)
- [*floating-point*](#floating-point-literals)
- [*integer*](#integer-literals)
- [*string*](#string-literals)
- [*vector*](#vector-literals)

### Boolean Literals

Boolean literals **MUST** be either the keyword `true` or the keyword `false`.

### Byte-Character Literals

A *byte-character* literal **MUST** be a single ASCII character enclosed
in single quotes preceded by character `b` as in `b'x'`. *Byte-Character*
literals **MUST** follow [byte escaping](#byte-escaping) rules and
[quote escaping](#quote-escaping) rules when needed.

*Byte-character* literals are to be interpreted as `u8` atomic type.

### Byte-String Literals

A *byte-string* literal **MUST** be one or more ASCII characters enclosed in
double-quotes preceded by character as in `"xyz"`. *Byte-String* literals
**MUST** follow [byte escaping](#byte-escaping) rules and
[quote escaping](#quote-escaping) rules when needed.

*Byte-string* literals are to be interpreted as `Vec<u8>` type where each
element in the *vector* represents single *byte-character*.


### Character Literals

A *character* literal **MUST** be a single UTF-8 character enclosed
in single quotes as in `'x'`. *Character* literals **MUST** follow
[ASCII escaping](#ascii-escaping) rules, [Unicode escaping](#unicode-escaping)
rules and [quote escaping](#quote-escaping) rules when needed.

### Floating-Point Literals

A *floating-point* literal has one of two forms:

- One or more *decimal-digits* followed by a period character `.`
 optionally followed by one or more *decimal-digits* optionally
 followed by an exponent.

- One or more *decimal-digits* followed by an exponent.

Where exponent is either the character `e` or `E` followed by
one or more *decimal-digits*.

Character `_` **MAY** be used as a visual separator between digits, and they
**MUST** be ignored by *rbdlc*.

Example:
`1_234.567_8` is the same as `1234.5678`.

### Integer Literals

An integer literal has one of several forms:

- `0`
- `0b0`
- `0o0`
- `0x0`
- A non zero *decimal-digit* followed by an arbitrary sequence of *decimal-digits*.
- `0x` followed by a non zero *hex-digit* followed by an arbitrary sequence of *decimal-digits*.
- `0o` followed by non zero *octal-digit* followed by an arbitrary sequence of *octal-digits*.
- `0b` followed by non zero *binary-digit* followed by an arbitrary sequence of *binary-digits*.

Character `_` **MAY** be used as a visual separator between digits, and they
**MUST** be ignored by *rbdlc*.

### String Literals

A *string* literal **MUST** be one ore more UTF-8 character enclosed
in double quotes as in `"xyx"`. *String* literals **MUST** follow
[ASCII escaping](#ascii-escaping) rules, [Unicode escaping](#unicode-escaping)
rules and [quote escaping](#quote-escaping) rules when needed.


### Vector Literals

A *vector* literal **MUST** be one or more literals of the same kind separated
by a comma `,` and enclosed in square brackets as in `[1, 2, 3, 4]`. The last
element in a vector literal **MAY** be separated from the closing square bracket
`]` by a comma `,` as in `[1, 2, 3,]`. Two *vector* literals are said to have the
same type if and only if all the elements inside both vectors have the same literal
type.

### ASCII Escaping

| ASCII Escape sequence | Name |
|-------------------------------|------------------|
|`\n` | New line |
|`\r` | Carriage return |
|`\t` | Tab |
|`\\` | Single backslash |
|`\0` | Null byte |
|`\x` followed by 2 *hex-digits*| Hex byte <= 0x7F |


### Byte Escaping

| Byte Escape Sequence | Name |
|-------------------------------|--------------------|
|`\n` | New line |
|`\r` | Carriage return |
|`\t` | Tab |
|`\\` | Single backslash |
|`\0` | Null byte |
|`\x` followed by 2 *hex-digits*| Arbitrary hex byte |


### Quote Escaping

| Quote Escape sequence | Name |
|------------------------|--------------|
| `\'` | Single Quote |
| `\"` | Double Quote |

### Unicode Escaping


| Unicode Escape sequence | Name |
|---------------------------------|------------------------|
| `\u` followed by 6 *hex-digits* | Unicode character code |
