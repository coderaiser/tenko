# Tenko parser test case

- Path: tests/testcases/classes/piggies_in_classes/await/unwrapped/in_extends_no_args.md

> :: classes : piggies in classes : await : unwrapped
>
> ::> in extends no args

## Input

`````js
class x extends await { }
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
      type: 'ClassDeclaration',
      loc:{start:{line:1,column:0},end:{line:1,column:25},source:''},
      id: {
        type: 'Identifier',
        loc:{start:{line:1,column:6},end:{line:1,column:7},source:''},
        name: 'x'
      },
      superClass: {
        type: 'Identifier',
        loc:{start:{line:1,column:16},end:{line:1,column:21},source:''},
        name: 'await'
      },
      body: {
        type: 'ClassBody',
        loc:{start:{line:1,column:22},end:{line:1,column:25},source:''},
        body: []
      }
    }
  ]
}

tokens (7x):
       ID_class IDENT ID_extends ID_await PUNC_CURLY_OPEN
       PUNC_CURLY_CLOSE
`````

### Strict mode

Parsed with script goal but as if it was starting with `"use strict"` at the top.

_Output same as sloppy mode._

### Module goal

Parsed with the module goal.

`````
throws: Parser error!
  An `await` expression is not allowed here

class x extends await { }
                ^------- error
`````


### Web compat mode

Parsed in sloppy script mode but with the web compat flag enabled.

_Output same as sloppy mode._

## AST Printer

Printer output different from input [sloppy]:

````js
class x extends (await) {}
````

Produces same AST
