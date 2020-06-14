## List of rbdl attributes sorted alphabetically


### alignment

Align the start address of member in struct.

### count

Sets the number of elements.

### delimiter
Sets the ending delimiter.

### discard
Do not include getter function for members marked with this attribute.

### encoding
Allows setting encoding for `String` type. Available Encodings:
- ascii
- utf8
- utf16

### endianness

Used to set endianness for numeric values that acquire more than one byte.
Possible values:
- `le`: little endian (Default value).
- `be`: big endian.

### padding
Align the end address.

### selector
Used to set the name of the selector function in enums with externally separable
memebrs.
### selector_args
Used to set the arguments passed to enums with externally separable memebers.

### shadow
Used to specify the name of shadow enum in enums with externally sperable members.
### static
Used on members with already known values.

### unreliable
Used on members that may fail to parse correctly. In which case these members
will be ignored and parsing will continue past them. Any type referencing an
unreliable member must be unreliable as well.
