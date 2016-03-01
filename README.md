# Styleguide for [Idris](http://www.idris-lang.org)

# Table of Contents

# Variable Names

## `%name` directives
Always use 

# Indentation

# `if ... then ... else`

# Totality
Whenever possible, set the project or file default to total functions. A total function is defined for all possible inputs (on its accepted types). This will alert you to missing cases, and prevent an entire class of errors.

```idris
-- Set all functions to being total functions
%default total
```
