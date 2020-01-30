# Basic concepts

## Conceptual Model

A type is informally defined as a set of values associated with a way to
semantically interpret these values. RBDL document's role is to provide
all the needed tools to create the semantic interpretation for any
arbitrary value that is valid based on some specifications.

Syntactically, types are just identifiers. In *well-formed documents*, a type *MUST* not be defined twice Some build-in types are reserved keywords
and **MUST** not be used in any other context.

*rbdlc* provides a set of primitive types, these types act as the building
blocks for compound types. RBDL document is composed of one or more
compound types definitions, some of which **MAY** depend on other
compound types.

## Template Meta-Types

For the purpose of this document, a template meta-type is informally defined
as an incomplete type. In *well-formed documents*, a template meta-type
**REQUIRES** one or more types arguments to complete the type
definition.

Syntactically, Template meta types are an identifier followed by open angle bracket symbol `<` followed by comma-separated list types followed by close angle bracket symbol `>`.

### Example:

The type `Vec` is a template meta-type and `Vec<u8>` is completed meta-type
representing an array of unsigned 8-bits integers.


If a type is used as an argument for a template meta-type, any required attributes for that argument type **MUST** be provided at the template meta-type usage.