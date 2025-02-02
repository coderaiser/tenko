# Tenko parser test case

- Path: tests/testcases/async_keyword/export_can_not_just_export_x0060asyncx0060_so_asi_not_allowed_for_arrow.md

> :: async keyword
>
> ::> export can not just export x0060asyncx0060 so asi not allowed for arrow

## Input

`````js
export async 
 a => b
`````

## Output

_Note: the whole output block is auto-generated. Manual changes will be overwritten!_

Below follow outputs in four parsing modes: sloppy mode, strict mode script goal, module goal, web compat mode (always sloppy).

Note that the output parts are auto-generated by the test runner to reflect actual result.

### Sloppy mode

Parsed with script goal and as if the code did not start with strict mode header.

`````
throws: Parser error!
  The `export` keyword can only be used with the module goal

export async
^------- error

 a => b
`````

### Strict mode

Parsed with script goal but as if it was starting with `"use strict"` at the top.

_Output same as sloppy mode._

### Module goal

Parsed with the module goal.

`````
throws: Parser error!
  Can only export async functions (not arrows), did not find a function

export async
 a => b
 ^------- error
`````


### Web compat mode

Parsed in sloppy script mode but with the web compat flag enabled.

_Output same as sloppy mode._
