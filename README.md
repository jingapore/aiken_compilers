# Programming Assignments

Numbering starts from 2.

## Assignment 2: Lexer

Overview and clarifications:
- The entry point of `./lexer`, which we build with `make lexer`, is specified in `lexttest.cc`.
    - Within `lextest.cc` we spot an inclusion of `include/PA2/cool-parse.h`. This file is actually an output of Bison, but is provided by the course so that we can get our lexer going.
    - I assume that this dump works, because a parser (in this case Bison) acts on tokens and so its output file will contain tokens that we need to lexer to produce.
- `cool_yylex()` is the function that we call repeated to get the next token. It's printed out with `dump_cool_token(...)`. The printout is diffed against the desired output during grading (e.g. take a look at `grading/arith.cool.out` after unzipping the encoded file embedded in the perl grading script).
