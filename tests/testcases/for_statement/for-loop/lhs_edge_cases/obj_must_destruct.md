# Tenko parser test case

- Path: tests/testcases/for_statement/for-loop/lhs_edge_cases/obj_must_destruct.md

> :: for statement : for-loop : lhs edge cases
>
> ::> obj must destruct
>
> This is an object that must destruct due to the init.

## PASS

## Input

`````js
for ({x=y}=x ;;) ;
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
  loc:{start:{line:1,column:0},end:{line:1,column:18},source:''},
  body: [
    {
      type: 'ForStatement',
      loc:{start:{line:1,column:0},end:{line:1,column:18},source:''},
      init: {
        type: 'AssignmentExpression',
        loc:{start:{line:1,column:5},end:{line:1,column:12},source:''},
        left: {
          type: 'ObjectPattern',
          loc:{start:{line:1,column:5},end:{line:1,column:10},source:''},
          properties: [
            {
              type: 'Property',
              loc:{start:{line:1,column:6},end:{line:1,column:9},source:''},
              key: {
                type: 'Identifier',
                loc:{start:{line:1,column:6},end:{line:1,column:7},source:''},
                name: 'x'
              },
              kind: 'init',
              method: false,
              computed: false,
              value: {
                type: 'AssignmentPattern',
                loc:{start:{line:1,column:6},end:{line:1,column:9},source:''},
                left: {
                  type: 'Identifier',
                  loc:{start:{line:1,column:6},end:{line:1,column:7},source:''},
                  name: 'x'
                },
                right: {
                  type: 'Identifier',
                  loc:{start:{line:1,column:8},end:{line:1,column:9},source:''},
                  name: 'y'
                }
              },
              shorthand: true
            }
          ]
        },
        operator: '=',
        right: {
          type: 'Identifier',
          loc:{start:{line:1,column:11},end:{line:1,column:12},source:''},
          name: 'x'
        }
      },
      test: null,
      update: null,
      body: {
        type: 'EmptyStatement',
        loc:{start:{line:1,column:17},end:{line:1,column:18},source:''}
      }
    }
  ]
}

tokens (14x):
       ID_for PUNC_PAREN_OPEN PUNC_CURLY_OPEN IDENT PUNC_EQ IDENT
       PUNC_CURLY_CLOSE PUNC_EQ IDENT PUNC_SEMI PUNC_SEMI
       PUNC_PAREN_CLOSE PUNC_SEMI
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
for ((({x = y} = x));;) ;
````

Produces same AST
