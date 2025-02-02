# Tenko parser test case

- Path: tests/testcases/arrays/destructuring/member_exprs/can_be_a_complex_template.md

> :: arrays : destructuring : member exprs
>
> ::> can be a complex template

## Input

`````js
[`a${5}b`.length] = x
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
  loc:{start:{line:1,column:0},end:{line:1,column:21},source:''},
  body: [
    {
      type: 'ExpressionStatement',
      loc:{start:{line:1,column:0},end:{line:1,column:21},source:''},
      expression: {
        type: 'AssignmentExpression',
        loc:{start:{line:1,column:0},end:{line:1,column:21},source:''},
        left: {
          type: 'ArrayPattern',
          loc:{start:{line:1,column:0},end:{line:1,column:17},source:''},
          elements: [
            {
              type: 'MemberExpression',
              loc:{start:{line:1,column:1},end:{line:1,column:16},source:''},
              object: {
                type: 'TemplateLiteral',
                loc:{start:{line:1,column:1},end:{line:1,column:9},source:''},
                expressions: [
                  {
                    type: 'Literal',
                    loc:{start:{line:1,column:5},end:{line:1,column:6},source:''},
                    value: 5,
                    raw: '5'
                  }
                ],
                quasis: [
                  {
                    type: 'TemplateElement',
                    loc:{start:{line:1,column:2},end:{line:1,column:3},source:''},
                    tail: false,
                    value: { raw: 'a', cooked: 'a' }
                  },
                  {
                    type: 'TemplateElement',
                    loc:{start:{line:1,column:7},end:{line:1,column:8},source:''},
                    tail: true,
                    value: { raw: 'b', cooked: 'b' }
                  }
                ]
              },
              property: {
                type: 'Identifier',
                loc:{start:{line:1,column:10},end:{line:1,column:16},source:''},
                name: 'length'
              },
              computed: false
            }
          ]
        },
        operator: '=',
        right: {
          type: 'Identifier',
          loc:{start:{line:1,column:20},end:{line:1,column:21},source:''},
          name: 'x'
        }
      }
    }
  ]
}

tokens (11x):
       PUNC_BRACKET_OPEN TICK_HEAD NUMBER_DEC TICK_TAIL PUNC_DOT IDENT
       PUNC_BRACKET_CLOSE PUNC_EQ IDENT ASI
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
(([`a${5}b`.length,] = x));
````

Produces same AST
