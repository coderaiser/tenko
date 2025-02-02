# Tenko parser test case

- Path: tests/testcases/comma/in_a_throw.md

> :: comma
>
> ::> in a throw
>
> comma is stronger than ternary

## Input

`````js
throw a,b
`````

## Output

_Note: the whole output block is auto-generated. Manual changes will be overwritten!_

Below follow outputs in four parsing modes: sloppy mode, strict mode script goal, module goal, web compat mode (always sloppy).

Note that the output parts are auto-generated by the test runner to reflect actual result.

### Sloppy mode

Parsed with script goal and as if the code did not start with strict mode header.

`````
ast: {
  type: 'Program',
  loc:{start:{line:1,column:0},end:{line:1,column:9},source:''},
  body: [
    {
      type: 'ThrowStatement',
      loc:{start:{line:1,column:0},end:{line:1,column:9},source:''},
      argument: {
        type: 'SequenceExpression',
        loc:{start:{line:1,column:6},end:{line:1,column:9},source:''},
        expressions: [
          {
            type: 'Identifier',
            loc:{start:{line:1,column:6},end:{line:1,column:7},source:''},
            name: 'a'
          },
          {
            type: 'Identifier',
            loc:{start:{line:1,column:8},end:{line:1,column:9},source:''},
            name: 'b'
          }
        ]
      }
    }
  ]
}

tokens (6x):
       ID_throw IDENT PUNC_COMMA IDENT ASI
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

## AST Printer

Printer output different from input [sloppy]:

````js
throw (a, b);
````

Produces same AST
