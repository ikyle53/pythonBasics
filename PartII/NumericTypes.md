# Numeric Types

In Python numbers are not a single object type. They're a category of similar types. It consists of usual numbers, floating points, and literals to make up expressions.  

- Interger and floating-point objects
- Complex number objects
- Decimal: fixed-precision objects
- Fractions: rational number objects
- Sets: collections with numeric operations
- Booleans: true and false
- Built-in functions and modules: `round`, `math`, `random`, and more
- Expressions: unlimited integer precision; bitwise operations, hex, octal, and binary formats
- Third party extensions: vectors, libraries, vizualizations, plotting, and more  

## Numeric Literals  

- Integers - `1234, -24, 0, 99999999`
- floating-point numbers - `1.23, 1., 14e-10, 4E210, 4.0e`
- Octal, hex, and binary literals - `0o177, 0x9ff, )b101010`
- Complex number literals - `3+4j, 3.0+4.0j, 3J`
- Sets - `set('spam'), {1, 2, 3, 4}`
- Decimal - `Decimal('1.0'), Fraction(1, 3)`
- Boolean - `bool(X), True, False`  

### Integers  

Integers are written as strings of decimal digits. Floating-point numbers have a decimal point and/or an optional signed exponenet introduced by an `e` or `E` and followed by an optional sign. If I write a number with a decimal point or exponent Python makes ita floating-point object and uses floating-point math (not integer math) when it's used in an expression.  

### Hexidecimal, Octal, and Binary literals  

Decimal - Base 10  
Hexidecimal - Base 16  
Octal - Base 8  
Binary - Base 2  

## Built-in Numeric Tools  

Expression operators:  
`+, -, *, /, >>, **, &`  

Built-in mathematical functions:  
`pow, abs, round, int, hex, bin`  

Utility modules:  
`random, math`  

## Expression operators  

An expression is a combination of numbers (or other objects) and operators (+, -, *) that computes a value when executed by Python.  
`X + Y` adds 2 numbers and uses the `+` operator. The sum of X and Y is another number object.  

> Current operators in Python for numbers:  

> - `yield x` - generator function `send` protocol
> - `lambda args: expression` - Anonymous function generator
> - `x if y else z` - Ternary selection(x is evaluated only if y is true)
> - `x or y` - Logical OR (y is evaluated only if x is false)
> - `x and y` - Logical AND (y is evaluated only if x is true)
> - `not x` - Logical negation
> - `x in y, x not in y` - Membership (iterables, sets)
> - `x is y, x is not y` - Object identity tests
> - `x < y, x <= y, x > y, x => y` - Magnitude comparison, set subset and superset
> - `x == y, x != y` - Value equality operators
> - `x | y` - Bitwise OR, set union
> - `x ^ y` - Bitwise XOR, set symmetric difference
> - `x & y` - Bitwise AND, set intersection
> - `x << y, x >> y` - Shift x left or right by y bits
> - `x + y` - Addition, concatenation
> - `x - y` - Subtraction, set difference
> - `x * y` - Multiplication, repetition
> - `x % y` - Remainder, format
> - `x / y, x // y` - Division, true and floor
> - `-x, +x` - Negation, identity
> - `~x` - Bitwise NOT (inversion)
> - `x ** y` - Power (exponentiation)
> - `x[i]` - Indexing (sequence, mapping, others)
> - `x[i:j:k]` - Slicing
> - `x(...)` - Call (function, method, class, other callable)
> - `x.attr` - Attribute reference
> - `(...)` - Tuple, expression, generator expression
> - `[...]` - List, list comprehension
> - `{...}` - Dictionary, set, set and dictionary comprehensions  

### Precedence rules  

Python does have a precedence order for its operators. Operators LOWER on the list above take precedence before those that are higher on the list.  

`X + Y * Z` - The multiplication is done first since it's further down the list that the addition operator.  

Parenthases group subexpressions: I can override the precedence rule with parentheses groupings. Those integers inside the parentheses will be evaluated first and then the rest of the expression will pop off.  

`(X + Y) * Z` or `X + (Y * Z)` - Even though I wouldn't need to use the parentheses in the second expression it's generally good practice to do it in bigger expressions for reliability and readability.  

## Numbers in action:  

`>>> a = 3`  
`>>> b = 4`  
`>>> a + 1, a -1`  
`(4, 2)`  
`>>> b * 3, b / 2`  
`(12, 2.0)`  
`>>> a % 2, b ** 2`  
`(1, 16)`  
`>>> 2 + 4.0, 2.0 ** b`  
`(6.0, 16.0)`  

The results are tuples of 2 values because the lines typed at the promt contain two expressions seperated by commas; that's why the results are displayed in parentheses.  

Firstly:  

- Variable are created when they are first assigned values
- Variables are replaced with their values when used in expressions