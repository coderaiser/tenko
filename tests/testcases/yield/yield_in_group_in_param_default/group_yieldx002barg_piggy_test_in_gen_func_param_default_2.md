# Tenko parser test case

- Path: tests/testcases/yield/yield_in_group_in_param_default/group_yieldx002barg_piggy_test_in_gen_func_param_default_2.md

> :: yield : yield in group in param default
>
> ::> group yieldx002barg piggy test in gen func param default 2
>
> https://tc39.github.io/ecma262/#sec-arrow-function-definitions-static-semantics-early-errors
>
> > It is a Syntax Error if ArrowParameters Contains YieldExpression is true.
>
> The arrow parens inherit the generator state from the parent scope (unlike regular funcs, who reset it)


## Input


`````js
function *f(){    function *g(x=(yield z)=y){}   }
`````

## Output

_Note: the whole output block is auto-generated. Manual changes will be overwritten!_

Below follow outputs in four parsing modes: sloppy mode, strict mode script goal, module goal, web compat mode (always sloppy).

Note that the output parts are auto-generated by the test runner to reflect actual result.

### Sloppy mode

Parsed with script goal and as if the code did not start with strict mode header.

`````
throws: Parser error!
  The `yield` keyword in arg default must be a var name but that is not allowed inside a generator

function *f(){    function *g(x=(yield z)=y){}   }
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
