# Environment

The text that describes binary file format is called *RBDL document*.

## Document Structure

The text of RBDL document **MUST** be kept in a single file prior to transpiling. The result of transpiling is **REQUIRED** to be *well-formed code*. Transpiled *code* **MAY** depend on arbitrary 3rd party run time library. However, it **MUST** be possible to convert the transpiled *code* (together with any needed 3rd party runtime) into a stand-alone library.


## Diagnostics

*rbdlc* **MUST** produce at least one error message it is processing *ill-formed document* or generating *ill-formed code*.

## Character Set

RBDL documents **MUST** be written using UTF-8 as per [ISO/IEC 10646](http://unicode.org/L2/L2010/10038-fcd10646-main.pdf). However, generated parsers **MUST** be at least capable of parsing arbitrary character set as a binary sequence.