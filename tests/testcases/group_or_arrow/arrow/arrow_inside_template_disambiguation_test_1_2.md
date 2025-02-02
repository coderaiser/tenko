# Tenko parser test case

- Path: tests/testcases/group_or_arrow/arrow/arrow_inside_template_disambiguation_test_1_2.md

> :: group or arrow : arrow
>
> ::> arrow inside template disambiguation test 1 2

## Input

`````js
`X${a => b + c}Y`
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
  loc:{start:{line:1,column:0},end:{line:1,column:17},source:''},
  body: [
    {
      type: 'ExpressionStatement',
      loc:{start:{line:1,column:0},end:{line:1,column:17},source:''},
      expression: {
        type: 'TemplateLiteral',
        loc:{start:{line:1,column:0},end:{line:1,column:17},source:''},
        expressions: [
          {
            type: 'ArrowFunctionExpression',
            loc:{start:{line:1,column:4},end:{line:1,column:14},source:''},
            params: [
              {
                type: 'Identifier',
                loc:{start:{line:1,column:4},end:{line:1,column:5},source:''},
                name: 'a'
              }
            ],
            id: null,
            generator: false,
            async: false,
            expression: true,
            body: {
              type: 'BinaryExpression',
              loc:{start:{line:1,column:9},end:{line:1,column:14},source:''},
              left: {
                type: 'Identifier',
                loc:{start:{line:1,column:9},end:{line:1,column:10},source:''},
                name: 'b'
              },
              operator: '+',
              right: {
                type: 'Identifier',
                loc:{start:{line:1,column:13},end:{line:1,column:14},source:''},
                name: 'c'
              }
            }
          }
        ],
        quasis: [
          {
            type: 'TemplateElement',
            loc:{start:{line:1,column:1},end:{line:1,column:2},source:''},
            tail: false,
            value: { raw: 'X', cooked: 'X' }
          },
          {
            type: 'TemplateElement',
            loc:{start:{line:1,column:15},end:{line:1,column:16},source:''},
            tail: true,
            value: { raw: 'Y', cooked: 'Y' }
          }
        ]
      }
    }
  ]
}

tokens (9x):
       TICK_HEAD IDENT PUNC_EQ_GT IDENT PUNC_PLUS IDENT TICK_TAIL ASI
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
`X${a => (((b) + (c)))}Y`;
````

Produces same AST
