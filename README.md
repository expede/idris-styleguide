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
case year of
     1885 -> Frightened
     1955 -> Anxious
     1985 -> Comfortable
     _    -> Curious
```

# `if/then/else`
```idris
-- Good
if milesPerHour == 88
  then TimeWarp
  else RegularTime

-- Bad
if milesPerHour == 88 then TimeWarp else RegularTime
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
`-- Great Scott!`

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
