# Tenko parser test case

- Path: tests/testcases/classes/piggies_in_classes/await/unwrapped/as_class_name.md

> :: classes : piggies in classes : await : unwrapped
>
> ::> as class name

## Input

`````js
class await { }
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
  loc:{start:{line:1,column:0},end:{line:1,column:15},source:''},
  body: [
    {
      type: 'ClassDeclaration',
      loc:{start:{line:1,column:0},end:{line:1,column:15},source:''},
      id: {
        type: 'Identifier',
        loc:{start:{line:1,column:6},end:{line:1,column:11},source:''},
        name: 'await'
      },
      superClass: null,
      body: {
        type: 'ClassBody',
        loc:{start:{line:1,column:12},end:{line:1,column:15},source:''},
        body: []
      }
    }
  ]
}

tokens (5x):
       ID_class ID_await PUNC_CURLY_OPEN PUNC_CURLY_CLOSE
`````

### Strict mode

Parsed with script goal but as if it was starting with `"use strict"` at the top.

_Output same as sloppy mode._

### Module goal

Parsed with the module goal.

`````
throws: Parser error!
  Cannot use this name (await) as a variable name because: Await is illegal as var name with module goal

class await { }
      ^------- error
`````


### Web compat mode

Parsed in sloppy script mode but with the web compat flag enabled.

_Output same as sloppy mode._

## AST Printer

Printer output different from input [sloppy]:

````js
class await{}
````

Produces same AST
