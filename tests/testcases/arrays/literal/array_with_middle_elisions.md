# Tenko parser test case

- Path: tests/testcases/arrays/literal/array_with_middle_elisions.md

> :: arrays : literal
>
> ::> array with middle elisions

## Input

`````js
[x,,y]
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
  loc:{start:{line:1,column:0},end:{line:1,column:6},source:''},
  body: [
    {
      type: 'ExpressionStatement',
      loc:{start:{line:1,column:0},end:{line:1,column:6},source:''},
      expression: {
        type: 'ArrayExpression',
        loc:{start:{line:1,column:0},end:{line:1,column:6},source:''},
        elements: [
          {
            type: 'Identifier',
            loc:{start:{line:1,column:1},end:{line:1,column:2},source:''},
            name: 'x'
          },
          null,
          {
            type: 'Identifier',
            loc:{start:{line:1,column:4},end:{line:1,column:5},source:''},
            name: 'y'
          }
        ]
      }
    }
  ]
}

tokens (8x):
       PUNC_BRACKET_OPEN IDENT PUNC_COMMA PUNC_COMMA IDENT
       PUNC_BRACKET_CLOSE ASI
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
([x, , y,]);
````

Produces same AST
