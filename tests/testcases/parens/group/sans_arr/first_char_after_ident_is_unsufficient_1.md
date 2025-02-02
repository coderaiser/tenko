# Tenko parser test case

- Path: tests/testcases/parens/group/sans_arr/first_char_after_ident_is_unsufficient_1.md

> :: parens : group : sans arr
>
> ::> first char after ident is unsufficient 1

## Input

`````js
(foo /=g/m.x);
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
        type: 'AssignmentExpression',
        loc:{start:{line:1,column:1},end:{line:1,column:12},source:''},
        left: {
          type: 'Identifier',
          loc:{start:{line:1,column:1},end:{line:1,column:4},source:''},
          name: 'foo'
        },
        operator: '/=',
        right: {
          type: 'BinaryExpression',
          loc:{start:{line:1,column:7},end:{line:1,column:12},source:''},
          left: {
            type: 'Identifier',
            loc:{start:{line:1,column:7},end:{line:1,column:8},source:''},
            name: 'g'
          },
          operator: '/',
          right: {
            type: 'MemberExpression',
            loc:{start:{line:1,column:9},end:{line:1,column:12},source:''},
            object: {
              type: 'Identifier',
              loc:{start:{line:1,column:9},end:{line:1,column:10},source:''},
              name: 'm'
            },
            property: {
              type: 'Identifier',
              loc:{start:{line:1,column:11},end:{line:1,column:12},source:''},
              name: 'x'
            },
            computed: false
          }
        }
      }
    }
  ]
}

tokens (11x):
       PUNC_PAREN_OPEN IDENT PUNC_DIV_EQ IDENT PUNC_DIV IDENT PUNC_DOT
       IDENT PUNC_PAREN_CLOSE PUNC_SEMI
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
((foo /= ((g) / ((m).x))));
````

Produces same AST
