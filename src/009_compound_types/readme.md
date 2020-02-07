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
