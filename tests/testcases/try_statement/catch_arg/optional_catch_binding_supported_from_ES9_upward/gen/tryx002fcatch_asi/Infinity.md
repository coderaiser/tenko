# Tenko parser autogenerated test case

- From: tests/testcases/try_statement/catch_arg/optional_catch_binding_supported_from_ES9_upward/autogen.md
- Path: tests/testcases/try_statement/catch_arg/optional_catch_binding_supported_from_ES9_upward/gen/tryx002fcatch_asi/Infinity.md

> :: try statement : catch arg : optional catch binding supported from ES9 upward : gen : tryx002fcatch asi
>
> ::> Infinity

## Input

- `es = Infinity`

`````js
try {} catch \n {}
`````

## Output

_Note: the whole output block is auto-generated. Manual changes will be overwritten!_

Below follow outputs in four parsing modes: sloppy mode, strict mode script goal, module goal, web compat mode (always sloppy).

Note that the output parts are auto-generated by the test runner to reflect actual result.

### Sloppy mode

Parsed with script goal and as if the code did not start with strict mode header.

`````
throws: Lexer error!
    Only unicode escapes are supported in identifier escapes

try {} catch \n {}
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
