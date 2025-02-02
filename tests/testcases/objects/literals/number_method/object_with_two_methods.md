# Tenko parser test case

- Path: tests/testcases/objects/literals/number_method/object_with_two_methods.md

> :: objects : literals : number method
>
> ::> object with two methods

## Input

`````js
wrap({.9(){}, 0x84(){}, 0b1(){}, 0o27(){}, 1e234(){}});
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
  loc:{start:{line:1,column:0},end:{line:1,column:55},source:''},
  body: [
    {
      type: 'ExpressionStatement',
      loc:{start:{line:1,column:0},end:{line:1,column:55},source:''},
      expression: {
        type: 'CallExpression',
        loc:{start:{line:1,column:0},end:{line:1,column:54},source:''},
        callee: {
          type: 'Identifier',
          loc:{start:{line:1,column:0},end:{line:1,column:4},source:''},
          name: 'wrap'
        },
        arguments: [
          {
            type: 'ObjectExpression',
            loc:{start:{line:1,column:5},end:{line:1,column:53},source:''},
            properties: [
              {
                type: 'Property',
                loc:{start:{line:1,column:6},end:{line:1,column:12},source:''},
                key: {
                  type: 'Literal',
                  loc:{start:{line:1,column:6},end:{line:1,column:8},source:''},
                  value: 0.9,
                  raw: '.9'
                },
                kind: 'init',
                method: true,
                computed: false,
                value: {
                  type: 'FunctionExpression',
                  loc:{start:{line:1,column:6},end:{line:1,column:12},source:''},
                  generator: false,
                  async: false,
                  id: null,
                  params: [],
                  body: {
                    type: 'BlockStatement',
                    loc:{start:{line:1,column:10},end:{line:1,column:12},source:''},
                    body: []
                  }
                },
                shorthand: false
              },
              {
                type: 'Property',
                loc:{start:{line:1,column:14},end:{line:1,column:22},source:''},
                key: {
                  type: 'Literal',
                  loc:{start:{line:1,column:14},end:{line:1,column:18},source:''},
                  value: 132,
                  raw: '0x84'
                },
                kind: 'init',
                method: true,
                computed: false,
                value: {
                  type: 'FunctionExpression',
                  loc:{start:{line:1,column:14},end:{line:1,column:22},source:''},
                  generator: false,
                  async: false,
                  id: null,
                  params: [],
                  body: {
                    type: 'BlockStatement',
                    loc:{start:{line:1,column:20},end:{line:1,column:22},source:''},
                    body: []
                  }
                },
                shorthand: false
              },
              {
                type: 'Property',
                loc:{start:{line:1,column:24},end:{line:1,column:31},source:''},
                key: {
                  type: 'Literal',
                  loc:{start:{line:1,column:24},end:{line:1,column:27},source:''},
                  value: 1,
                  raw: '0b1'
                },
                kind: 'init',
                method: true,
                computed: false,
                value: {
                  type: 'FunctionExpression',
                  loc:{start:{line:1,column:24},end:{line:1,column:31},source:''},
                  generator: false,
                  async: false,
                  id: null,
                  params: [],
                  body: {
                    type: 'BlockStatement',
                    loc:{start:{line:1,column:29},end:{line:1,column:31},source:''},
                    body: []
                  }
                },
                shorthand: false
              },
              {
                type: 'Property',
                loc:{start:{line:1,column:33},end:{line:1,column:41},source:''},
                key: {
                  type: 'Literal',
                  loc:{start:{line:1,column:33},end:{line:1,column:37},source:''},
                  value: 23,
                  raw: '0o27'
                },
                kind: 'init',
                method: true,
                computed: false,
                value: {
                  type: 'FunctionExpression',
                  loc:{start:{line:1,column:33},end:{line:1,column:41},source:''},
                  generator: false,
                  async: false,
                  id: null,
                  params: [],
                  body: {
                    type: 'BlockStatement',
                    loc:{start:{line:1,column:39},end:{line:1,column:41},source:''},
                    body: []
                  }
                },
                shorthand: false
              },
              {
                type: 'Property',
                loc:{start:{line:1,column:43},end:{line:1,column:52},source:''},
                key: {
                  type: 'Literal',
                  loc:{start:{line:1,column:43},end:{line:1,column:48},source:''},
                  value: 1e+234,
                  raw: '1e234'
                },
                kind: 'init',
                method: true,
                computed: false,
                value: {
                  type: 'FunctionExpression',
                  loc:{start:{line:1,column:43},end:{line:1,column:52},source:''},
                  generator: false,
                  async: false,
                  id: null,
                  params: [],
                  body: {
                    type: 'BlockStatement',
                    loc:{start:{line:1,column:50},end:{line:1,column:52},source:''},
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

tokens (36x):
       IDENT PUNC_PAREN_OPEN PUNC_CURLY_OPEN NUMBER_DEC
       PUNC_PAREN_OPEN PUNC_PAREN_CLOSE PUNC_CURLY_OPEN
       PUNC_CURLY_CLOSE PUNC_COMMA NUMBER_HEX PUNC_PAREN_OPEN
       PUNC_PAREN_CLOSE PUNC_CURLY_OPEN PUNC_CURLY_CLOSE PUNC_COMMA
       NUMBER_BIN PUNC_PAREN_OPEN PUNC_PAREN_CLOSE PUNC_CURLY_OPEN
       PUNC_CURLY_CLOSE PUNC_COMMA NUMBER_OCT PUNC_PAREN_OPEN
       PUNC_PAREN_CLOSE PUNC_CURLY_OPEN PUNC_CURLY_CLOSE PUNC_COMMA
       NUMBER_DEC PUNC_PAREN_OPEN PUNC_PAREN_CLOSE PUNC_CURLY_OPEN
       PUNC_CURLY_CLOSE PUNC_CURLY_CLOSE PUNC_PAREN_CLOSE PUNC_SEMI
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
((wrap)({.9(){}, 0x84(){}, 0b1(){}, 0o27(){}, 1e234(){}}));
````

Produces same AST
