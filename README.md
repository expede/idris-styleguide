*NOTE: This styleguide is in early stages & thus very incomplete and subject to rapid change*

# [Idris](http://www.idris-lang.org) Styleguide
![](http://www.idris-lang.org/logo/logo.png)

# Table of Contents
- [Naming](#naming)
  - [Type Variables](#type-variables)
  - [`%name` directives](#name-directives)
- [Formatting](#formatting)
  - [Line Length](#line-length)
  - [Alignment](#alignment)
    - [Indentation](#indentation)
    - [`case`](#case)
    - [`if/then/else`](#if-then-else)
    - [Multiline `data` Declarations](#multiline-data-declarations)
  - [Blank Lines](#blank-lines)
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

-- Automatic variable naming:
Eq elem => Eq (Tree elem) where
  (==) Empty y = ?Eq_rhs_3
  (==) (Node left x middle) y = ?Eq_rhs_1
  (/=) x y = ?Eq_rhs_2
```

# Formatting
## Line Length
Observe the standard 80-character limit

## Alignment
### Indentation
Tabs are illegal. Use 2 spaces normally, unless it helps to improve the comprehension of the structure of the code, such as in the cases listed below.

### `case`
```idris
case year of
     1885 => Frightened
     1955 => Anxious
     1985 => Comfortable
     _    => Curious
```

### `if/then/else`
```idris
-- Good
if milesPerHour == 88
  then TimeWarp
  else RegularTime

-- Bad
if milesPerHour == 88 then TimeWarp else RegularTime
```

### Multiline `data` Declarations
Align the `|` with the `=`

```idris
data Maybe a = Nothing
             | Just a
```

## Blank Lines
Use one blank line to break apart logical groups of imports.
Place a blank line between functions, type definitions, and so on.
Do not place a blank line between type signatures and function definitions.

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
mySum : List Int -> Int
mySum [] = 0
mySum (x :: xs) = x + mySum xs
```

## Clarification
### Single Line
```idris
-- Great Scott!
```

### Multiple Lines
Skip the first line

```idris
{-
  Unbelievable, that old Biff could have chosen that particular date.
  It could mean that that point in time inherently contains some sort of cosmic significance.
  Almost as if it were the temporal junction point for the entire space-time continuum.
  On the other hand, it could just be an amazing coincidence. 
-}
```
