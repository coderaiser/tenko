# Tenko parser test case

- Path: tests/testcases/objects/duplicate_keys/objlit_inside_async_call/dupe_shorthand_key.md

> :: objects : duplicate keys : objlit inside async call
>
> ::> dupe shorthand key
>
> Note: duplicate keys are NOT a syntax error for assignment patterns (pfew)

## Input

`````js
async ({x, x})
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
  loc:{start:{line:1,column:0},end:{line:1,column:14},source:''},
  body: [
    {
      type: 'ExpressionStatement',
      loc:{start:{line:1,column:0},end:{line:1,column:14},source:''},
      expression: {
        type: 'CallExpression',
        loc:{start:{line:1,column:0},end:{line:1,column:14},source:''},
        callee: {
          type: 'Identifier',
          loc:{start:{line:1,column:0},end:{line:1,column:5},source:''},
          name: 'async'
        },
        arguments: [
          {
            type: 'ObjectExpression',
            loc:{start:{line:1,column:7},end:{line:1,column:13},source:''},
            properties: [
              {
                type: 'Property',
                loc:{start:{line:1,column:8},end:{line:1,column:9},source:''},
                key: {
                  type: 'Identifier',
                  loc:{start:{line:1,column:8},end:{line:1,column:9},source:''},
                  name: 'x'
                },
                kind: 'init',
                method: false,
                computed: false,
                value: {
                  type: 'Identifier',
                  loc:{start:{line:1,column:8},end:{line:1,column:9},source:''},
                  name: 'x'
                },
                shorthand: true
              },
              {
                type: 'Property',
                loc:{start:{line:1,column:11},end:{line:1,column:12},source:''},
                key: {
                  type: 'Identifier',
                  loc:{start:{line:1,column:11},end:{line:1,column:12},source:''},
                  name: 'x'
                },
                kind: 'init',
                method: false,
                computed: false,
                value: {
                  type: 'Identifier',
                  loc:{start:{line:1,column:11},end:{line:1,column:12},source:''},
                  name: 'x'
                },
                shorthand: true
              }
            ]
          }
        ]
      }
    }
  ]
}

tokens (10x):
       ID_async PUNC_PAREN_OPEN PUNC_CURLY_OPEN IDENT PUNC_COMMA IDENT
       PUNC_CURLY_CLOSE PUNC_PAREN_CLOSE ASI
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
(async({x, x}));
````

Produces same AST
