# Tenko parser test case

- Path: tests/testcases/strict_mode/header_requirements_for_directive_in_body/octal_escape_in_func_header_and_the_use_strict_directive_rules/arrow_param_name/package_as_func_param_unicode_escape_no_directive_1.md

> :: strict mode : header requirements for directive in body : octal escape in func header and the use strict directive rules : arrow param name
>
> ::> package as func param unicode escape no directive 1
>
> Octal escapes are okay in sloppy mode. 
>
> `package` is a keyword only in strict mode

## Input

`````js
function foo(p\u0061ckage) { }
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
  loc:{start:{line:1,column:0},end:{line:1,column:30},source:''},
  body: [
    {
      type: 'FunctionDeclaration',
      loc:{start:{line:1,column:0},end:{line:1,column:30},source:''},
      generator: false,
      async: false,
      id: {
        type: 'Identifier',
        loc:{start:{line:1,column:9},end:{line:1,column:12},source:''},
        name: 'foo'
      },
      params: [
        {
          type: 'Identifier',
          loc:{start:{line:1,column:13},end:{line:1,column:25},source:''},
          name: 'package'
        }
      ],
      body: {
        type: 'BlockStatement',
        loc:{start:{line:1,column:27},end:{line:1,column:30},source:''},
        body: []
      }
    }
  ]
}

tokens (8x):
       ID_function IDENT PUNC_PAREN_OPEN IDENT PUNC_PAREN_CLOSE
       PUNC_CURLY_OPEN PUNC_CURLY_CLOSE
`````

### Strict mode

Parsed with script goal but as if it was starting with `"use strict"` at the top.

`````
throws: Parser error!
  Cannot use this name (p\u0061ckage) as a variable name because: Keywords may not have escapes in their name

function foo(p\u0061ckage) { }
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
function foo(package) {}
````

Produces same AST
