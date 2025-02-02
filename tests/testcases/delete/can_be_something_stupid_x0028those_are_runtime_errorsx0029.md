# Tenko parser test case

- Path: tests/testcases/delete/can_be_something_stupid_x0028those_are_runtime_errorsx0029.md

> :: delete
>
> ::> can be something stupid x0028those are runtime errorsx0029

## Input

`````js
delete foo()
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
  loc:{start:{line:1,column:0},end:{line:1,column:12},source:''},
  body: [
    {
      type: 'ExpressionStatement',
      loc:{start:{line:1,column:0},end:{line:1,column:12},source:''},
      expression: {
        type: 'UnaryExpression',
        loc:{start:{line:1,column:0},end:{line:1,column:12},source:''},
        operator: 'delete',
        prefix: true,
        argument: {
          type: 'CallExpression',
          loc:{start:{line:1,column:7},end:{line:1,column:12},source:''},
          callee: {
            type: 'Identifier',
            loc:{start:{line:1,column:7},end:{line:1,column:10},source:''},
            name: 'foo'
          },
          arguments: []
        }
      }
    }
  ]
}

tokens (6x):
       ID_delete IDENT PUNC_PAREN_OPEN PUNC_PAREN_CLOSE ASI
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
(delete ((foo)()));
````

Produces same AST
