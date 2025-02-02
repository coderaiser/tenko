# Tenko parser test case

- Path: tests/testcases/let_declaration/binding_generic/as_a_statement/rest_first.md

> :: let declaration : binding generic : as a statement
>
> ::> rest first
>
> First binding is a rest (not allowed)
>
> 

## FAIL

## Input

`````js
let ...a = 1;
`````

## Output

_Note: the whole output block is auto-generated. Manual changes will be overwritten!_

Below follow outputs in four parsing modes: sloppy mode, strict mode script goal, module goal, web compat mode (always sloppy).

Note that the output parts are auto-generated by the test runner to reflect actual result.

### Sloppy mode

Parsed with script goal and as if the code did not start with strict mode header.

`````
throws: Parser error!
  Unable to ASI, token: {# PUNC_DOT_DOT_DOT : nl=N pos=4:7 loc=4:1 `...`#}

let ...a = 1;
    ^------- error
`````

### Strict mode

Parsed with script goal but as if it was starting with `"use strict"` at the top.

`````
throws: Parser error!
  Let declaration missing binding names and `let` cannot be a regular var or label name in strict mode

let ...a = 1;
    ^------- error
`````


### Module goal

Parsed with the module goal.

_Output same as strict mode._

### Web compat mode

Parsed in sloppy script mode but with the web compat flag enabled.

_Output same as sloppy mode._
