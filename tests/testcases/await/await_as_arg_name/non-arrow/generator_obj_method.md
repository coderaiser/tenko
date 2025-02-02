# Tenko parser test case

- Path: tests/testcases/await/await_as_arg_name/non-arrow/generator_obj_method.md

> :: await : await as arg name : non-arrow
>
> ::> generator obj method

## Input

`````js
let o = {*f(await){}}
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
      type: 'VariableDeclaration',
      loc:{start:{line:1,column:0},end:{line:1,column:21},source:''},
      kind: 'let',
      declarations: [
        {
          type: 'VariableDeclarator',
          loc:{start:{line:1,column:4},end:{line:1,column:21},source:''},
          id: {
            type: 'Identifier',
            loc:{start:{line:1,column:4},end:{line:1,column:5},source:''},
            name: 'o'
          },
          init: {
            type: 'ObjectExpression',
            loc:{start:{line:1,column:8},end:{line:1,column:21},source:''},
            properties: [
              {
                type: 'Property',
                loc:{start:{line:1,column:9},end:{line:1,column:20},source:''},
                key: {
                  type: 'Identifier',
                  loc:{start:{line:1,column:10},end:{line:1,column:11},source:''},
                  name: 'f'
                },
                kind: 'init',
                method: true,
                computed: false,
                value: {
                  type: 'FunctionExpression',
                  loc:{start:{line:1,column:9},end:{line:1,column:20},source:''},
                  generator: true,
                  async: false,
                  id: null,
                  params: [
                    {
                      type: 'Identifier',
                      loc:{start:{line:1,column:12},end:{line:1,column:17},source:''},
                      name: 'await'
                    }
                  ],
                  body: {
                    type: 'BlockStatement',
                    loc:{start:{line:1,column:18},end:{line:1,column:20},source:''},
                    body: []
                  }
                },
                shorthand: false
              }
            ]
          }
        }
      ]
    }
  ]
}

tokens (14x):
       ID_let IDENT PUNC_EQ PUNC_CURLY_OPEN PUNC_STAR IDENT
       PUNC_PAREN_OPEN ID_await PUNC_PAREN_CLOSE PUNC_CURLY_OPEN
       PUNC_CURLY_CLOSE PUNC_CURLY_CLOSE ASI
`````

### Strict mode

Parsed with script goal but as if it was starting with `"use strict"` at the top.

_Output same as sloppy mode._

### Module goal

Parsed with the module goal.

`````
throws: Parser error!
  Cannot use this name (await) as a variable name because: Await is illegal as var name with module goal

let o = {*f(await){}}
            ^------- error
`````


### Web compat mode

Parsed in sloppy script mode but with the web compat flag enabled.

_Output same as sloppy mode._

## AST Printer

Printer output different from input [sloppy]:

````js
let o = {* f(await){}};
````

Produces same AST
