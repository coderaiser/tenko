# Tenko parser test case

- Path: tests/testcases/new/new_operator/multi_arguments/dynamic_member.md

> :: new : new operator : multi arguments
>
> ::> dynamic member

## Input

`````js
new Foo["bar"](X, Y, Z)
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
  loc:{start:{line:1,column:0},end:{line:1,column:23},source:''},
  body: [
    {
      type: 'ExpressionStatement',
      loc:{start:{line:1,column:0},end:{line:1,column:23},source:''},
      expression: {
        type: 'NewExpression',
        loc:{start:{line:1,column:0},end:{line:1,column:23},source:''},
        arguments: [
          {
            type: 'Identifier',
            loc:{start:{line:1,column:15},end:{line:1,column:16},source:''},
            name: 'X'
          },
          {
            type: 'Identifier',
            loc:{start:{line:1,column:18},end:{line:1,column:19},source:''},
            name: 'Y'
          },
          {
            type: 'Identifier',
            loc:{start:{line:1,column:21},end:{line:1,column:22},source:''},
            name: 'Z'
          }
        ],
        callee: {
          type: 'MemberExpression',
          loc:{start:{line:1,column:4},end:{line:1,column:14},source:''},
          object: {
            type: 'Identifier',
            loc:{start:{line:1,column:4},end:{line:1,column:7},source:''},
            name: 'Foo'
          },
          property: {
            type: 'Literal',
            loc:{start:{line:1,column:8},end:{line:1,column:13},source:''},
            value: 'bar',
            raw: '"bar"'
          },
          computed: true
        }
      }
    }
  ]
}

tokens (14x):
       ID_new IDENT PUNC_BRACKET_OPEN STRING_DOUBLE PUNC_BRACKET_CLOSE
       PUNC_PAREN_OPEN IDENT PUNC_COMMA IDENT PUNC_COMMA IDENT
       PUNC_PAREN_CLOSE ASI
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
new ((Foo)["bar"])(X, Y, Z);
````

Produces same AST
