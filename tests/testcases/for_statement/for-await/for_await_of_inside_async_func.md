# Tenko parser test case

- Path: tests/testcases/for_statement/for-await/for_await_of_inside_async_func.md

> :: for statement : for-await
>
> ::> for await of inside async func

## Input

`````js
async function f(){ for await (x of y) {} }
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
  loc:{start:{line:1,column:0},end:{line:1,column:43},source:''},
  body: [
    {
      type: 'FunctionDeclaration',
      loc:{start:{line:1,column:0},end:{line:1,column:43},source:''},
      generator: false,
      async: true,
      id: {
        type: 'Identifier',
        loc:{start:{line:1,column:15},end:{line:1,column:16},source:''},
        name: 'f'
      },
      params: [],
      body: {
        type: 'BlockStatement',
        loc:{start:{line:1,column:18},end:{line:1,column:43},source:''},
        body: [
          {
            type: 'ForOfStatement',
            loc:{start:{line:1,column:20},end:{line:1,column:41},source:''},
            left: {
              type: 'Identifier',
              loc:{start:{line:1,column:31},end:{line:1,column:32},source:''},
              name: 'x'
            },
            right: {
              type: 'Identifier',
              loc:{start:{line:1,column:36},end:{line:1,column:37},source:''},
              name: 'y'
            },
            await: true,
            body: {
              type: 'BlockStatement',
              loc:{start:{line:1,column:39},end:{line:1,column:41},source:''},
              body: []
            }
          }
        ]
      }
    }
  ]
}

tokens (17x):
       ID_async ID_function IDENT PUNC_PAREN_OPEN PUNC_PAREN_CLOSE
       PUNC_CURLY_OPEN ID_for ID_await PUNC_PAREN_OPEN IDENT ID_of
       IDENT PUNC_PAREN_CLOSE PUNC_CURLY_OPEN PUNC_CURLY_CLOSE
       PUNC_CURLY_CLOSE
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
async function f() {for await ((x) of y) {}}
````

Produces same AST
