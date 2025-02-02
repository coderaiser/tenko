# Tenko parser test case

- Path: tests/testcases/for_statement/for-in/obj_destructuring_without_binding.md

> :: for statement : for-in
>
> ::> obj destructuring without binding
>
> {a: b.c} is destructible so should be fine as lhs of any for loop. note: the lhs must be a Pattern with `in` or `of`!

## Input

`````js
for ({a: b.c} in d) e
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
      type: 'ForInStatement',
      loc:{start:{line:1,column:0},end:{line:1,column:21},source:''},
      left: {
        type: 'ObjectPattern',
        loc:{start:{line:1,column:5},end:{line:1,column:13},source:''},
        properties: [
          {
            type: 'Property',
            loc:{start:{line:1,column:6},end:{line:1,column:12},source:''},
            key: {
              type: 'Identifier',
              loc:{start:{line:1,column:6},end:{line:1,column:7},source:''},
              name: 'a'
            },
            kind: 'init',
            method: false,
            computed: false,
            value: {
              type: 'MemberExpression',
              loc:{start:{line:1,column:9},end:{line:1,column:12},source:''},
              object: {
                type: 'Identifier',
                loc:{start:{line:1,column:9},end:{line:1,column:10},source:''},
                name: 'b'
              },
              property: {
                type: 'Identifier',
                loc:{start:{line:1,column:11},end:{line:1,column:12},source:''},
                name: 'c'
              },
              computed: false
            },
            shorthand: false
          }
        ]
      },
      right: {
        type: 'Identifier',
        loc:{start:{line:1,column:17},end:{line:1,column:18},source:''},
        name: 'd'
      },
      body: {
        type: 'ExpressionStatement',
        loc:{start:{line:1,column:20},end:{line:1,column:21},source:''},
        expression: {
          type: 'Identifier',
          loc:{start:{line:1,column:20},end:{line:1,column:21},source:''},
          name: 'e'
        }
      }
    }
  ]
}

tokens (15x):
       ID_for PUNC_PAREN_OPEN PUNC_CURLY_OPEN IDENT PUNC_COLON IDENT
       PUNC_DOT IDENT PUNC_CURLY_CLOSE ID_in IDENT PUNC_PAREN_CLOSE
       IDENT ASI
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
for ({a:(b).c} in d) (e);
````

Produces same AST
