# Tenko parser test case

- Path: tests/testcases/yield/yield_in_group_in_param_default/group_yield_piggy_test_in_func_param_default_2.md

> :: yield : yield in group in param default
>
> ::> group yield piggy test in func param default 2
>
> a function does reset the yield/await state for params
>
> https://tc39.github.io/ecma262/#sec-arrow-function-definitions-static-semantics-early-errors
>
> > It is a Syntax Error if ArrowParameters Contains YieldExpression is true.
>
> The arrow parens inherit the generator state from the parent scope (unlike regular funcs, who reset it)

## Input

`````js
function *f(){    function g(x=(yield)=y){}   }
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
  loc:{start:{line:1,column:0},end:{line:1,column:47},source:''},
  body: [
    {
      type: 'FunctionDeclaration',
      loc:{start:{line:1,column:0},end:{line:1,column:47},source:''},
      generator: true,
      async: false,
      id: {
        type: 'Identifier',
        loc:{start:{line:1,column:10},end:{line:1,column:11},source:''},
        name: 'f'
      },
      params: [],
      body: {
        type: 'BlockStatement',
        loc:{start:{line:1,column:13},end:{line:1,column:47},source:''},
        body: [
          {
            type: 'FunctionDeclaration',
            loc:{start:{line:1,column:18},end:{line:1,column:43},source:''},
            generator: false,
            async: false,
            id: {
              type: 'Identifier',
              loc:{start:{line:1,column:27},end:{line:1,column:28},source:''},
              name: 'g'
            },
            params: [
              {
                type: 'AssignmentPattern',
                loc:{start:{line:1,column:29},end:{line:1,column:40},source:''},
                left: {
                  type: 'Identifier',
                  loc:{start:{line:1,column:29},end:{line:1,column:30},source:''},
                  name: 'x'
                },
                right: {
                  type: 'AssignmentExpression',
                  loc:{start:{line:1,column:31},end:{line:1,column:40},source:''},
                  left: {
                    type: 'Identifier',
                    loc:{start:{line:1,column:32},end:{line:1,column:37},source:''},
                    name: 'yield'
                  },
                  operator: '=',
                  right: {
                    type: 'Identifier',
                    loc:{start:{line:1,column:39},end:{line:1,column:40},source:''},
                    name: 'y'
                  }
                }
              }
            ],
            body: {
              type: 'BlockStatement',
              loc:{start:{line:1,column:41},end:{line:1,column:43},source:''},
              body: []
            }
          }
        ]
      }
    }
  ]
}

tokens (21x):
       ID_function PUNC_STAR IDENT PUNC_PAREN_OPEN PUNC_PAREN_CLOSE
       PUNC_CURLY_OPEN ID_function IDENT PUNC_PAREN_OPEN IDENT PUNC_EQ
       PUNC_PAREN_OPEN ID_yield PUNC_PAREN_CLOSE PUNC_EQ IDENT
       PUNC_PAREN_CLOSE PUNC_CURLY_OPEN PUNC_CURLY_CLOSE
       PUNC_CURLY_CLOSE
`````

### Strict mode

Parsed with script goal but as if it was starting with `"use strict"` at the top.

`````
throws: Parser error!
  Cannot use `yield` outside of generator functions when in strict mode

function *f(){    function g(x=(yield)=y){}   }
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
function* f() {function g(x = (yield = y)) {}}
````

Produces same AST
