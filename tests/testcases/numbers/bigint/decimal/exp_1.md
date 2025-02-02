# Tenko parser test case

- Path: tests/testcases/numbers/bigint/decimal/exp_1.md

> :: numbers : bigint : decimal
>
> ::> exp 1
>
> BigInt suffix only supported on decimals and exponent is not supported

## FAIL

## Input

`````js
313e1n
`````

## Output

_Note: the whole output block is auto-generated. Manual changes will be overwritten!_

Below follow outputs in four parsing modes: sloppy mode, strict mode script goal, module goal, web compat mode (always sloppy).

Note that the output parts are auto-generated by the test runner to reflect actual result.

### Sloppy mode

Parsed with script goal and as if the code did not start with strict mode header.

`````
throws: Lexer error!
    Found `n`. It is not legal for an ident or number token to start after a number token without some form of separation

313e1n
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
