# Terms, keywords, and symbols

The key words **MUST**, **MUST NOT**, **REQUIRED**, **SHALL**,
**SHALL NOT**, **SHOULD**, **SHOULD NOT**, **RECOMMENDED**,
**MAY**, and **OPTIONAL** in this document are to be interpreted
as described in [RFC 2119](https://tools.ietf.org/html/rfc2119).

For the purpose of this document, the following terms, keywords,
and symbols are styled in *italic*.

### binary-digit
A character selected from the alphabet:
```
0 1
```
### code
the result of RBDL transpiling process.

### compile time
the phase during which output of *rbdlc* is converted into machine language or equivalent.

### decimal-digit

A character selected from the alphabet:

```
0 1 2 3 4 5 6 7 8 9
```

### hex-digit
A character selected from the alphabet:
```
A B C D E F a b c d e
f 0 1 2 3 4 5 6 7 8 9
```

### ill-formed code

code that does not follow either the syntax constraints or the semantic rules of *target language*

### ill-formed document

a document that does not follow either the syntax constraints or the semantic rules of RBDL


### octal-digit
A character selected from the alphabet:
```
0 1 2 3 4 5 6 7
```

### rbdlc

[Short hand for RBDL compiler] RBDL transpiler implementation that confirms RBDL specifications and supports all **target languages**

### run time
the phase during which a parser generated from RBDL document gets to parse binary files.

### target language

a programming language which RBDL document can be converted into as per this specifications document

### transpile time
the phase during which RBDL document is converted into code written in *target language*

### well-formed code

*code* that follows both the syntax constraints and the semantic rules of *target language*

### well-formed document

a document that follows both the syntax constraints and the semantic rules of RBDL
