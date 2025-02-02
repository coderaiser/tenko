# Tenko parser test case

- Path: tests/testcases/if_statement/if_return_regex_else.md

> :: if statement
>
> ::> if return regex else
>
> Regression was incorrectly parsing ASI where it shouldn't
>
> This was causing the semi to be parsed as an empty statement, which in turn prevented the `else` to be matched with the `if`

## Input

`````js
function x(){
  if (x) return / /;
  else;
}
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
  loc:{start:{line:1,column:0},end:{line:4,column:1},source:''},
  body: [
    {
      type: 'FunctionDeclaration',
      loc:{start:{line:1,column:0},end:{line:4,column:1},source:''},
      generator: false,
      async: false,
      id: {
        type: 'Identifier',
        loc:{start:{line:1,column:9},end:{line:1,column:10},source:''},
        name: 'x'
      },
      params: [],
      body: {
        type: 'BlockStatement',
        loc:{start:{line:1,column:12},end:{line:4,column:1},source:''},
        body: [
          {
            type: 'IfStatement',
            loc:{start:{line:2,column:2},end:{line:3,column:7},source:''},
            test: {
              type: 'Identifier',
              loc:{start:{line:2,column:6},end:{line:2,column:7},source:''},
              name: 'x'
            },
            consequent: {
              type: 'ReturnStatement',
              loc:{start:{line:2,column:9},end:{line:2,column:20},source:''},
              argument: {
                type: 'Literal',
                loc:{start:{line:2,column:16},end:{line:2,column:19},source:''},
                value: null,
                regex: { pattern: ' ', flags: '' },
                raw: '/ /'
              }
            },
            alternate: {
              type: 'EmptyStatement',
              loc:{start:{line:3,column:6},end:{line:3,column:7},source:''}
            }
          }
        ]
      }
    }
  ]
}

tokens (16x):
       ID_function IDENT PUNC_PAREN_OPEN PUNC_PAREN_CLOSE
       PUNC_CURLY_OPEN ID_if PUNC_PAREN_OPEN IDENT PUNC_PAREN_CLOSE
       ID_return REGEXN PUNC_SEMI ID_else PUNC_SEMI PUNC_CURLY_CLOSE
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
function x() {if (x) return / /; else ;}
````

Produces same AST
