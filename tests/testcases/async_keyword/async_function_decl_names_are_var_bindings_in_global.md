# Tenko parser test case

- Path: tests/testcases/async_keyword/async_function_decl_names_are_var_bindings_in_global.md

> :: async keyword
>
> ::> async function decl names are var bindings in global
>
> global func decls are considered `var` in SCRIPT goal; https://tc39.github.io/ecma262/#sec-block-static-semantics-toplevellexicallydeclarednames

## Input

`````js
async function f() {} var f;
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
  loc:{start:{line:1,column:0},end:{line:1,column:28},source:''},
  body: [
    {
      type: 'FunctionDeclaration',
      loc:{start:{line:1,column:0},end:{line:1,column:21},source:''},
      generator: false,
      async: true,
      id: {
        type: 'Identifier',
        loc:{start:{line:1,column:15},end:{line:1,column:16},source:''},
        name: 'f'
      },
      params: [],
      body: {
        type: 'BlockStatement',
        loc:{start:{line:1,column:19},end:{line:1,column:21},source:''},
        body: []
      }
    },
    {
      type: 'VariableDeclaration',
      loc:{start:{line:1,column:22},end:{line:1,column:28},source:''},
      kind: 'var',
      declarations: [
        {
          type: 'VariableDeclarator',
          loc:{start:{line:1,column:26},end:{line:1,column:27},source:''},
          id: {
            type: 'Identifier',
            loc:{start:{line:1,column:26},end:{line:1,column:27},source:''},
            name: 'f'
          },
          init: null
        }
      ]
    }
  ]
}

tokens (11x):
       ID_async ID_function IDENT PUNC_PAREN_OPEN PUNC_PAREN_CLOSE
       PUNC_CURLY_OPEN PUNC_CURLY_CLOSE ID_var IDENT PUNC_SEMI
`````

### Strict mode

Parsed with script goal but as if it was starting with `"use strict"` at the top.

_Output same as sloppy mode._

### Module goal

Parsed with the module goal.

`````
throws: Parser error!
  Found a var binding that is duplicate of a lexical binding on the same or lower statement level

async function f() {} var f;
                          ^------- error
`````


### Web compat mode

Parsed in sloppy script mode but with the web compat flag enabled.

_Output same as sloppy mode._

## AST Printer

Printer output different from input [sloppy]:

````js
async function f() {}
var f;
````

Produces same AST
