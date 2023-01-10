---
layout: default
title: DEFAULT parameter values
nav_order: 2
---

## Calling a procedure or function with DEFAULT parameter values

In T-SQL, you can pass the `DEFAULT` keyword in a call to a procedure or function to indicate that the default value of the parameter, as specified in the declaration of the procedure or function, should be used in the call. Babelfish doesn't support the `DEFAULT` keyword in procedure or function calls.

You can run Babelfish Compass with the `-rewrite` option on SQL source files containing procedure and function calls. Babelfish Compass rewrites the calls with actual default parameter values in place of the `DEFAULT` keyword. Each literal value that replaces a `DEFAULT` keyword is preceded and followed by comments that identify which parameters represent default values. If you change the default value of the parameter in the declaration of the procedure or function, you should update the old parameter values with which the DEFAULT keyword has been replace for all calls to that procedure or function.

--Before rewrite

```sql
dbo.stored_procedure_1( @variable1, parameter_value, DEFAULT, DEFAULT, DEFAULT)
```

--After Babelfish Compass rewrite

```sql
dbo.stored_procedure_1( @variable1, parameter_value, /*REWRITTEN*/ 'N/A' /*DEFAULT*/,
/*REWRITTEN*/ NULL /*DEFAULT*/, /*REWRITTEN*/ 0 /*DEFAULT*/)
```

For information about using Babelfish from both the TDS port and the PostgreSQL port, [visit the Babelfish website](https://babelfishpg.org/docs/usage/interoperability/).
