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
`Help on built-in function replace:`  

`replace(old, new, count=-1, /) method of builtins.str instance`  
    `Return a copy with all occurrences of substring old replaced by new.`  
      `count`  
        `Maximum number of occurrences to replace.`  
        `-1 (the default value) means replace all occurrences.`  
    `If the optional argument count is given, only the first count occurrences are
    replaced.`  

- `help` ships with python and is known as PyDoc, which extracts documentation from objects.  
- `dir` and `help` can accept `objects` or the name of a data type (`str`, `list`, `dict`).  
- This is a good way to get information about a specific method being used on your object.  

## String escape notations  

Strings have escape notations in the format of hexadecimal escape notations. `\xNN`  
`>>> S = 'A\nB\tC'`   # \n means end-of-line and \t means tab  
`>>> len(S)`  
`5` # The `\` is ignored as part of the length method since it's an escape notation  

`>>> ord('\n')` # \n is one character coded as a decimal value 10  
`10`  

`>>> S = 'A\0B\0C'`  # \0 is a binary zero byte and will not terminate the string  
`>>> len(S)`  
`5`  
`>>> S`  
`'A\x00B\x00C'` # non-printables are displayed as \xNN hex escapes  

Python strings can use single or double quotes. Singles are preferred, but you can do multi-line string literals with triple quotes:  

`>>> msg = """`  
`aaaaaaaaa`  
`bbb'''bbbbbbbbbb""bbbbbbbbb'bbbbbb`  
`ccccccccccccc`  
`"""`  
`>>> msg`  
`'\naaaaaaaaa\nbbb'''bbbbbbbbbb""bbbbbbbbb'bbbbbb\nccccccccccccc'`  

### Unicode strings  

`>>> 'sp\xc4m'`  
`'spÄm'`  
`>>> b'a\x01c'` # b stands for byte, which makes this a byte string, which is byte-based data  
`b'a\x01c'`  

`>>> u'sp\u00c4m` # u stands for unicode so this makes it a unicode string type
`'spÄm'`  

Strings handle both the 8-bit characters and the raw byte values.  
`>>> print u'sp\xc4m'`  
`'spÄm'`  
`>>> 'a\x01c'`  
`'a\x01c'`  
`>>> b'a\x01c'`  
`'a\x01c'`  

Non-Unicode strings are sequences of 8-bit bytes that print with ASCII characters when possible. Unicode strings are sequences of unicode code points- which identifies numbers with characters. This doens't always map out to single bytes when encoded to files or when stored in memory.  
`>>> 'spam'` # Characters may be 1, 2, or 4 bytes in memory  
`spam`  
`>>> 'spam'.encode('utf8')` # This encodes to 4 bytes in utf-8 in files  
`b'spam'`  
`>>> 'spam'.encode('utf16')` # This encodes to 10 bytes in utf-16  
`b'\xff\xfes\x00p\x00a\x00m\x00'`  

`>>> 'sp\xc4\u00c4\U000000c4m'`  
`'spÄÄÄm'`  

So, why are these important? Knowing unicode can allow you to embed code as code-point (numerical value that maps to a specific character) ordinal-value (ordered categories) integers in text strings.  

Byte code on the other hand uses `\x` hexadecimal escapes to embed the encoded form of text, not its actual code point values.  

`'\u00A3', '\u00A3'.encode('latin1'), b'\xA3'.decode('latin1')`  

Python `v2.X` allows normal and unicode strings to mix, whereas `v3.X` never allows normal and byte strings to mix without explicit conversion.  

> Unicode processing mostly comes down to trasnferring text data to and from files- the text is encoded to bytes when stored in a file, and then it's decoded into characters (code points) when it's read back into memory.  

Becuase of this model files are content-specific in `v3.X`.  

1. Text files - implement named encodings and accept and return `str` strings.

2. Binary files - deal in `bytes` strings for raw binary data.  

### Pattern matching with strings using `re`  

Note: none of the string object's own methods support pattern-based text processing. This is an advanced tool.  

`>>> import re`  
`>>> match = re.match('Hello[\t]*(.*)world', 'Hello  Python world')`  
`>>> match.group(1)`  
`'Python '`  

The above example searches for a substring that begins with the word `"Hello"` followed by zero or more spaces or tabs (`[\t]`) followed by arbitrary characters to be saved as a matched group (`(.*)`), terminated by the word `"world"`.  

## Lists  

Lists are the most general sequence provided by python. They're positionally ordered collections of arbitrarily typed object (meaning it's not predefined) and it also has no limit to how long the list can be. Lists are also mutable so they can be modified in place by assignmnet to offsets as well as a variety of list method calls.  

`>>> L = [123, 'spam', 1.23]`  
`>>> len(L)`  
`3`  

Lists can be indexed, sliced, and so on just like strings:  
`>>> L[0]` #get an index  
`123`  
`>>> L[:-1]` #sliced the last index off  
`[123, 'spam']`  
`>>> L + [4, 5, 6]` #adds 4, 5, & 6 to the current list  
`[123, 'spam', 1.23, 4, 5, 6]`  
`>>> L * 2` #repeats the list twice  
`[123, 'spam', 1.23, 123, 'spam', 1.23]`  
`>>> L` #Lastly, the original object isn't changed  
`[123, 'spam', 1.23]`

> I am tempted to compare `list` to `array` in other languages. I see them as almost the same thing, but Python doesn't have the `type` constraints other languages do. I have a number, a string, and a floating-point number in my list above. Also, lists have no defined size so I can make it bigger or smaller on demand.  

`>>> L.append('NI')` #adds `'NI'` to the list  
`>>> L`  
`[123, 'spam', 1.23, 'NI']`  

`>>> L.pop(2)` #deletes the item at index 2  
`1.23`  
`>>> L`  
`[123, 'spam', 'NI']`  

There are a few more list methods that can do extra things like the one's above:  

1. `insert` - insert an item at a given postion
2. `remove` - remove a given item by its value
3. `extend` - adds multiple items at the end of the list  

There's also sorting methods for lists:  
`>>> M = ['bb', 'cc', 'aa']` #Created a list of letters  
`>>> M.sort()` #sorts the list by alphabetically  
`>>> M`  
`['aa', 'bb', 'cc']`  

Similarly, it can reverse sort:  
`>>> M.reverse()`  
`>>> M`  
`['cc', 'bb', 'aa']`  

Both modify the list directly.  

### Nesting  

Nesting in Python allows us to create a nest with as big of a depth as we choose with any types we want.  

#### Maxtrix  

`>>> M = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]` #A 'matrix' which is a list of 3 lists.  

`M` represents a 3x3 matrix in which we can accessin a variety of ways:  
`>>> M[1]` #Get row 2  
`[4, 5, 6]`  
`>>> M[1][2]` #Get row 2 and the index of 2 (from row 2)
`6`  

### Comprehensions  

Python includes an advanced operation known as a list comprehension expression. This operation can process my matrix and similar data structures like it.  

`>>> col2 = [row[1] for row in M]`  
`>>> col2`  
`[2, 5, 8]`  

Essentially if I stack the three lists I get a 3x3 grid matrix. I created `col2` that chooses 2, 5, and 8, which is the middle column of the matrix.  
`[[1, 2, 3],`  
`[4, 5, 6],`  
`[7, 8, 9]]`  

List comprehensions build a new list by running an expression on each item in a sequence, one at a time, from left to right. 1, 2, 3, 4, 5, 6, 7, 8, and 9 get put through the expression respectively and a new list is created based on the criteria. In this case I'm using row[1] and looping through M to get that item for the new list.  

We can make it a little more complex:  
`>>> [row[1] + 1 for row in M]`  
`[3, 6, 9]`  
`>>> [row[1] for row in M if row[1] % 2 == 0]` #This filters out odd numbers from the column we previously filtered for (2, 5, & 8). It adds an if clause that if it's divisible by 2 it can be added to the new list. Otherwise, it get's filtered out and not added to the new list.  
`[2, 8]`  

List comprehensions make new lists of results and can be used to to iterate over any iterable object.  
`>>> diag = [M[i][i] for i in [0, 1, 2]]` #This iterates through our M object and uses `i` as an iterater that takes on the values of 0, 1, and 2 after each succesfful iteration of a list. Bascially, `i` starts off at the value of 0 and iterates to find index `[0]` of row `[0]` of our `M` matrix I created earlier. Once the iteration successful it will then result in `1` for the first item of the new list. After the result it then takes on the value of 1 and iterates using that value. It goes through the second list (indexed as row[1]) and then iterates again to result in `5` using the index of that list of `[1]`. This repeats for `[2]` and I get the result below.  
`>>> diag`  
`[1, 5, 9]`  
`>>> doubles = [c * 2 for c in 'spam']` #Repeats each character twice in the string `'spam'`  
`>>> doubles`  
`['ss', 'pp', 'aa', 'mm']`  

These expressions can also be used to collect multiple values:  
`>>> list(range(4))`  
`[0, 1, 2, 3]`  
`>>> list(range(-6, 7, 2))`  #Creates a list that ranges from -6 to +6 (not including 7) that counts up by 2.  
`[-6, -4, -2, 0, 2, 4, 6]`  

`>>> [[x ** 2, x ** 3] for x in range(4)]` #This is an expression that creates a list of x to the power of 2 and 3. It then loops through the range set at 4; starting from 0 and ending on 3.  

Comprehensions can also be used to create generators:  
`>>> G = (sum(row) for row in M)` #Creates a generator of row sums  
`>>> next(G)`  
`6`  
`>>> next(G)`  
`15`  
`>>> next(G)`  
`24`  

`>>> list(map(sum, M))`  
`[6, 15, 24]`  

## Dictionaries  

In python dicationaries are not sequences. They are instead known as mappings. This means they are a collection of other objects. It stores these objects by keys with no left-to-right order.  

Dictionaries are mutable and can be changed on a whim.  

Dictionaries are written with curly braces `{ }` and consist of key value pairs `{key: value}`. These are then indexed.  

`>>> D = {'food': 'Spam', 'quantity': 4, 'color': 'red'}`  
`>>> D['food']` #Square brackets are used to target the value of a key.  
`Spam`  
`>>> D['quantity'] += 1`  
`>>> D`  
`{'food': 'Spam', 'quantity': 5, 'color': 'red'}` #quantity is now 5  

A dictionary can be formed one key at a time and add more key value pairs:  

`>>> D = {}` #I created an empty dictionary  
`>>> D['name'] = 'Kyle'` #I've now created a new key by assignment  
`>>> D['job'] = 'Software Developer'`  
`>>> D['age'] = 31`  
`>>> D`  
`{'age': 31, 'job': 'Software Developer', 'name': 'Kyle'}` #New dictionary!  
`>>> print(D['name'])`  
`Kyle`  

Two examples of creating a dictionary using keywords and zipping:  

### Keywords  

`>>> kyle1 = dict(name='Kyle', job='dev', age=31)`  
`>>> kyle1`  
`{'age': 31, 'name': 'Kyle', 'job': 'dev'}`  

### Zipping  

`>>> kyle2 = dict(zip(['name', 'job', 'age'], ['Kyle', 'dev', 31]))`  
`>>> kyle2`  
`{'job': 'dev', 'name': 'Kyle', 'age': 31}`  

### Nesting revisited  

`rec = {'name': {'first': 'Kyle', 'last': 'Honaker'}, 'jobs': ['dev', 'mgr'], 'age': 31}`  
`rec`  
`{'name': {'first': 'Kyle', 'last': 'Honaker'}, 'jobs': ['dev', 'mgr'], 'age': 31}`  
`rec['name']`  
`{'first': 'Kyle', 'last': 'Honaker'}`  
`rec['name']['last']`  
`'Honaker'`  
`rec['jobs']`  
`['dev', 'mgr']`  
`rec['jobs'][-1]`  
`'mgr'`  
`rec['jobs'].append('janitor')`  
`rec`  

### Dictionary methods  

`D = {'a': 1, 'b': 2, 'c': 3}`  
`D`  
`{'a': 1, 'b': 2, 'c': 3}`  
`D['e'] = 99` #Make a new key value pair  
`D`  
`{'a': 1, 'b': 2, 'c': 3, 'e': 99}`  
`D['f']`  #f doesn't exist and throws an error  
`Traceback (most recent call last):`  
  `File "<pyshell#25>", line 1, in <module>`  
   `D['f']`  
`KeyError: 'f'`  
`'f' in D` #This checks to see if f is in D ("if in" test)  
`False`  
`if not 'f' in D:`  #if f isn't in D we want it to print 'missing' using this if statement  
    `print('missing')`  
`missing`  

#### Get method  

`value = D.get('x', 0)`  
`value`  
`0`  
`value = D['x'] if 'x' in D else 0`  
`value`  
`0`  

#### Sorting key: for loops  

`D`  
`{'a': 1, 'b': 2, 'c': 3, 'e': 99}`  
`Ks = list(D.keys())`  
`Ks`  
`['a', 'b', 'c', 'e']`  

`for key in Ks:`  
    `print(key, '=>', D[key])`  
`a => 1`  
`b => 2`  
`c => 3`  
`e => 99`  

Another example using `sorted`:  

`for key in sorted(D):`  
    `print(key, '=>', D[key])`  
`a => 1`  
`b => 2`  
`c => 3`  
`e => 99`  

### For/while looping  

For loops typically work on sequenced objects as a sequence operation and on some objects that are not sequenced.  

`for c in 'spam':`  #`c` is our loop variable  
   `print(c.upper())`  #I call the loop variable to uppercase each printed string  

`S`  
`P`  
`A`  
`M`  

While loops are more general for looping. It's not limited to stepping across sequences, but it generally reuqires more code.  

`x = 4`  
`while x > 0:`  #if x is more than 0 it will continue to run  
    `print('spam!' * x)`  
    `x -= 1`  #the while loop subtracts 1 each loop till 4 reaches 0 and meets the end condition  

`spam!spam!spam!spam!`  
`spam!spam!spam!`  
`spam!spam!`  
`spam!`  

### Iteration and optimization  

An object in Python is iterable if it is either a physically stores sequence in memory, or an object that generates one item at a time in the context of an iteration operation- a sort of 'virtual' sequence. They will have the `iteration protocol` (responds to `iter` and `next`)  

`squares = [x ** 2 for x in [1, 2, 3, 4, 5]]` #A basic comprehension expression that squares a list of numbers  
`squares`  
`[1, 4, 9, 16, 25]`  

It can also be written using a `for` loop that appends a new result with each iteration:  
`squares = []`  
`for x in [1, 2, 3, 4, 5]:`  
    `squares.append(x ** 2)`  
`squares`  
`[1, 4, 9, 16, 25]`  

## Tuples  

Tuples are like a list that can't be changed, yet are sequenced. They are used to represent fixed collections items. They do support arbitrary types, arbitrary nesting, and sequence operations.  

`T = (1, 2, 3, 4)`  
`len(T)`  
`4`  
`T + (5, 6)`  
`(1, 2, 3, 4, 5, 6)`  #I can add to the Tuple, but I can't change any of the values.  
`T[0]`  
`1`  

`T.index(4)` #The index method can be used to find what value is assigned to which index  
`3`  #4 resides at the index of 3  
`T.count(4)` #The count method can also be used to determine how many times that value appears in the tuple.  
`1` #4 only occurs once  

I have to explicitly state for a new tuple object to be made if I want to change any of the values:  

`T = (2,) + T[1:]` #I assign T as 2 + the remainder of T including and after the index of 1 (slicing).  
`T`  
`(2, 2, 3, 4)` #The result is a new T object with 2 as the new value in the `[0]` index.  

> Side note - Parenthases enclosing a tuple can be ommitted. In contexts where commas don't really matter, the commas are what actually builds a tuple.  

`T = 'spam', 3.0, [11, 12, 13]`  #Tuples support different types as well  
`T[1]`  
`3.0`  
`T[2][1]`  #Nesting is also supported  
`12`  

> So why tuples? Tuples are just like list but are immutable, and that's the point. Immutability provides integrity to information that shouldn't be changed, such as days on a calendar. If only lists were used the list could be changed somewhere in the program unintentionally.  

## Files  

Files are a core type, but don't have a specific syntax provided for it. Instead files are called upon using the `open` function along with the file name.  

`f = open('data.txt', 'w')`  #`w` means write. We are writing a new file  
`f.write('Hello\n')`  #This writes the text `'Hello'` along with a new line  
`6`  
`f.write('world\n')`  
`6`  
`f.close()`  
`f = open('data.txt')`  #`'r'` means read is default if the operation is ommitted  
`text = f.read()`  
`text`  
`'Hello\nworld\n'`  
`print(text)`  
`Hello`  
`world`  
`text.split()`  
`['Hello', 'world']`  

### Binary bytes files  

Binary byte files represent content as a special `bytes` string and allow me to access file content unaltered. This is used for processing media, accessing data created by C programs.  

`import struct`  
`packed = struct.pack('>i4sh', 7, b'spam', 8)` #This creates a packed binary data  
`packed`  
`b'\x00\x00\x00\x07spam\x00\x08'`  
`file = open('data.bin', 'wb')` #I open the binary output file  
`file.write(packed)` #I then write the packed binary data  
`10`  
`file.close()`  

Reading binary data back:  

`data = open('data.bin', 'rb').read()` #This opens and reads the binary data file  
`data`  
`b'\x00\x00\x00\x07spam\x00\x08'` #These are the 10 bytes that are still unaltered  
`data[4:8]` #This is the bytes cliced in the middle  
`b'spam'`  
`list(data)`  #This list gives me a sequence of 8-bit bytes  
`[0, 0, 0, 7, 115, 112, 97, 109, 0, 8]`  
`struct.unpack('>i4sh', data)` #Lastly, I unpack the bytes data into an object again  
`(7, b'spam', 8)`  

### Unicode text files  

Text files are used to process all sorts of text-based data. In Python we have to ask "what kind", which leads us to the text's unicode encoding type.  
If I don't know the encoding type I can simply use Python's automatic encoding/decoding on reads:  

`S = 'sp\xc4m'` #Non-ASCII unicode text  
`S`  
`'spÄm'`  
`S[2]`  
`'Ä'`  
`file = open('unidata.txt', 'w', encoding='utf-8')`  #Write/encode UTF-8 text  
`file.write(S)` #4 Characters get written  
`4`  
`file.close()`  
`text = open('unidata.txt', encoding='utf-8').read()` #Read and decode the UTF-8 text  
`text`  
`'spÄm'`  
`len(text)`  
`4`  

If needed, I can also step into binary mode to see what's truly stored in the the file:  

`raw = open('unidata.txt', 'rb').read()` #This reads the raw encoded bytes  
`raw`  
`b'sp\xc3\x84m'` #It's actually 5 bytes in UTF-8  
`len(raw)`  
`5`  

## Sets (Not a core type, but could be)  

`X = set('spam')` #Makes a set out of a sequence  
`X`  
`{'m', 'a', 'p', 's'}`  
`Y = {'h', 'a', 'm'}` #Makes a set using set literals  
`X, Y`  
`({'m', 'a', 'p', 's'}, {'h', 'm', 'a'})` #Makes a tuple of the 2 sets  
`X & Y`  
`{'m', 'a'}`  #Intersects where the two sets have the same characters  
`X | Y`  
`{'h', 'm', 'p', 's', 'a'}` #This unifies the two sets without repeating characters  
`X - Y`  
`{'p', 's'}` #Creates the difference in both sets  
`X > Y` #Allows me to know if it's a superset  
`False`  

Sets are great for getting rid of duplicates, isolating differences, and performing equality tests without sorting (in iterable objects).  

`list(set([1, 2, 1, 3, 1]))` #Filters out duplicates  
`[1, 2, 3]`  
`set('spam') - set('ham')` #Finds differences in the collections  
`{'p', 's'}`  
`set('spam') == set('asmp')` #Equality test to see if they are the same, regardless of order  
`True`  

## Decimal numbers & fractions  

`1 / 3`  
`0.3333333333333333`  
`(2/3) + (1/2)`  
`1.1666666666666665`  
`import decimal`  
`d = decimal.Decimal('3.141')`  
`d + 1`  
`Decimal('4.141')`  
`decimal.getcontext().prec = 2`  
`decimal.Decimal('1.00') / decimal.Decimal('3.00')`  
`Decimal('0.33')`  
`from fractions import Fraction`  
`f = Fraction(2, 3)`  
`f + 1`  
`Fraction(5, 3)`  
`f + Fraction(1, 2)`  
`Fraction(7, 6)`  

## Booleans as well!  

`1 > 2, 1 < 2`  
`(False, True)`  
`bool('spam')`  
`True`  

## User-defined classes  

`class Worker:`  
    `def __init__(self, name, pay):` #Initializes when created  
        `self.name = name` #Self is the new object  
        `self.pay = pay`  
    `def lastName(self):`  
        `return self.name.split()[-1]` #This will split the name string on blanks/spaces and use the last name (-1)
    `def giveRaise(self, percent):`  
        `self.pay *= (1.0 + percent)` #This updates the pay in place


`kyle = Worker('Kyle Honaker', 50000)`  
`asaki = Worker('Asaki Honaker', 50000)`  
`kyle.lastName()`  
`'Honaker'`  
`asaki.lastName()`  
`'Honaker'`  
`asaki.giveRaise(.10)`  
`asaki.pay`  
`55000.00000000001`  
