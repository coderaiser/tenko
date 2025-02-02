# Tenko parser test case

- Path: tests/testcases/export_declaration/lhs_cannot_be_array_literal.md

> :: export declaration
>
> ::> lhs cannot be array literal
>
> It is a Syntax Error if LeftHandSideExpression is either an ObjectLiteral or an ArrayLiteral and LeftHandSideExpression is not covering an AssignmentPattern.

## Input

`````js
export default [x] = y
`````

## Output

_Note: the whole output block is auto-generated. Manual changes will be overwritten!_

Below follow outputs in four parsing modes: sloppy mode, strict mode script goal, module goal, web compat mode (always sloppy).

Note that the output parts are auto-generated by the test runner to reflect actual result.

### Sloppy mode

Parsed with script goal and as if the code did not start with strict mode header.

`````
throws: Parser error!
  The `export` keyword can only be used with the module goal

export default [x] = y
^------- error
`````

### Strict mode

Parsed with script goal but as if it was starting with `"use strict"` at the top.

_Output same as sloppy mode._

### Module goal

Parsed with the module goal.

`````
ast: {
  type: 'Program',
  loc:{start:{line:1,column:0},end:{line:1,column:22},source:''},
  body: [
    {
      type: 'ExportDefaultDeclaration',
      loc:{start:{line:1,column:0},end:{line:1,column:22},source:''},
      declaration: {
        type: 'AssignmentExpression',
        loc:{start:{line:1,column:15},end:{line:1,column:22},source:''},
        left: {
          type: 'ArrayPattern',
          loc:{start:{line:1,column:15},end:{line:1,column:18},source:''},
          elements: [
            {
              type: 'Identifier',
              loc:{start:{line:1,column:16},end:{line:1,column:17},source:''},
              name: 'x'
            }
          ]
        },
        operator: '=',
        right: {
          type: 'Identifier',
          loc:{start:{line:1,column:21},end:{line:1,column:22},source:''},
          name: 'y'
        }
      }
    }
  ]
}

tokens (9x):
       ID_export ID_default PUNC_BRACKET_OPEN IDENT PUNC_BRACKET_CLOSE
       PUNC_EQ IDENT ASI
`````


### Web compat mode

Parsed in sloppy script mode but with the web compat flag enabled.

_Output same as sloppy mode._

## AST Printer

Printer output different from input [module]:

````js
export default ([x,] = y);
````

Produces same AST
