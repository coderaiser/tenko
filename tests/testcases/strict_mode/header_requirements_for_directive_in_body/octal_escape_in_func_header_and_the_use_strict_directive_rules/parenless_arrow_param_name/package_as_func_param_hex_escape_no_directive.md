# Tenko parser test case

- Path: tests/testcases/strict_mode/header_requirements_for_directive_in_body/octal_escape_in_func_header_and_the_use_strict_directive_rules/parenless_arrow_param_name/package_as_func_param_hex_escape_no_directive.md

> :: strict mode : header requirements for directive in body : octal escape in func header and the use strict directive rules : parenless arrow param name
>
> ::> package as func param hex escape no directive
>
> Octal escapes are okay in sloppy mode. 
>
> `package` is a keyword only in strict mode

## Input


`````js
p\x61ckage => { }
`````

## Output

_Note: the whole output block is auto-generated. Manual changes will be overwritten!_

Below follow outputs in four parsing modes: sloppy mode, strict mode script goal, module goal, web compat mode (always sloppy).

Note that the output parts are auto-generated by the test runner to reflect actual result.

### Sloppy mode

Parsed with script goal and as if the code did not start with strict mode header.

`````
throws: Lexer error!
    Only unicode escapes are supported in identifier escapes

p\x61ckage => { }
^------- error
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
