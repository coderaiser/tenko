# Tenko parser test case

- Path: tests/testcases/async_keyword/introduced_in_es8/let_async_asi_function.md

> :: async keyword : introduced in es8
>
> ::> let async asi function

## Input

- `es = 7`

`````js
let async 
 function f(){}
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
  loc:{start:{line:1,column:0},end:{line:2,column:15},source:''},
  body: [
    {
      type: 'VariableDeclaration',
      loc:{start:{line:1,column:0},end:{line:1,column:9},source:''},
      kind: 'let',
      declarations: [
        {
          type: 'VariableDeclarator',
          loc:{start:{line:1,column:4},end:{line:1,column:9},source:''},
          id: {
            type: 'Identifier',
            loc:{start:{line:1,column:4},end:{line:1,column:9},source:''},
            name: 'async'
          },
          init: null
        }
      ]
    },
    {
      type: 'FunctionDeclaration',
      loc:{start:{line:2,column:1},end:{line:2,column:15},source:''},
      generator: false,
      async: false,
      id: {
        type: 'Identifier',
        loc:{start:{line:2,column:10},end:{line:2,column:11},source:''},
        name: 'f'
      },
      params: [],
      body: {
        type: 'BlockStatement',
        loc:{start:{line:2,column:13},end:{line:2,column:15},source:''},
        body: []
      }
    }
  ]
}

tokens (10x):
       ID_let ID_async ASI ID_function IDENT PUNC_PAREN_OPEN
       PUNC_PAREN_CLOSE PUNC_CURLY_OPEN PUNC_CURLY_CLOSE
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
let async;
function f() {}
````

Produces same AST
