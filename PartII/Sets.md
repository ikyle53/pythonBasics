# Sets  

`Sets` are an unordered collection of unique and immutable objects that supports operations corresponding to mathematical set theory.  

- An item only appears once in a set. There are no duplicates, even if duplicates are made
- Since lists are objects they also share some behavior with objects such as lists and dictionaries
- Sets are iterable, can grow and shrink on demand, and may contain a variety of object types
- Sets are unordered and do not map keys to values, which makes them niether sequenced or mapping types. They get their own category
- Sets are mathematical in nature  

To make a set object I pass in a sequence or other iterble to the built-in `set` function:  
`>>> x = set('abcde')`  
`>>> y = set('bdxyz')`  
`>>> x`  
`{'e', 'b', 'a', 'd', 'c'}`  

## Set Difference  

Set difference resolves differences between both sets and prints the results of what is not included in the set being compared (y).  

`>>> x - y`  
`{'e', 'a', 'c'}` # e, a, and c are not contained in `y`  

`>>> y - x`  
`{'x', 'y', 'z'}` # x, y, and z are not contained in `x`  

## Set Union  

Set union combines both sets and rids of any duplicates:  

`>>> x | y`  
`{'e', 'x', 'b', 'a', 'd', 'z', 'y', 'c'}`  

## Set Intersection  

Intersection is comparing both sets to see which items are the same.  

`>>> x & y`  
`{'d', 'b'}` # d and b in this case are contained in both `x` & `y`  

## Symmetric Difference  

Symmetric difference gives a result of ALL differences in both sets.  

`>>> x ^ y`  
`{'a', 'x', 'e', 'z', 'y', 'c'}` #These items are the items that are not contained in one or the other  

## Superset, Subset  

`>>> x > y, x < y`  
`(False, False)`  

Superset is a set that contains all of another set plus some more. Example:  
(`>>> x > y`)  
`>>> x = set('abc')`  
`>>> y = set('abcdefg')` #`y` is a superset of `x` because it contains the entirety of `x` (abc) as well as more characters.  

Subset is the opposite. Example:  
(`>>> x < y`)  
`>>> x = set('abc')` #`y` contains all of `x` and thus `x` is a subset of `y`. They can be said to be equal since they contain the same characters.  
`>>> y = set('abcdefg')`  

## Membership test  

This expression works on all other collection types as well (sometimes called search).  
`>>> 'e' in x`  
`True`  
`>>> 'a' in y`  
`False`  

`>>> 'e' in 'Arisen', 22 in [11, 22, 33]`  
`(True, True)`  

## Methods for sets  

Intersection:  

`>>> z = x.intersection(y)`  
`>>> z`  
`{'d', 'b'}`  

Add:  

`>>> z.add('SPAM')`  
`>>> z`  
`{'SPAM', 'd', 'b'}`  

Update:  

`>>> z.update(set(['X', 'Y']))`  
`>>> z`  
`{'d', 'Y', 'b', 'SPAM', 'X'}`  #Merge: in-place union  

Remove:  

`>>> z.remove('b')`  
`>>> z`  
`{'d', 'Y', 'SPAM', 'X'}`  

> NOTE: Sets don't support sequence operations like indexing and slicing since they aren't ordered.  

For Loop:  

`>>> for item in set('abc'): print(item * 3)`  
`aaa`  
`bbb`  
`ccc`  

Set expressions generally require two sets, but sets can often work with any iterable type as well:  

`>>> S = set([1, 2, 3])`  
`>>> S | set([3, 4])`  
`{1, 2, 3, 4}`  
`>>> S | ([3, 4])` #Gives a type error  

`>>> S.union([3, 4])`  
`{1, 2, 3, 4}`  
`>>> S.intersection((1, 3, 5))`  
`{1, 3}`  
`>>> S.issubset(range(-5, 5))`  

## Set literals and comprehensions  

The following are equivalent when creating a set literal:  

`>>> set([1, 2, 3, 4])` #The usual way to create a set  
`{1, 2, 3, 4}`  
`>>> {1, 2, 3, 4}` #Set literal  
`{1, 2, 3, 4}`  

This basically looks like a valueless dictionary. Dictionaries are key : value pairs.  

> NOTE: `set()` is still required for creating empty sets and to build sets from existing iterable objects.  

`>>> K1 = {10, 11, 12, 13}` #New set  
`>>> K1 - {10, 11, 12, 13}` #Empties the set  
`set()` #Returns an empty set  
`>>> K1`  
`{10, 11, 12, 13}` #Doesn't erase all the items though  
`>>> type({})`  
`<class 'dict'>`  
`>>> type(K1)`  
`<class 'set'>`  

`>>> K = set()`  
`>>> K.add('MyList')` #Adding an item to an empty list  
`>>> K`  
`{'MyList'}`  

Set literals also support the same methods with general iterable operands that expressions do not:  

Union:  
`>>> {1, 2, 3} | {3, 4}` #Two sets unionized are okay  
`{1, 2, 3, 4}`  

`>>> {1, 2, 3} | [3, 4]` #Gives a type error since I want to unionize a list to a set using an expression  

`>>> {1, 2, 3}.union([3, 4])`  
`{1, 2, 3, 4}` #Methods work however  

`>>> {1, 2, 3}.union({3, 4})`  
`{1, 2, 3, 4}`  

`>>> {1, 2, 3}.union(set([3, 4]))`  
`{1, 2, 3, 4}`  

`>>> {1, 2, 3}.intersection((1, 3, 5))`  
`{1, 3}`  

`>>> {1, 2, 3}.issubset(range(-5, 5))`  
`True`  

## Immutable constraints and frozen sets  

Sets can only contain immutable (hashable) object types. That being said, lists and dictionaries can't be embedded in sets, but tuples can if I need to store compound values.  

`>>> K`  
`{5.55}`  
`>>> K.add([1, 2, 3])` #Adding a list gives a type error  

`>>> K.add({'a':1})` #Adding a dictionary gives a type error  

`>>> S.add((1, 2, 3))`  
`>>> S`  
`{1, 2, 3, (1, 2, 3)}`  

`>>> K | {(4, 5, 6), (1, 2, 3)}` #Unionizing using the operand with a set of tuples  
`{(1, 2, 3), 5.55, (4, 5, 6)}`  

`>>> (1, 2, 3) in K` #Membership is also able to work with a tuple and sets  
`False`  

> Tuple importance: Tuples being used in sets might represent dates, records, IP addresses, and so on. Works great since they're immutable.  
