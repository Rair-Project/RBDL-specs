# Basic concepts

## Conceptual Model

A type is informally defined as a set of values associated with a way to
semantically interpret these values. RBDL document's role is to provide
all the needed tools to create the semantic interpretation for any
arbitrary value that is valid based on some specifications.

*rbdlc* provides set of primative types, these types act as the building
blocks for compound types. RBDL document is composed of one or more
compound types definitions, some of which **MAY** depend on other
compound types.