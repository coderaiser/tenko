# Tenko parser test case

- Path: tests/testcases/objects/duplicate_keys/assigment_pattern/double_computed_dupe_key.md

> :: objects : duplicate keys : assigment pattern
>
> ::> double computed dupe key
>
> Note: duplicate keys are NOT a syntax error for assignment patterns (pfew)

## Input

`````js
({[a]: x, [b]: x} = obj)
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
  loc:{start:{line:1,column:0},end:{line:1,column:24},source:''},
  body: [
    {
      type: 'ExpressionStatement',
      loc:{start:{line:1,column:0},end:{line:1,column:24},source:''},
      expression: {
        type: 'AssignmentExpression',
        loc:{start:{line:1,column:1},end:{line:1,column:23},source:''},
        left: {
          type: 'ObjectPattern',
          loc:{start:{line:1,column:1},end:{line:1,column:17},source:''},
          properties: [
            {
              type: 'Property',
              loc:{start:{line:1,column:2},end:{line:1,column:8},source:''},
              key: {
                type: 'Identifier',
                loc:{start:{line:1,column:3},end:{line:1,column:4},source:''},
                name: 'a'
              },
              kind: 'init',
              method: false,
              computed: true,
              value: {
                type: 'Identifier',
                loc:{start:{line:1,column:7},end:{line:1,column:8},source:''},
                name: 'x'
              },
              shorthand: false
            },
            {
              type: 'Property',
              loc:{start:{line:1,column:10},end:{line:1,column:16},source:''},
              key: {
                type: 'Identifier',
                loc:{start:{line:1,column:11},end:{line:1,column:12},source:''},
                name: 'b'
              },
              kind: 'init',
              method: false,
              computed: true,
              value: {
                type: 'Identifier',
                loc:{start:{line:1,column:15},end:{line:1,column:16},source:''},
                name: 'x'
              },
              shorthand: false
            }
          ]
        },
        operator: '=',
        right: {
          type: 'Identifier',
          loc:{start:{line:1,column:20},end:{line:1,column:23},source:''},
          name: 'obj'
        }
      }
    }
  ]
}

tokens (19x):
       PUNC_PAREN_OPEN PUNC_CURLY_OPEN PUNC_BRACKET_OPEN IDENT
       PUNC_BRACKET_CLOSE PUNC_COLON IDENT PUNC_COMMA
       PUNC_BRACKET_OPEN IDENT PUNC_BRACKET_CLOSE PUNC_COLON IDENT
       PUNC_CURLY_CLOSE PUNC_EQ IDENT PUNC_PAREN_CLOSE ASI
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
(({[a]:x, [b]:x} = obj));
````

Produces same AST
