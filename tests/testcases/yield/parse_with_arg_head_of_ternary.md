# Tenko parser test case

- Path: tests/testcases/yield/parse_with_arg_head_of_ternary.md

> :: yield
>
> ::> parse with arg head of ternary

## Input

`````js
function *f() { 1 ? yield 2 : 3; }
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
  loc:{start:{line:1,column:0},end:{line:1,column:34},source:''},
  body: [
    {
      type: 'FunctionDeclaration',
      loc:{start:{line:1,column:0},end:{line:1,column:34},source:''},
      generator: true,
      async: false,
      id: {
        type: 'Identifier',
        loc:{start:{line:1,column:10},end:{line:1,column:11},source:''},
        name: 'f'
      },
      params: [],
      body: {
        type: 'BlockStatement',
        loc:{start:{line:1,column:14},end:{line:1,column:34},source:''},
        body: [
          {
            type: 'ExpressionStatement',
            loc:{start:{line:1,column:16},end:{line:1,column:32},source:''},
            expression: {
              type: 'ConditionalExpression',
              loc:{start:{line:1,column:16},end:{line:1,column:31},source:''},
              test: {
                type: 'Literal',
                loc:{start:{line:1,column:16},end:{line:1,column:17},source:''},
                value: 1,
                raw: '1'
              },
              consequent: {
                type: 'YieldExpression',
                loc:{start:{line:1,column:20},end:{line:1,column:27},source:''},
                delegate: false,
                argument: {
                  type: 'Literal',
                  loc:{start:{line:1,column:26},end:{line:1,column:27},source:''},
                  value: 2,
                  raw: '2'
                }
              },
              alternate: {
                type: 'Literal',
                loc:{start:{line:1,column:30},end:{line:1,column:31},source:''},
                value: 3,
                raw: '3'
              }
            }
          }
        ]
      }
    }
  ]
}

tokens (15x):
       ID_function PUNC_STAR IDENT PUNC_PAREN_OPEN PUNC_PAREN_CLOSE
       PUNC_CURLY_OPEN NUMBER_DEC PUNC_QMARK ID_yield NUMBER_DEC
       PUNC_COLON NUMBER_DEC PUNC_SEMI PUNC_CURLY_CLOSE
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
function* f() {((1)? ((yield (2))) : (3));}
````

Produces same AST
