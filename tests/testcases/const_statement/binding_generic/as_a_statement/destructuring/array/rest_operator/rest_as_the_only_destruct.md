# Tenko parser test case

- Path: tests/testcases/const_statement/binding_generic/as_a_statement/destructuring/array/rest_operator/rest_as_the_only_destruct.md

> :: const statement : binding generic : as a statement : destructuring : array : rest operator
>
> ::> rest as the only destruct

## Input

`````js
const [...foo] = obj;
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
  loc:{start:{line:1,column:0},end:{line:1,column:21},source:''},
  body: [
    {
      type: 'VariableDeclaration',
      loc:{start:{line:1,column:0},end:{line:1,column:21},source:''},
      kind: 'const',
      declarations: [
        {
          type: 'VariableDeclarator',
          loc:{start:{line:1,column:6},end:{line:1,column:20},source:''},
          id: {
            type: 'ArrayPattern',
            loc:{start:{line:1,column:6},end:{line:1,column:14},source:''},
            elements: [
              {
                type: 'RestElement',
                loc:{start:{line:1,column:7},end:{line:1,column:13},source:''},
                argument: {
                  type: 'Identifier',
                  loc:{start:{line:1,column:10},end:{line:1,column:13},source:''},
                  name: 'foo'
                }
              }
            ]
          },
          init: {
            type: 'Identifier',
            loc:{start:{line:1,column:17},end:{line:1,column:20},source:''},
            name: 'obj'
          }
        }
      ]
    }
  ]
}

tokens (9x):
       ID_const PUNC_BRACKET_OPEN PUNC_DOT_DOT_DOT IDENT
       PUNC_BRACKET_CLOSE PUNC_EQ IDENT PUNC_SEMI
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

Printer output was same as input [sloppy]
