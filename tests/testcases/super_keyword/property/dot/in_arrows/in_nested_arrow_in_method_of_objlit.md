# Tenko parser test case

- Path: tests/testcases/super_keyword/property/dot/in_arrows/in_nested_arrow_in_method_of_objlit.md

> :: super keyword : property : dot : in arrows
>
> ::> in nested arrow in method of objlit

## Input

`````js
x={ foo(){ return () => () => super.foo; }}
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
  loc:{start:{line:1,column:0},end:{line:1,column:43},source:''},
  body: [
    {
      type: 'ExpressionStatement',
      loc:{start:{line:1,column:0},end:{line:1,column:43},source:''},
      expression: {
        type: 'AssignmentExpression',
        loc:{start:{line:1,column:0},end:{line:1,column:43},source:''},
        left: {
          type: 'Identifier',
          loc:{start:{line:1,column:0},end:{line:1,column:1},source:''},
          name: 'x'
        },
        operator: '=',
        right: {
          type: 'ObjectExpression',
          loc:{start:{line:1,column:2},end:{line:1,column:43},source:''},
          properties: [
            {
              type: 'Property',
              loc:{start:{line:1,column:4},end:{line:1,column:42},source:''},
              key: {
                type: 'Identifier',
                loc:{start:{line:1,column:4},end:{line:1,column:7},source:''},
                name: 'foo'
              },
              kind: 'init',
              method: true,
              computed: false,
              value: {
                type: 'FunctionExpression',
                loc:{start:{line:1,column:4},end:{line:1,column:42},source:''},
                generator: false,
                async: false,
                id: null,
                params: [],
                body: {
                  type: 'BlockStatement',
                  loc:{start:{line:1,column:9},end:{line:1,column:42},source:''},
                  body: [
                    {
                      type: 'ReturnStatement',
                      loc:{start:{line:1,column:11},end:{line:1,column:40},source:''},
                      argument: {
                        type: 'ArrowFunctionExpression',
                        loc:{start:{line:1,column:18},end:{line:1,column:39},source:''},
                        params: [],
                        id: null,
                        generator: false,
                        async: false,
                        expression: true,
                        body: {
                          type: 'ArrowFunctionExpression',
                          loc:{start:{line:1,column:24},end:{line:1,column:39},source:''},
                          params: [],
                          id: null,
                          generator: false,
                          async: false,
                          expression: true,
                          body: {
                            type: 'MemberExpression',
                            loc:{start:{line:1,column:30},end:{line:1,column:39},source:''},
                            object: {
                              type: 'Super',
                              loc:{start:{line:1,column:30},end:{line:1,column:35},source:''}
                            },
                            property: {
                              type: 'Identifier',
                              loc:{start:{line:1,column:36},end:{line:1,column:39},source:''},
                              name: 'foo'
                            },
                            computed: false
                          }
                        }
                      }
                    }
                  ]
                }
              },
              shorthand: false
            }
          ]
        }
      }
    }
  ]
}

tokens (22x):
       IDENT PUNC_EQ PUNC_CURLY_OPEN IDENT PUNC_PAREN_OPEN
       PUNC_PAREN_CLOSE PUNC_CURLY_OPEN ID_return PUNC_PAREN_OPEN
       PUNC_PAREN_CLOSE PUNC_EQ_GT PUNC_PAREN_OPEN PUNC_PAREN_CLOSE
       PUNC_EQ_GT ID_super PUNC_DOT IDENT PUNC_SEMI PUNC_CURLY_CLOSE
       PUNC_CURLY_CLOSE ASI
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
((x = {foo(){return () => (() => (super.foo));}}));
````

Produces same AST
