# Tenko parser test case

- Path: tests/testcases/functions/dupe_params_with_arr_pattern.md

> :: functions
>
> ::> dupe params with arr pattern
>
> By fuzzer, v8 only
>
> Error: Duplicate parameter name not allowed in this context
>
> The pattern makes the params "complex", so the duplicate binding triggers the syntax error.
>
> There was a regression where this would still throw in sloppy mode because the future keyword detection would mark the param as "complex" in order for it to throw if the body turned out to be strict mode. Basically solved it by adding another state to indicate non-strict-but-simple.
>
> Another regression was that patterns and rest were not detected as complex.

## Input

`````js
function x([public], public){}
`````

## Output

_Note: the whole output block is auto-generated. Manual changes will be overwritten!_

Below follow outputs in four parsing modes: sloppy mode, strict mode script goal, module goal, web compat mode (always sloppy).

Note that the output parts are auto-generated by the test runner to reflect actual result.

### Sloppy mode

Parsed with script goal and as if the code did not start with strict mode header.

`````
throws: Parser error!
  Function had duplicate params

function x([public], public){}
                             ^------- error
`````

### Strict mode

Parsed with script goal but as if it was starting with `"use strict"` at the top.

`````
throws: Parser error!
  Cannot use this name (public) as a variable name because: Cannot use this reserved word as a variable name in strict mode

function x([public], public){}
                  ^------- error
`````


### Module goal

Parsed with the module goal.

_Output same as strict mode._

### Web compat mode

Parsed in sloppy script mode but with the web compat flag enabled.

_Output same as sloppy mode._
