# Tenko parser test case

- Path: tests/testcases/exponentiation_op/expr/new_with_parens_is_allowed_as_lhs.md

> :: exponentiation op : expr
>
> ::> new with parens is allowed as lhs
>
> the lhs of `**` must be an assignment or exponentiation operator... there is no goal that allows this unary expression

## Input

`````js
(new x() ** 2)
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
        type: 'BinaryExpression',
        loc:{start:{line:1,column:1},end:{line:1,column:13},source:''},
        left: {
          type: 'NewExpression',
          loc:{start:{line:1,column:1},end:{line:1,column:8},source:''},
          arguments: [],
          callee: {
            type: 'Identifier',
            loc:{start:{line:1,column:5},end:{line:1,column:6},source:''},
            name: 'x'
          }
        },
        operator: '**',
        right: {
          type: 'Literal',
          loc:{start:{line:1,column:12},end:{line:1,column:13},source:''},
          value: 2,
          raw: '2'
        }
      }
    }
  ]
}

tokens (10x):
       PUNC_PAREN_OPEN ID_new IDENT PUNC_PAREN_OPEN PUNC_PAREN_CLOSE
       PUNC_STAR_STAR NUMBER_DEC PUNC_PAREN_CLOSE ASI
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
(((new (x)()) ** (2)));
````

Produces same AST
