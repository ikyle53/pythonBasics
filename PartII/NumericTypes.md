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

> Current operators in Python for numbers
>
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

## Numbers in action  

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

The results are tuples of 2 values because the lines typed at the prompt contain two expressions seperated by commas; that's why the results are displayed in parentheses.  

- Initialize counters to zero before adding to them
- Initialize lists to an empty list before appending to them
- Initialize dictionaries as an empty dictionary before appending to them  

> Side Note: `repr` and `str` are used for display formatting. Both convert arbitrary objects to their string representations. However, `repr` gived more options
> than `str` does.

### Comparing numbers  

`1 < 2` #Less than  
`True`  
`2.0 >= 1` #More than or equal to  
`True`  
`2.0 == 2.0` #Equal to  
`True`  
`2.0 != 2.0` #Does not equal to  
`False`  

### Chaining comparisons for range tests  

Chained comparisons are like shorthand for larger Boolean expressions.  

`X < Y < Z` #Y is only evaluated once in this expression that's being chained  
`True`  
`X < Y and Y < Z` #Here Y is being evaluated twice, which is something to avoid  
`True`  

Numeric comparisons are also based on magnitudes. Floating-point numbers can give different results.  

`1.1 + 2.2 == 3.3`  
`False`  
`1.1 + 2.2`  
`3.3000000000000003`  

`int(1.1 + 2.2) == int(3.3)` #It works once I expressly convert it  
`True`  

This stems from the fact that floating-point numbers cannot represent some values exactly due to their limited number of bits.  

### Division: Classic, Floor, and True  

`X / Y` is true division and it always keeps remainders in floating-point results, regardless of its type.  
`5 / 3`  
`1.6666666666666667`  

`X // Y` is floor division. This operator always truncates fractional remainders down to their floor, regardless of type. Its results type depends on the types of its operands.  
`5 // 3`  
`1`  

> Side-note: `//` Floor division is informally known as Truncating division.  

`math.floor(2.5)`  
`2`  
`math.floor(-2.5)`  
`-3`  
`math.trunc(2.5)`  
`2`  
`math.trunc(-2.5)` #Truncation doesn't work for negatives so Floor division is more of a proper term than truncation division  

Example:  

`5 / 2, 5 / -2`  
`(2.5, -2.5)`  
`5 // 2, 5 // -2`  
`(2, -3)` #Result is truncated (or floored) to -3 rather than -2  

If I REALLY want to truncate towards 0 with a negative I'll have to use the `math.trunc` method.  

`math.trunc(5 / -2)` #Truncation instead of floor  
`-2`  

### Integer precision  

Python 3 supports unlimited size:  

`>>> 9999999999999999999 + 1`  
`10000000000000000000`  

`>>> 2 ** 200`  
`1606938044258990275541962092341162602522202993782792835301376`  

### Complex numbers  

Complex numbers are typically used in engineering and such so I may not use these very often. However, it's important to note that in complex numbers that they use a `j` or `J` suffix the denotes the number as imaginary (for testing purposes perhaps).  

`>>> 1j * 1J`  
`(-1+0j)`  
`>>> 2 + 1j * 3`  
`(2+3j)`  
`>>> (2 + 1j) * 3`  
`(6+3j)`  

### Hex, Octal, Binary, and Conversions  

Octal literal:  
`0o1, 0o20, 0o377`  
`(1, 16, 255)`  

Hex literal:  
`0x01, 0x10, 0xFF`  
`(1, 16, 255)`  

Binary literal:  
`0b1, 0b10000, 0b11111111`  
`(1, 16, 255)`  

How hex/binary map to decimal:  
`>>> 0xFF, (15 * (16 ** 1)) + (15 * (16 ** 0))`  
`(255, 255)`  
`>>> 0x2F, (2 * (16 ** 1)) + (15 * (16 ** 0))`  
`(47, 47)`  
`>>> 0xF, 0b1111, (1*(2**3) + 1*(2**2) + 1*(2**1) + 1*(2**0))`  
`(15, 15, 15)`  

Python prints integer values in decimal (base 10) by default. It has a built-in function though that allows me to convert integers to other bases' digit strings.  
`>>> oct(64), hex(64), bin(64)`  
`('0o100', '0x40', '0b1000000')`  

Opposite way:  
`>>> 64, 0o100, 0x40, 0b1000000`  
`(64, 64, 64, 64)`  

The `eval` function treats strings as though they were Python code. It runs a bit more slowly, but has its uses. The string is assumed that it's a trusted source, so this can be used in nefarious ways if needed (like deleting files).  

`eval('64'), eval('0o100'), eval('0x40'), eval('0b1000000')`  
`(64, 64, 64, 64)`  

Intergers can also be converted to base-specific strings with string formatting method calls and expressions:  
`>>> '{0:o}, {1:x}, {2:b}'.format(64, 64, 64)`  
`'100, 40, 1000000'`  

### Bitwise operations  

`>>> x = 1` #1 decimal is 0001 in bits  
`>>> x << 2` #This shifts left 2 bits making it 0100  
`4`  
`>>> x | 2` #Bitwise OR: 0011  
`3`  
`>>> x & 1` #Bitwise AND: 0001  
`1`  

> These bit-masking operations allow me to encode and extract multiple flags and other values within a single integer.  

These operations can inspect numbers by bit-strings:  
`>>> bin(X << 2)`  
`'0b100'`  
`>>> bin(X & 0b1)`  
`'0b1'`  

Finally, the `bit_length` method let's me query the number of bits required to represent a number's value in binary:  
`>>> bin(X), X.bit_length(), len(bin(X)) - 2`  
`('0b1100011', 7, 7)`  
`>>> bin(256), (256).bit_length(), len(bin(256)) - 2`  
`('0b100000000', 9, 9)`  

### Other built-in numeric tools  

Python has some built-in functions and modules for numeric processing. Example: `pow` and `abs` compute powers and absolute values. There's also the `math` module.  

`>>> import math`  
`>>> math.pi, math.e`  
`(3.141592653589793, 2.718281828459045)`  
`>>> math.sin(2 * math.pi / 180)` #Sin, tangent, cosine  
`0.03489949670250097`  
`>>> math.sqrt(144), math.sqrt(2)` #Square root  
`(12.0, 1.4142135623730951)`  
`>>> pow(2, 4), 2 ** 4, 2.0 ** 4.0` #Exponentiation  
`(16, 16, 16.0)`  
`>>> abs(-42.0), sum((1, 2, 3, 4))` #Absolute value, summation (sum takes a sequence)  
`(42.0, 10)`  
`>>> min(3, 1, 2, 4), max(3, 1, 2, 4)` #Minimum and maximum (accepts a sequence or individual argument)  
`(1, 4)`  
`>>> math.floor(2.567), math.floor(-2.567)` #Floor (next lower integer)  
`(2, -3)`  
`>>> math.trunc(2.567), math.trunc(-2.567)` #Truncate (drop decimal digits)  
`(2, -2)`  
`>>> int(2.567), int(-2.567)` #Truncate (integer conversion (from floating-point in this case))  
`(2, -2)`  
`>>> round(2.567), round(2.467), round(2.567, 2)` #Rounding~  
`(3, 2, 2.57)`  
`>>> '%.1f' % 2.567, '{0:.2f}'.format(2.567)`  
`('2.6', '2.57')`  

Three weays to do square root:  

1. `math.sqrt(144)` #Module way
2. `144 ** .5` #Expression way
3. `pow(144, .5)` #Built-in way

`Random` module:  

Random chooses a random floating-point number between 0 and 1  
`>>> import random`  
`>>> random.random()`  
`0.12800176498774818`  

It can also choose a random number between 2 numbers  
`>>> random.randint(1, 10)`  
`5`  

Lastly, it can choose an item at random from a sequence, and shuffle a list of items randomly:  
`>>> random.choice(['Life of Kyle', 'Holy Grail', 'Wackadoos'])`  
`'Holy Grail'`  

`>>> suits = ['hearts', 'clubs', 'diamonds', 'spades']`  
`>>> random.shuffle(suits)`  
`>>> suits`  
`['spades', 'clubs', 'diamonds', 'hearts']`  

### Decimal  

`Decimal` is another numeric type: the decimal object. Decimals are like floating-point numbers but they have a fixed number of decimal points. That's why they're fixed-precision floating-point values. With decimals I can specify how to round or truncate the extra decimal digits beyond the object's cutoff. It's best suited for things like money and achieving better numeric accuracy.  

Regular integers can give a wacky result due to the hardware involved in calculating the numbers:  
`>>> 0.1 + 0.1 + 0.1 - 0.3`  
`5.551115123125783e-17`  

`Decimal` on the other hand is more exact and accurate. Notice that these numbers are passed in as strings:  
`>>> from decimal import Decimal`  
`>>> Decimal('0.1') + Decimal('0.1') + Decimal('0.1') - Decimal('0.3')`  
`Decimal('0.0')`  

Different decimal point precisions can be used as well. Python will convert up to the largest number of decimal digits automatically:  
`>>> Decimal('0.1') + Decimal('0.10') + Decimal('0.10') - Decimal('0.30')`  
`Decimal('0.00')`  

Floating-point numbers can also be used directly. The single-quotes are not used in this case since I don't want to convert to a string. I want it to be a floating-point that's converted to a decimal:  
`>>> Decimal(0.1) + Decimal(0.1) + Decimal(0.1) - Decimal(0.3)`  
`Decimal('2.775557561565156540423631668E-17')`  

### Setting decimal precision globally  

`>>> import decimal`  #The default precision is set to 28 digits after the decimal  
`>>> decimal.Decimal(1) / decimal.Decimal(7)`  
`Decimal('0.1428571428571428571428571429')` #This is 28 digits after the decimal when we divide 1 by 7  
`>>> decimal.getcontext().prec = 4` #Here I set it to display 4 digits instead of 28
`>>> decimal.Decimal(1) / decimal.Decimal(7)`  
`Decimal('0.1429')`  
`>>> Decimal(0.1) + Decimal(0.1) + Decimal(0.1) - Decimal(0.3)`  
`Decimal('1.110E-17')` #Lastly, this is way closer to 0 than the previous floating-point usage since I scaled down the precision  

### Decimal context manager  

`>>> decimal.Decimal('1.00') / decimal.Decimal('3.00')`  
`Decimal('0.3333333333333333333333333333')` #Precision is set to 28  
`>>> with decimal.localcontext() as ctx:`  #Set the local context as a temp variable called `ctx`  
                `... ctx.prec = 2` #Temporarily set the context of the precision to 2 for the following statement  
                `... decimal.Decimal('1.00') / decimal.Decimal('3.00')`  
`Decimal('0.33')`  

## Fraction type  

Fraction explicitly keeps a numerator and denominator to avoid inaccuracies and limitations of floating-point math. Fraction is a module!  

`>>> from fractions import Fraction`  
`>>> x = Fraction(1, 3)`  
`>>> y = Fraction(4, 6)`  
`>>> x`  
`Fraction(1, 3)`  
`>>> y`  
`Fraction(2, 3)` #Fractions get simplified by greatest common denominator (gcd) and is thus converted automatically  
`>>> print(y)`  
`2/3`  

These fractions can then be used in regular math expressions:  
`>>> x + y`  
`Fraction(1, 1)`  

Fractions are also able to use decimals!  

`>>> Fraction('.25')`  
`Fraction(1, 4)`  
`>>> Fraction('1.25')`  
`Fraction(5, 4)`  
`>>> Fraction('.25') + Fraction('1.25')`  
`Fraction(3, 2)`  
