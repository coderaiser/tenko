# Tenko parser test case

- Path: tests/testcases/objects/destructuring/spread_on_string_property_assignment_to_spread.md

> :: objects : destructuring
>
> ::> spread on string property assignment to spread
>
>spread on string proprety assignment to spread
Basically spreading an assignment to a string property, which is "ok"


## Input

`````js
x={..."foo".foo=x}
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
  loc:{start:{line:1,column:0},end:{line:1,column:18},source:''},
  body: [
    {
      type: 'ExpressionStatement',
      loc:{start:{line:1,column:0},end:{line:1,column:18},source:''},
      expression: {
        type: 'AssignmentExpression',
        loc:{start:{line:1,column:0},end:{line:1,column:18},source:''},
        left: {
          type: 'Identifier',
          loc:{start:{line:1,column:0},end:{line:1,column:1},source:''},
          name: 'x'
        },
        operator: '=',
        right: {
          type: 'ObjectExpression',
          loc:{start:{line:1,column:2},end:{line:1,column:18},source:''},
          properties: [
            {
              type: 'SpreadElement',
              loc:{start:{line:1,column:3},end:{line:1,column:17},source:''},
              argument: {
                type: 'AssignmentExpression',
                loc:{start:{line:1,column:6},end:{line:1,column:17},source:''},
                left: {
                  type: 'MemberExpression',
                  loc:{start:{line:1,column:6},end:{line:1,column:15},source:''},
                  object: {
                    type: 'Literal',
                    loc:{start:{line:1,column:6},end:{line:1,column:11},source:''},
                    value: 'foo',
                    raw: '"foo"'
                  },
                  property: {
                    type: 'Identifier',
                    loc:{start:{line:1,column:12},end:{line:1,column:15},source:''},
                    name: 'foo'
                  },
                  computed: false
                },
                operator: '=',
                right: {
                  type: 'Identifier',
                  loc:{start:{line:1,column:16},end:{line:1,column:17},source:''},
                  name: 'x'
                }
              }
            }
          ]
        }
      }
    }
  ]
}

tokens (12x):
       IDENT PUNC_EQ PUNC_CURLY_OPEN PUNC_DOT_DOT_DOT STRING_DOUBLE
       PUNC_DOT IDENT PUNC_EQ IDENT PUNC_CURLY_CLOSE ASI
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
((x = {...("foo".foo = x)}));
````

Produces same AST
