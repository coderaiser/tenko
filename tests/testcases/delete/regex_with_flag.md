# Tenko parser test case

- Path: tests/testcases/delete/regex_with_flag.md

> :: delete
>
> ::> regex with flag

## Input

`````js
delete /foo/g.bar;
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
        type: 'UnaryExpression',
        loc:{start:{line:1,column:0},end:{line:1,column:17},source:''},
        operator: 'delete',
        prefix: true,
        argument: {
          type: 'MemberExpression',
          loc:{start:{line:1,column:7},end:{line:1,column:17},source:''},
          object: {
            type: 'Literal',
            loc:{start:{line:1,column:7},end:{line:1,column:13},source:''},
            value: null,
            regex: { pattern: 'foo', flags: 'g' },
            raw: '/foo/g'
          },
          property: {
            type: 'Identifier',
            loc:{start:{line:1,column:14},end:{line:1,column:17},source:''},
            name: 'bar'
          },
          computed: false
        }
      }
    }
  ]
}

tokens (6x):
       ID_delete REGEXN PUNC_DOT IDENT PUNC_SEMI
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
(delete (/foo/g.bar));
````

Produces same AST
