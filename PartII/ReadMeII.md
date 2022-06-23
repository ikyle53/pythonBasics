# Part II

## Python object types

This part of the book focuses on "Things" an "Stuff". The things are the operations (addition, concatenation). The stuff are objects in which the things are operating on.

### "Stuff" (Objects)

In Python objects are essentially just pieces of memory. These are built into python and can also be created using classes or things like C extension librares. In Python EVERYTHING is an object.

Python programs can be decomposed into modules, expressions, and objects:

1. Programs are composed of modules
2. Modules contain statements
3. Statements contain expressions
4. Expressions create and process objects

Traditional programming often stresses three different pillars~ Python has tools in all 3:

1. Sequence - Do this, then that
2. Selection - Do this if that is true
3. Repetition - Do this many times

Here are the built in objects within Python:

1. Numbers `1234, 3.1415, 3+4j, Ob111, Decimal(), Fraction()`
2. Strings `'spam', "Kyle's", b'a\x01c', u'sp\xc4m'`
3. Lists `[1[2, 'three'], 4.5], list(range(10))` Provides ordred collections of other objects
4. Dictionaries `{'food': 'spam', 'taste': 'yum'}, dict(hours=10)`
5. Tuples `(1, 'spam', 4, 'U'), tuple('spam'), namedtuple`
6. Files `open('eggs.txt'), open(r'C:\ham.bin', 'wb')`
7. Sets `set('abc'), {'a', 'b', 'c'}`
8. Other core types `Booleans, types, none`
9. Program unit types `Functions, modules, classes`
10. Implementation-related types `Compiled code, stack tracebacks`

## Numbers

`str` is a built-in string function that converts something to a string. Example:
`print(str(2 ** 10))` would print out the string of `"1024"` rather than `1024`
We also have `len` which means length and gives a print out of an objects length:
`len(str(2 ** 1000000))` this would give us 301,030 digits of length!

### Floating points  

When working with floating numbers we can run into python's very precise calculations:  
Running `3.14 * 2` would give us the number `6.28300000000000004` This is known as the as-code `repr`  

However, when we run the same code with `print` we'll get a more user friendly output:  
`print(3.14 * 2)` prints `6.283`  

### Math module  

The math module is a nice built in tool to do...math!  
`>>> import math`  
`>>> math.pi`  
`>>> 3.141592653589793`  
`>>> math.sqrt(85)`  
`>>> 9.219544457292887`  
This module sports some advanced numeric tools as functions. It also has the `random` module.  
`>>> import random`  
`>>> random.random()`  
`0.72352352347457`  
`>>> random.choice([1, 2, 3, 4])`  
`1`  

## Strings  

Strings are interesting. They record both textual information and arbitrary collections of bytes (like image file's contents). It's the first example of a `sequence`.  

`**Sequences**` maintain a left-to-right order among the items they contain: these items are stored and fetched by their relative positions in the sequence. Strings can be described as sequences of one-character strings.

This is a good example of sequence and the one-character strings idea:  
`>>> S = 'Spam'`  
`>>> len(S)`  
`4`  
`'S'`is set as a variable of 'Spam' and the length function is then used to determine its length, which prints out 4. This is a string made of 4 one-character strings!  
We can also target each character in the sequence using its indexed position:  
`>>> S[0]`  
`'S'`  
`>>> S[1]`  
`'p'`  
We can also index from the opposite direction:  
`>>> S[-1]`
`'m'`  

### ***Slicing***  

Slicing a string in python is a bit different from other languages, but still kind of the same. The result is returned in a new string object.  

`>>> S`  
`>>> 'Spam'`  
`>>> S[1:3]`  This slices the offsets 1 through 2 and not including 3.  
`pa`  
`>>> S[1:]` Everything past the first gets sliced.  
`'pam'`  
`>>> S[0:3]` Slices everything but the last character.  
`'Spa'`  
`>>> S[:3]` Same as above!  
`'Spa'`  
`>>> S[:-1]` Everything but the last again, but simpler (0:-1). Negative one begins from the end.  
 `'Spa'`  
`>>> S[:]` This is a top-level copy of `S` (0:len(S)).
`'Spam'`  

### ***Concatenation***  

Strings are also able to be concatenated using the `+` sign. We can also use `repetition`:  

`>>> S + 'xyz'` Concatenates 'xyz' onto 'Spam'.  
`'Spamxyz'`  
`>>> S * 8` This repeats 'Spam' 8 times.  
`'SpamSpamSpamSpamSpamSpamSpamSpam'`  

The `+` sign in Python works differently depending on the type on the object it's used on. Number objects will add the numbers together while string objects will concatenate.  

## ***Immutability***  

Once an object is defined it becomes immutable, which means it can't be overwritten. Python cleans up old objects as you go, so creating a new object is the way to go. However, the core types of **numbers**, **strings**, and **tuples** are the only immutable objects. **Lists**, **ditionaries**, and **sets** are not immutable.  

`>>> S`  
`'Spam'`  
`>>> S[0] = 'z'`  This creates an error because the object is immutable!  
`>>> S = 'z' + S[1:]` This creates a new object of `S` as `'z'` and adds the sliced 'Spam' from index 1 ('p') along with the rest of the string ('am').  
`>>> S`  
`'zpam'`  

## Changing text in-place using `list` and `bytearray`  

### List - this converts the string to a list and uses the join function to piece it back together

`>>> S = 'shrubbery'`  
`>>> L = list(S)`  # Makes a list (array) of each character  
`>>> L`  
`['s', 'h', 'r', 'u', 'b', 'b', 'e', 'r', 'y']`  
`>>> L[1] = 'c'`  # Makes the index at `[1]` a `'c'` instead of an `'h'`  
`>>> ''.join(L)`  
'scrubbery'  

### ByteArray - this converts the string to a hybrid of a list and bytes  

`>>> B = bytearray(b'spam')`  
`>>> B.extend(b'eggs')` # extend() function adds on to the original `'spam'` object  
`>>> B`  
`bytearray(b'spameggs')` # We're left with 'spameggs' after the extend function.  
`>>> B.decode()` # Using the decode() function it then decodes it and gives us the 'spameggs' string  
`'spameggs'`  

Understanding bytes, mutable lists, and Unicode more will help in fully grasping bytearrays  

## Type-specific methods  

Type-specific methods are attached to and act upon a specific object, which is triggered with a call expression.  

### String methods `find` & `replace`  

`>>> S = 'Spam'`  
`>>> S.find('pa')`  
`1`  
`>>> S`  
`'Spam'`  
`>>> S.replace('pa', 'XYZ')`  
`'SXYZm'`  
`>>> S`  
`'Spam'`  

We are not changing the original string, but creating a new string from the results- because strings are immutable.  

### Split  

`>>> line = 'aaa,bbb,ccccc,dd'`  
`>>> line.split(',')`  
`['aaa', 'bbb', 'ccccc', 'dd']`  

### Upper  

`>>> S = 'Spam'`  
`>>> S.upper()`  
'SPAM'  

### Is alpha (A - Z), is digit (1 - 0)  ~ Content test

`>>> S.isalpha()`  # tests the content to see if it's alpha characters  
`True`  

`>>> S = '1'`  
`>>> S.isdigit()` # test the content to see if it's a number
`True`  
`>>> S.isalpha()`  
`False`  

### rstrip  - strips trailing characters from a string

`>>> line = 'aaa,bbb,ccccc,dd\n'`  
`>>> line.rstrip()`  # () empty parenthases defaults to whitespaces  
`'aaa,bbb,ccccc,dd'`  
`>>> line.rstrip().split(',')`  # Combination of rstrip() and split()
`['aaa', 'bbb', 'ccccc', 'dd']`  

### Format - strings also support an advanced substitution operation known as formatting. It's available as both an expression and a method call. Formatting is rich with features  

`>>> '%s, eggs, and %s' % ('spam', 'SPAM!')` # Formatting expression (all)  
`'spam, eggs, and SPAM!'`  

`>>> '{0}, eggs, and {1}'.format('spam', 'SPAM!')`  
`'spam, eggs, and SPAM!'`  

`>>> '{}, eggs, and {}'.format('spam', 'SPAM!')`  
`'spam, eggs, and SPAM!'`  

`>>> '{:,.2f}'.format(296999.2567)` # Separators, decimal digits  
`269,999.26`  
`>>> '%.2f | %+05d' % (3.14159, -42)` # Digits, padding, signs  
`'3.14 | -0042'`  

## dir - using the built-in dir function on a string lists the available method calls you can do on the string. Can also be used on different object types  

`>>> dir(S)`  
`['__add__', '__class__', '__contains__', '__delattr__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__getitem__', '__getnewargs__', '__gt__', '__hash__', '__init__', '__init_subclass__', '__iter__', '__le__', '__len__', '__lt__', '__mod__', '__mul__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__rmod__', '__rmul__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', 'capitalize', 'casefold', 'center', 'count', 'encode', 'endswith', 'expandtabs', 'find', 'format', 'format_map', 'index', 'isalnum', 'isalpha', 'isascii', 'isdecimal', 'isdigit', 'isidentifier', 'islower', 'isnumeric', 'isprintable', 'isspace', 'istitle', 'isupper', 'join', 'ljust', 'lower', 'lstrip', 'maketrans', 'partition', 'removeprefix', 'removesuffix', 'replace', 'rfind', 'rindex', 'rjust', 'rpartition', 'rsplit', 'rstrip', 'split', 'splitlines', 'startswith', 'strip', 'swapcase', 'title', 'translate', 'upper', 'zfill']`  

`>>> S + 'Ni!'`  
`'spamNi!'`  

`>>> S.__add__('Ni!')`  
`'spamNi'`  

## help - using dir and then passing one of the methods to the `help` built-in function will ask what it does and return a reply of what it does  

`>>> help(S.replace)`  
`Help on built-in function replace:

replace(old, new, count=-1, /) method of builtins.str instance
    Return a copy with all occurrences of substring old replaced by new.
    
      count
        Maximum number of occurrences to replace.
        -1 (the default value) means replace all occurrences.
    
    If the optional argument count is given, only the first count occurrences are
    replaced.`  


