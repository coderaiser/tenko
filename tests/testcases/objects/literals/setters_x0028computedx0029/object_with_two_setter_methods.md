# Tenko parser test case

- Path: tests/testcases/objects/literals/setters_x0028computedx0029/object_with_two_setter_methods.md

> :: objects : literals : setters x0028computedx0029
>
> ::> object with two setter methods

## Input

`````js
wrap({set [foo](b){}, set [bar](d){}});
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
  loc:{start:{line:1,column:0},end:{line:1,column:39},source:''},
  body: [
    {
      type: 'ExpressionStatement',
      loc:{start:{line:1,column:0},end:{line:1,column:39},source:''},
      expression: {
        type: 'CallExpression',
        loc:{start:{line:1,column:0},end:{line:1,column:38},source:''},
        callee: {
          type: 'Identifier',
          loc:{start:{line:1,column:0},end:{line:1,column:4},source:''},
          name: 'wrap'
        },
        arguments: [
          {
            type: 'ObjectExpression',
            loc:{start:{line:1,column:5},end:{line:1,column:37},source:''},
            properties: [
              {
                type: 'Property',
                loc:{start:{line:1,column:6},end:{line:1,column:20},source:''},
                key: {
                  type: 'Identifier',
                  loc:{start:{line:1,column:11},end:{line:1,column:14},source:''},
                  name: 'foo'
                },
                kind: 'set',
                method: false,
                computed: true,
                value: {
                  type: 'FunctionExpression',
                  loc:{start:{line:1,column:6},end:{line:1,column:20},source:''},
                  generator: false,
                  async: false,
                  id: null,
                  params: [
                    {
                      type: 'Identifier',
                      loc:{start:{line:1,column:16},end:{line:1,column:17},source:''},
                      name: 'b'
                    }
                  ],
                  body: {
                    type: 'BlockStatement',
                    loc:{start:{line:1,column:18},end:{line:1,column:20},source:''},
                    body: []
                  }
                },
                shorthand: false
              },
              {
                type: 'Property',
                loc:{start:{line:1,column:22},end:{line:1,column:36},source:''},
                key: {
                  type: 'Identifier',
                  loc:{start:{line:1,column:27},end:{line:1,column:30},source:''},
                  name: 'bar'
                },
                kind: 'set',
                method: false,
                computed: true,
                value: {
                  type: 'FunctionExpression',
                  loc:{start:{line:1,column:22},end:{line:1,column:36},source:''},
                  generator: false,
                  async: false,
                  id: null,
                  params: [
                    {
                      type: 'Identifier',
                      loc:{start:{line:1,column:32},end:{line:1,column:33},source:''},
                      name: 'd'
                    }
                  ],
                  body: {
                    type: 'BlockStatement',
                    loc:{start:{line:1,column:34},end:{line:1,column:36},source:''},
                    body: []
                  }
                },
                shorthand: false
              }
            ]
          }
        ]
      }
    }
  ]
}

tokens (26x):
       IDENT PUNC_PAREN_OPEN PUNC_CURLY_OPEN ID_set PUNC_BRACKET_OPEN
       IDENT PUNC_BRACKET_CLOSE PUNC_PAREN_OPEN IDENT PUNC_PAREN_CLOSE
       PUNC_CURLY_OPEN PUNC_CURLY_CLOSE PUNC_COMMA ID_set
       PUNC_BRACKET_OPEN IDENT PUNC_BRACKET_CLOSE PUNC_PAREN_OPEN
       IDENT PUNC_PAREN_CLOSE PUNC_CURLY_OPEN PUNC_CURLY_CLOSE
       PUNC_CURLY_CLOSE PUNC_PAREN_CLOSE PUNC_SEMI
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
((wrap)({set [foo](b){}, set [bar](d){}}));
````

Produces same AST
