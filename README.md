# Styleguide for [Idris](http://www.idris-lang.org)

# Table of Contents

# Variable Names

## Type variables
While the most common names for generic types is `ty`, strive to name names specifically.

```idris
-- Bad
Func : Ty -> Ty -> Type

-- Good
Func : HappyTy -> SadTy -> MoodTy

-- Also good
Func : StringInt -> Vect n StringInt
```

If you _must_ fall back to generic naming, we suggest the "tie-dye" naming scheme of a letter plus `y`

```idris
Ty -> Dy -> Ay -> By -> Cy
```

## `%name` directives
Always use `%name` for functions that can be case split. This will help keep your own code clear, and help others extend your code while in development.

```idris
data Tree elem = Empty
               | Node (Tree elem) elem (Tree elem)

%name Tree left, middle, right
```

# Alignment
## `case`
```idris
case foo of
     Baz -> 0
     Bar -> 1
     _   -> 2
```

# `if/then/else`
```idris
-- Good
if foo == bar
  then baz
  else quux

-- Bad
if foo == bar then baz else quux  
```

# Totality
Whenever possible, set the project or file default to total functions. A total function is defined for all possible inputs (on its accepted types). This will alert you to missing cases, and prevent an entire class of errors.

```idris
-- Set all functions to being total functions
%default total
```

# Comments
## Formal Documentation
Formal documentation for a function is give 

```idris
||| Sum a list of numbers
sum : [Int] -> Int
sum [] = 0
sum (x :: xs) = x + sum xs
```

## Clarification
### Single Line
`-- Comment`

### Multiple Lines
Skip the first line

```idris
{%
  comments
%}
```
