# Tenko parser test case

- Path: tests/testcases/tests_related_to_bindings/varx002flex_dupe_checks/let_inside_var_outside_is_okay.md

> :: tests related to bindings : varx002flex dupe checks
>
> ::> let inside var outside is okay
> 
> In general, you can not declare a lex binding if a var binding exists on the same statement level or below but this check stops at function boundaries. There are no further restriction for var bindings beyond that.

## Input

`````js
{ let x } var x;
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
  loc:{start:{line:1,column:0},end:{line:1,column:16},source:''},
  body: [
    {
      type: 'BlockStatement',
      loc:{start:{line:1,column:0},end:{line:1,column:9},source:''},
      body: [
        {
          type: 'VariableDeclaration',
          loc:{start:{line:1,column:2},end:{line:1,column:7},source:''},
          kind: 'let',
          declarations: [
            {
              type: 'VariableDeclarator',
              loc:{start:{line:1,column:6},end:{line:1,column:7},source:''},
              id: {
                type: 'Identifier',
                loc:{start:{line:1,column:6},end:{line:1,column:7},source:''},
                name: 'x'
              },
              init: null
            }
          ]
        }
      ]
    },
    {
      type: 'VariableDeclaration',
      loc:{start:{line:1,column:10},end:{line:1,column:16},source:''},
      kind: 'var',
      declarations: [
        {
          type: 'VariableDeclarator',
          loc:{start:{line:1,column:14},end:{line:1,column:15},source:''},
          id: {
            type: 'Identifier',
            loc:{start:{line:1,column:14},end:{line:1,column:15},source:''},
            name: 'x'
          },
          init: null
        }
      ]
    }
  ]
}

tokens (9x):
       PUNC_CURLY_OPEN ID_let IDENT ASI PUNC_CURLY_CLOSE ID_var IDENT
       PUNC_SEMI
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
{let x;}
var x;
````

Produces same AST
