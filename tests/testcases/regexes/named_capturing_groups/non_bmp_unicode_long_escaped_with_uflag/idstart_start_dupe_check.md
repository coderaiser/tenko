# Tenko parser test case

- Path: tests/testcases/regexes/named_capturing_groups/non_bmp_unicode_long_escaped_with_uflag/idstart_start_dupe_check.md

> :: regexes : named capturing groups : non bmp unicode long escaped with uflag
>
> ::> idstart start dupe check
>
> Capturing group name starts with a non-bmp unicode ID_START
>
> This confirms whether back reference can reference a group with unicode non-bmp char `\u{2F9DF}` / `\ud87e\udddf`,

## PASS

## Input

`````js
/(?<\u{2F9DF}xyz>foo)met\k<\ud87e\udddfxyz>/u
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
  loc:{start:{line:1,column:0},end:{line:1,column:45},source:''},
  body: [
    {
      type: 'ExpressionStatement',
      loc:{start:{line:1,column:0},end:{line:1,column:45},source:''},
      expression: {
        type: 'Literal',
        loc:{start:{line:1,column:0},end:{line:1,column:45},source:''},
        value: null,
        regex: {
          pattern: '(?<\\u{2F9DF}xyz>foo)met\\k<\\ud87e\\udddfxyz>',
          flags: 'u'
        },
        raw: '/(?<\\u{2F9DF}xyz>foo)met\\k<\\ud87e\\udddfxyz>/u'
      }
    }
  ]
}

tokens (3x):
       REGEXU ASI
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
/(?<\u{2F9DF}xyz>foo)met\k<\ud87e\udddfxyz>/u;
````

Produces same AST
