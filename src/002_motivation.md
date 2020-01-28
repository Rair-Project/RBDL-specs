# Motivation

Parsing binary file formats is a very complex process, let
alone handling cases where binary files may be tampered
with to make the parsing process itself harder. RBDL aims
to simplify the process of parsing complex binary file
formats by delegating the process of writing parsers to
transpiler that accepts declarative syntax, and generating
an imperative parser for the given format.
