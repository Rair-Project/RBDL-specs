## Comments

### Single Line Comments

Except when being part of string literal, a single line comments start with
`//` sequence and follwed by any UTF-8 character and terminated by new line.

Example

```rust,ignore
    // This is single line comment
    Color : struct {
        // This is another single line comment
        r: u8,
        g: u8,
        b: u8,
    }
```

### Multiline Comments

Except when being part of string literal, a multiline comment starts with
`\*` sequence and terminated by `*/` sequence. Multiline comments **MAY**
contain any valid UTF-8 characters except the terminating sequence `*/`.
Multi line comments **MUST NOT** be nested.

Example

```rust,ignore
    /* This is
       a multi line
       comment
    */
    Color : struct {
        r: u8,
        g: u8,
        /* another
            multiline
            comment
        */
        b: u8,
    }
```