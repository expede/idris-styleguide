# Styleguide for [Idris](http://www.idris-lang.org)
![](http://www.idris-lang.org/logo/logo.png)

# Table of Contents
- [Naming](#naming)
  - [Type Variables](#type-variables)
  - [`%name` directives](#name-directives)
- [Alignment](#alignment)
  - [`case`](#case)
  - [`if/then/else](#if-then-else)
- [Totality](#totality)
- [Comments](#comments)
  - [Formal Documentation](#formal-documentation)
  - [Clarification](#clarification)
  - [Single Line](#single-line)
  - [Multiple Lines](#multiple-lines)

# Naming
## Type variables
While the most common names for generic types is `ty`, strive to name names specifically.

```idris
-- Bad
SomeFunc : Ty -> Ty -> Type

-- Good
SomeFunc : HappyTy -> SadTy -> MoodTy

-- Also good
SomeFunc : StringInt -> [StringInt]
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
