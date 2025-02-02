# Tenko parser test case

- Path: tests/testcases/for_statement/for-loop/destructuring_non-binding_cases/object_that_would_not_be_destructible.md

> :: for statement : for-loop : destructuring non-binding cases
>
> ::> object that would not be destructible

## Input

`````js
for ({a: x + y};;);
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
  loc:{start:{line:1,column:0},end:{line:1,column:19},source:''},
  body: [
    {
      type: 'ForStatement',
      loc:{start:{line:1,column:0},end:{line:1,column:19},source:''},
      init: {
        type: 'ObjectExpression',
        loc:{start:{line:1,column:5},end:{line:1,column:15},source:''},
        properties: [
          {
            type: 'Property',
            loc:{start:{line:1,column:6},end:{line:1,column:14},source:''},
            key: {
              type: 'Identifier',
              loc:{start:{line:1,column:6},end:{line:1,column:7},source:''},
              name: 'a'
            },
            kind: 'init',
            method: false,
            computed: false,
            value: {
              type: 'BinaryExpression',
              loc:{start:{line:1,column:9},end:{line:1,column:14},source:''},
              left: {
                type: 'Identifier',
                loc:{start:{line:1,column:9},end:{line:1,column:10},source:''},
                name: 'x'
              },
              operator: '+',
              right: {
                type: 'Identifier',
                loc:{start:{line:1,column:13},end:{line:1,column:14},source:''},
                name: 'y'
              }
            },
            shorthand: false
          }
        ]
      },
      test: null,
      update: null,
      body: {
        type: 'EmptyStatement',
        loc:{start:{line:1,column:18},end:{line:1,column:19},source:''}
      }
    }
  ]
}

tokens (14x):
       ID_for PUNC_PAREN_OPEN PUNC_CURLY_OPEN IDENT PUNC_COLON IDENT
       PUNC_PLUS IDENT PUNC_CURLY_CLOSE PUNC_SEMI PUNC_SEMI
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
for (({a:((x) + (y))});;) ;
````

Produces same AST
