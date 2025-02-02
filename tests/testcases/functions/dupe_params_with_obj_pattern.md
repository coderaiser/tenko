# Tenko parser test case

- Path: tests/testcases/functions/dupe_params_with_obj_pattern.md

> :: functions
>
> ::> dupe params with obj pattern
>
> The param name is a future reserved keyword and illegal to use as param name in strict mode. But fine in sloppy mode.
>
> There was a regression where this would still throw in sloppy mode because the future keyword detection would mark the param as "complex" in order for it to throw if the body turned out to be strict mode. Basically solved it by adding another state to indicate non-strict-but-simple.
>
> Another regression was that patterns and rest were not detected as complex.

## Input

`````js
function i(package,package){}
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
  loc:{start:{line:1,column:0},end:{line:1,column:29},source:''},
  body: [
    {
      type: 'FunctionDeclaration',
      loc:{start:{line:1,column:0},end:{line:1,column:29},source:''},
      generator: false,
      async: false,
      id: {
        type: 'Identifier',
        loc:{start:{line:1,column:9},end:{line:1,column:10},source:''},
        name: 'i'
      },
      params: [
        {
          type: 'Identifier',
          loc:{start:{line:1,column:11},end:{line:1,column:18},source:''},
          name: 'package'
        },
        {
          type: 'Identifier',
          loc:{start:{line:1,column:19},end:{line:1,column:26},source:''},
          name: 'package'
        }
      ],
      body: {
        type: 'BlockStatement',
        loc:{start:{line:1,column:27},end:{line:1,column:29},source:''},
        body: []
      }
    }
  ]
}

tokens (10x):
       ID_function IDENT PUNC_PAREN_OPEN ID_package PUNC_COMMA
       ID_package PUNC_PAREN_CLOSE PUNC_CURLY_OPEN PUNC_CURLY_CLOSE
`````

### Strict mode

Parsed with script goal but as if it was starting with `"use strict"` at the top.

`````
throws: Parser error!
  Cannot use this name (package) as a variable name because: Cannot use this reserved word as a variable name in strict mode

function i(package,package){}
           ^------- error
`````


### Module goal

Parsed with the module goal.

_Output same as strict mode._

### Web compat mode

Parsed in sloppy script mode but with the web compat flag enabled.

_Output same as sloppy mode._

## AST Printer

Printer output different from input [sloppy]:

````js
function i(package, package) {}
````

Produces same AST
