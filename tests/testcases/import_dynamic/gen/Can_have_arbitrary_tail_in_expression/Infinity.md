# Tenko parser autogenerated test case

- From: tests/testcases/import_dynamic/autogen.md
- Path: tests/testcases/import_dynamic/gen/Can_have_arbitrary_tail_in_expression/Infinity.md

> :: import dynamic : gen : Can have arbitrary tail in expression
>
> ::> Infinity

## Input

- `es = Infinity`

`````js
foo(import('foo').den());
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
  loc:{start:{line:1,column:0},end:{line:1,column:25},source:''},
  body: [
    {
      type: 'ExpressionStatement',
      loc:{start:{line:1,column:0},end:{line:1,column:25},source:''},
      expression: {
        type: 'CallExpression',
        loc:{start:{line:1,column:0},end:{line:1,column:24},source:''},
        callee: {
          type: 'Identifier',
          loc:{start:{line:1,column:0},end:{line:1,column:3},source:''},
          name: 'foo'
        },
        arguments: [
          {
            type: 'CallExpression',
            loc:{start:{line:1,column:4},end:{line:1,column:23},source:''},
            callee: {
              type: 'MemberExpression',
              loc:{start:{line:1,column:4},end:{line:1,column:21},source:''},
              object: {
                type: 'CallExpression',
                loc:{start:{line:1,column:4},end:{line:1,column:17},source:''},
                callee: {
                  type: 'Import',
                  loc:{start:{line:1,column:4},end:{line:1,column:10},source:''}
                },
                arguments: [
                  {
                    type: 'Literal',
                    loc:{start:{line:1,column:11},end:{line:1,column:16},source:''},
                    value: 'foo',
                    raw: "'foo'"
                  }
                ]
              },
              property: {
                type: 'Identifier',
                loc:{start:{line:1,column:18},end:{line:1,column:21},source:''},
                name: 'den'
              },
              computed: false
            },
            arguments: []
          }
        ]
      }
    }
  ]
}

tokens (13x):
       IDENT PUNC_PAREN_OPEN ID_import PUNC_PAREN_OPEN STRING_SINGLE
       PUNC_PAREN_CLOSE PUNC_DOT IDENT PUNC_PAREN_OPEN
       PUNC_PAREN_CLOSE PUNC_PAREN_CLOSE PUNC_SEMI
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
((foo)(((import('foo')).den)()));
````

Produces same AST
