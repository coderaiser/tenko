# Tenko parser test case

- Path: tests/testcases/var_statement/destructuring_edge_case.md

> :: var statement
>
> ::> destructuring edge case

## Input

`````js
var {[2]: y} = {2:3}
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
  loc:{start:{line:1,column:0},end:{line:1,column:20},source:''},
  body: [
    {
      type: 'VariableDeclaration',
      loc:{start:{line:1,column:0},end:{line:1,column:20},source:''},
      kind: 'var',
      declarations: [
        {
          type: 'VariableDeclarator',
          loc:{start:{line:1,column:4},end:{line:1,column:20},source:''},
          id: {
            type: 'ObjectPattern',
            loc:{start:{line:1,column:4},end:{line:1,column:12},source:''},
            properties: [
              {
                type: 'Property',
                loc:{start:{line:1,column:5},end:{line:1,column:11},source:''},
                key: {
                  type: 'Literal',
                  loc:{start:{line:1,column:6},end:{line:1,column:7},source:''},
                  value: 2,
                  raw: '2'
                },
                kind: 'init',
                method: false,
                computed: true,
                value: {
                  type: 'Identifier',
                  loc:{start:{line:1,column:10},end:{line:1,column:11},source:''},
                  name: 'y'
                },
                shorthand: false
              }
            ]
          },
          init: {
            type: 'ObjectExpression',
            loc:{start:{line:1,column:15},end:{line:1,column:20},source:''},
            properties: [
              {
                type: 'Property',
                loc:{start:{line:1,column:16},end:{line:1,column:19},source:''},
                key: {
                  type: 'Literal',
                  loc:{start:{line:1,column:16},end:{line:1,column:17},source:''},
                  value: 2,
                  raw: '2'
                },
                kind: 'init',
                method: false,
                computed: false,
                value: {
                  type: 'Literal',
                  loc:{start:{line:1,column:18},end:{line:1,column:19},source:''},
                  value: 3,
                  raw: '3'
                },
                shorthand: false
              }
            ]
          }
        }
      ]
    }
  ]
}

tokens (16x):
       ID_var PUNC_CURLY_OPEN PUNC_BRACKET_OPEN NUMBER_DEC
       PUNC_BRACKET_CLOSE PUNC_COLON IDENT PUNC_CURLY_CLOSE PUNC_EQ
       PUNC_CURLY_OPEN NUMBER_DEC PUNC_COLON NUMBER_DEC
       PUNC_CURLY_CLOSE ASI
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
var {[2]:y} = {2:3};
````

Produces same AST
