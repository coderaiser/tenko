# Tenko parser test case

- Path: tests/testcases/statements_and_declarations/cannot_nest_a_declaration_inside_a_non-block_statement/const/block.md

> :: statements and declarations : cannot nest a declaration inside a non-block statement : const
>
> ::> block

## Input

`````js
{ const y = x }
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
  loc:{start:{line:1,column:0},end:{line:1,column:15},source:''},
  body: [
    {
      type: 'BlockStatement',
      loc:{start:{line:1,column:0},end:{line:1,column:15},source:''},
      body: [
        {
          type: 'VariableDeclaration',
          loc:{start:{line:1,column:2},end:{line:1,column:13},source:''},
          kind: 'const',
          declarations: [
            {
              type: 'VariableDeclarator',
              loc:{start:{line:1,column:8},end:{line:1,column:13},source:''},
              id: {
                type: 'Identifier',
                loc:{start:{line:1,column:8},end:{line:1,column:9},source:''},
                name: 'y'
              },
              init: {
                type: 'Identifier',
                loc:{start:{line:1,column:12},end:{line:1,column:13},source:''},
                name: 'x'
              }
            }
          ]
        }
      ]
    }
  ]
}

tokens (8x):
       PUNC_CURLY_OPEN ID_const IDENT PUNC_EQ IDENT ASI
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
{const y = x;}
````

Produces same AST
