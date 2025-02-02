# Tenko parser test case

- Path: tests/testcases/regexes/named_capturing_groups/non_bmp_unicode_double_escaped/idrest_es6_unicode.md

> :: regexes : named capturing groups : non bmp unicode double escaped
>
> ::> idrest es6 unicode
>
> `\u{1D7D0}` is a valid id_continue but the escape variant is only valid with u-flag

## FAIL

## Input

`````js
/(?<abc\u{1D7D0}def>foo\k<abc\u{1D7D0}def>)/
`````

## Output

_Note: the whole output block is auto-generated. Manual changes will be overwritten!_

Below follow outputs in four parsing modes: sloppy mode, strict mode script goal, module goal, web compat mode (always sloppy).

Note that the output parts are auto-generated by the test runner to reflect actual result.

### Sloppy mode

Parsed with script goal and as if the code did not start with strict mode header.

`````
throws: Lexer error!
    Regex: The es6 long unicode escape is only valid with u-flag; Found "es6" unicode escape (`\u{..}`) or surrogate pair quads (`\uxxxx\uxxxx`) in regex ident, which is only valid with u-flag in regex; Regex body had an escape that is only valid with an u-flag, but it had no u-flag

/(?<abc\u{1D7D0}def>foo\k<abc\u{1D7D0}def>)/
^------- error
`````

### Strict mode

Parsed with script goal but as if it was starting with `"use strict"` at the top.

_Output same as sloppy mode._

### Module goal

Parsed with the module goal.

_Output same as sloppy mode._

### Web compat mode

Parsed in sloppy script mode but with the web compat flag enabled.

_Output same as sloppy mode._
