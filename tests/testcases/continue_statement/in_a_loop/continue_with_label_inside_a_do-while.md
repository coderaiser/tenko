# Tenko parser test case

- Path: tests/testcases/continue_statement/in_a_loop/continue_with_label_inside_a_do-while.md

> :: continue statement : in a loop
>
> ::> continue with label inside a do-while

## Input

`````js
foo: do continue foo; while(foo);
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
  loc:{start:{line:1,column:0},end:{line:1,column:33},source:''},
  body: [
    {
      type: 'LabeledStatement',
      loc:{start:{line:1,column:0},end:{line:1,column:33},source:''},
      label: {
        type: 'Identifier',
        loc:{start:{line:1,column:0},end:{line:1,column:3},source:''},
        name: 'foo'
      },
      body: {
        type: 'DoWhileStatement',
        loc:{start:{line:1,column:5},end:{line:1,column:33},source:''},
        body: {
          type: 'ContinueStatement',
          loc:{start:{line:1,column:8},end:{line:1,column:21},source:''},
          label: {
            type: 'Identifier',
            loc:{start:{line:1,column:17},end:{line:1,column:20},source:''},
            name: 'foo'
          }
        },
        test: {
          type: 'Identifier',
          loc:{start:{line:1,column:28},end:{line:1,column:31},source:''},
          name: 'foo'
        }
      }
    }
  ]
}

tokens (12x):
       IDENT PUNC_COLON ID_do ID_continue IDENT PUNC_SEMI ID_while
       PUNC_PAREN_OPEN IDENT PUNC_PAREN_CLOSE PUNC_SEMI
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
foo: do continue foo; while (foo);
````

Produces same AST
