# Tenko parser test case

- Path: tests/testcases/objects/invalid_destructuring_assignments_x0028x002316x0029/obj_pattern_with_value_of_a_computed_property_being_an_arrow.md

> :: objects : invalid destructuring assignments x0028x002316x0029
>
> ::> obj pattern with value of a computed property being an arrow

## Input


`````js
({[a]: b => []} = [2])
`````

## Output

_Note: the whole output block is auto-generated. Manual changes will be overwritten!_

Below follow outputs in four parsing modes: sloppy mode, strict mode script goal, module goal, web compat mode (always sloppy).

Note that the output parts are auto-generated by the test runner to reflect actual result.

### Sloppy mode

Parsed with script goal and as if the code did not start with strict mode header.

`````
throws: Parser error!
  Tried to destructure something that is not destructible

({[a]: b => []} = [2])
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
