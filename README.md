# PL/O'

This is a PL/O' compiler written in Rust.

## BNF

```
<program> ::=
    <block> "."

<block> ::=
    { <const_declaration> | <var_declaration> | <function_declaration> } <statement>

<const_declaration> ::=
    "const" <ident> "=" <number> { "," <ident> "=" <number> } ";"

<var_declaration> ::=
    "var" <ident> { "," ident } ";"

<function_declaration> ::=
    "function" <ident> "(" [ <ident> { "," <ident> } ] ")" <block> ";"

<statement> ::=
    [
        <ident> ":=" <expression> |
        "begin" <statement> { ";" <statement> } "end" |
        "if" <statement> "then" <statement> |
        "while" <condition> "do" <statement> |
        "return" <expression> |
        "write" <expression> |
        "writeln"
    ]

<condition> ::=
    "odd" <expression> |
    <expression> ( "=" | "<>" | "<" | "<=" | ">" | ">=" ) <expression>

<expression> ::=
    [ "+" | "-" ] <term> { ( "+" | "-" ) <term> }

<term> ::=
    <factor> { ( "*" | "/" ) <factor> }

<factor> ::=
    <ident> |
    <number> |
    <ident> "(" [ <expression> { "," <expression> } ] ")" |
    "(" <expression> ")"
```

## References

* [コンパイラ - 作りながら学ぶ](https://www.ohmsha.co.jp/book/9784274221163/)
