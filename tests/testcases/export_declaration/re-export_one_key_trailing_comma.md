# Tenko parser test case

- Path: tests/testcases/export_declaration/re-export_one_key_trailing_comma.md

> :: export declaration
>
> ::> re-export one key trailing comma

## Input

`````js
export {x,} from "foo"
`````

## Output

_Note: the whole output block is auto-generated. Manual changes will be overwritten!_

Below follow outputs in four parsing modes: sloppy mode, strict mode script goal, module goal, web compat mode (always sloppy).

Note that the output parts are auto-generated by the test runner to reflect actual result.

### Sloppy mode

Parsed with script goal and as if the code did not start with strict mode header.

`````
throws: Parser error!
  The `export` keyword can only be used with the module goal

export {x,} from "foo"
^------- error
`````

### Strict mode

Parsed with script goal but as if it was starting with `"use strict"` at the top.

_Output same as sloppy mode._

### Module goal

Parsed with the module goal.

`````
ast: {
  type: 'Program',
  loc:{start:{line:1,column:0},end:{line:1,column:22},source:''},
  body: [
    {
      type: 'ExportNamedDeclaration',
      loc:{start:{line:1,column:0},end:{line:1,column:22},source:''},
      specifiers: [
        {
          type: 'ExportSpecifier',
          loc:{start:{line:1,column:8},end:{line:1,column:9},source:''},
          local: {
            type: 'Identifier',
            loc:{start:{line:1,column:8},end:{line:1,column:9},source:''},
            name: 'x'
          },
          exported: {
            type: 'Identifier',
            loc:{start:{line:1,column:8},end:{line:1,column:9},source:''},
            name: 'x'
          }
        }
      ],
      declaration: null,
      source: {
        type: 'Literal',
        loc:{start:{line:1,column:17},end:{line:1,column:22},source:''},
        value: 'foo',
        raw: '"foo"'
      }
    }
  ]
}

tokens (9x):
       ID_export PUNC_CURLY_OPEN IDENT PUNC_COMMA PUNC_CURLY_CLOSE
       ID_from STRING_DOUBLE ASI
`````


### Web compat mode

Parsed in sloppy script mode but with the web compat flag enabled.

_Output same as sloppy mode._

## AST Printer

Printer output different from input [module]:

````js
export {x} from "foo"
````

Produces same AST
