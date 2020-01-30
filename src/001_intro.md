# Introduction

RBDL is declarative Domain Specific Language designed to formally describe binary file formats. Its main objective is to decouple the parsing of executable files (as well as any file-based binary structure) from the remaining process of reverse engineering. RBDL is capable of handling binary file formats with variable header size and optional components. RBDL supports recovering gracefully while parsing partially corrupted data.

RBDL does not depend on any language. However, RBDL files are intended to be later transpiled into another language that implements the mechanism required for parsing the file format in question.

WARNING: This product targets languages known to the State of California to cause cancer
and birth defects or other reproductive harm (pun intended).

### Credits

RBDL specifications is heavily inspired by [C standards ISO/IEC 9899:2011](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n1124.pdf), [Standard for ProgrammingLanguage C++](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4296.pdf), and
[The Rust Reference](https://doc.rust-lang.org/reference/introduction.html).