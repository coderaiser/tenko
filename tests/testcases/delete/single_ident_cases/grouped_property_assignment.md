# Tenko parser test case

- Path: tests/testcases/delete/single_ident_cases/grouped_property_assignment.md

> :: delete : single ident cases
>
> ::> grouped property assignment

## Input

`````js
delete ("foo".bar = 20)
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
  loc:{start:{line:1,column:0},end:{line:1,column:23},source:''},
  body: [
    {
      type: 'ExpressionStatement',
      loc:{start:{line:1,column:0},end:{line:1,column:23},source:''},
      expression: {
        type: 'UnaryExpression',
        loc:{start:{line:1,column:0},end:{line:1,column:23},source:''},
        operator: 'delete',
        prefix: true,
        argument: {
          type: 'AssignmentExpression',
          loc:{start:{line:1,column:8},end:{line:1,column:22},source:''},
          left: {
            type: 'MemberExpression',
            loc:{start:{line:1,column:8},end:{line:1,column:17},source:''},
            object: {
              type: 'Literal',
              loc:{start:{line:1,column:8},end:{line:1,column:13},source:''},
              value: 'foo',
              raw: '"foo"'
            },
            property: {
              type: 'Identifier',
              loc:{start:{line:1,column:14},end:{line:1,column:17},source:''},
              name: 'bar'
            },
            computed: false
          },
          operator: '=',
          right: {
            type: 'Literal',
            loc:{start:{line:1,column:20},end:{line:1,column:22},source:''},
            value: 20,
            raw: '20'
          }
        }
      }
    }
  ]
}

tokens (10x):
       ID_delete PUNC_PAREN_OPEN STRING_DOUBLE PUNC_DOT IDENT PUNC_EQ
       NUMBER_DEC PUNC_PAREN_CLOSE ASI
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
(delete (("foo".bar = 20)));
````

Produces same AST
