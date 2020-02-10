## Numbers

* The / operator always returns a float
* The // does integer division
* The ** operator calculates powers. For example  2 ** 3 is 8
* In interactive mode _ stores the last printed expression

## Strings

* " or ' can be both used for string literals
* use print() to print a string
* with """ or ''' a string can span multiple lines
* \+ concatenates strings
* \* repeats strings
* two or more string literals next to each other are concatenated
* strings are indexed, starting from 0, using [index]
* negative indices start from the bottom, using [#index]
* slicing allowsyou to get substrings, using [i:j]
* i is included
* j is excluded
* i defaults to 0
* j defaults to the length of the string
* out of range slice indices are handled gracefully
* strings are immutable
* len(s) returns the length of the string s

## Lists

* [1, 2, 3, 4] is a list
* like strings, they can be indexed and sliced
* slice operations always return a new list
* lists are mutable
* l.append(3) appends 3 to l
* assignment to slices can even change the list size
* len(l) returns the length of the list
* lists can be nested

## First steps

* fibonacci
```python
a, b = 0, 1
while a < 10:
	print(a)
	a, b = b, a + b
```
* any non 0 value is considered to be true
* a sequence is true if it's length is not zero

* If
```python
if x < 0:
	x = 0
elif x == 0:
	print('zero')
elif x == 1:
	print('one')
else:
	print('more')
```
## For
```python
l = [1, 2, 3]
for n in l:
	print(n)
```
* code that modifies a collection while iterating over is tricky. Instead loop
   over a copy of the collection, or create a new one
* the range() function is  useful to iterate over a sequence of numbers
* range(5) generates a list of numbers, from 0 to 4
* range(5, 10) generates [5, 6, 7, 8, 9]
* range(0, 10, 3) generates [0, 3, 6, 9]
* to iterate over the indices of a sequence l, range(len(l)) can be used
* the object returned from range() is not strictly a list, but it behaves like
   one. These objects are called iterables
* list(range(4)) gets a list from a range

## break, continue and else on Loops

* loops can have an else clause, which is executed once the loop has reaches
   exhaustion, but not when the loop is terminated by a break statement
* the continue statement skips to the next iteration of the loop

## pass Statement

* pass does nothing
* can be used when a statement is required syntactically but the program
   requires no action
* can be used as placeholder when working on new code

## Functions

* defining a fibonacci function
```python
def fib(n):
	"""Print a Fibonacci series up to n."""
	a, b = 0, 1
	while a < n:
		print (a, end=' ')
		a, b = b, a + b
	print()
```
* the keyword def introduces a new function definition
* the first statement can be a string literal, which is used as documentation
* arguments are passed using call by value, where the value is always an
  object reference
* functions can be assigned to variables
* the return statement is used to return a value from a function

## More on Defining Functions

* variadic functions can be defined
* a default value can be specified for one or more arguments
```python
def ask_ok(prompt, retries=4, reminder='Please try again!')
	while True:
		ok = input(prompt)
		if ok in ('y', 'ye', 'yes'):
			return True
		if ok in ('n', 'no', 'nop', 'nope'):
			return False
		retries = retries - 1
		if retries < 0:
			raise ValueError('invalid response')
		print(reminder)
```
* the in keyword tests whether or not a sequence contains a value
* the default values are evaluated at the point of function definition in the
  defining scope
* the default value is evauated only once, so object references are shared
* functions can be called using arg=value, like this
```python
parrot('a thousand', action='VOOOOM', voltage=1000000)
```
* in a function call, keyword arguments must follow positional arguments
* keyword arguments order is irrelevant
* no argument may receive a value more than once
* when a final formal parameter of the form **name is present, it receives
  a dictionary containing all keyword arguments except for those corresponding
  to a formal parameter
* this may be combined with a formal parameter of the form *name which receives
  a tuple containing the positional arguments beyond the formal parameter list
* *name must occour before **name
* is good practice to restrict the way arguments can be passed as follows
```python
def f(pos1, pos2, /, pos_or_keyword, *, keyword1, keyword2):
```
* positional only parameters are placed before a /
* parameters following / may be positional-or-keyword or keyword-only
* to mark paramters keyword-only place a * in the argument list just before the
  first keyword-only parameter
* the names of positional-only parameters can be used in **name without 
  ambiguity
* for an API, use positional-only parameters to prevent breaking API changes
  if the parameter's name is modified in the future
* to specify that a function can be called with an arbitrary number of
  arguments use *args and they will be wrapped into a tuple
```python
def write_multiple_items(file, separator, *args):
	file.write(separator.join(args))
```
* any formal parameter that occurs after the *args parameter is a keyword-only
  parameter
* sometimes the parameters are in a list or tuple and need to be unpacked
```python
args = [3, 6]
list(range(*args))
```
* in the same fashion, dictionaries can deliver keyword arguments with the **
  operator

### Lambda Expressions

* use the lambda keyword to create small anonymous fucntions
* lambda functions can be used whenever a function object is required
* lambda functions can reference variables from the containing scope
```python
def make_incrementor(n):
	return lambda x: x + n

f = make_incrementor(42)
f(0)	# is 42
f(1)	# is 43
```
### Documentation Strings

* the first line should always be a short and concise summary of the object's
  purpose
* don't state the object name and type since these should be clear
* should begin with a capital letter and end with a period
* if there are more lines, the line following the first, should be blank,
  visually separating the summary from the description

### Function annotations

* annotations add optional metadata
* are stored in the __annotations__ attribute of the function as a dictionary
* parameter annotations are defined by a colon after the parameter name,
  followed by an expression evaluating to the value of the annotation
* Return annotation are defined with ->, followed by an expression, between the
  parameter list and the colon ending the def statement
* an example
```python
def f(ham: str, eggs: str = 'eggs') -> str:
	print("Annotations: ", f.__annotations__)
	print("Arguments: ", ham, eggs)
	return ham + ' and ' + eggs
```
## Coding style

* use 4 space indentations and no tabs
* wrap lines to not excede 79 characters
* use blank lines to separate functions and classes and larger bloks of code
  inside functions
* put comments on a line of their own, when possible
* use docstrings
* use spaces around operators and after a comma
* name functions and classes consistently
* use UpperCamelCase for classes
* use snake_case for functions and methods
* always use self as the name of the first method argument
* more on [PEP 8](https://www.python.org/dev/peps/pep-0008/)

# Data Structures

## Lists

* `list.append(x)` adds an item to the end of the list
* `list.extend(iterable)` extends the list by appending all the items form
  the iterable
* `list.insert(i, x)` inserts x at the given position
* `list.remove(x)` removes the first item from the list whose value is equal to
  x
* `list.pop(i)` removes the item at the given position. If no argument is
  passed, it removes the last element of the list
* `list.clear()` removes all itmes
* `list.index(x, start, end)` returns zero-based index of the first item in the
  list that is equal to x. The arguments start and end are optional and are
  used to limit the search to a particular sublist of the list. The returned 
  index is computed relative to the beginning of the list
* `list.count(x)` return the number of times x appears in the list
* `list.sort(key=None, reverse=False)` sorts the items of the list in place
* `list.reverse()` reverses the list in place
* `list.copy()` returns a shallow copy of the list
* all methods that modify the list return None. This is a design principle for
  all mutable data structures in Python

### Using Lists as Stacks

* to add an item to the top of the stack, use `append()`
* to retrieve an item from the top use `pop()`

### Using Lists as Queues

* lists are not efficient for this purpose
* appends and pops are fast
* inserts and pops at the beginning of a list is slow
* to implement a queue use `collections.deque` which was designed to have fast
  appends and pops from both ends

### List Comprehensions

* are a concise way to create lists
* a list of sqaures
```python
squares = list(map(lambda x: x**2, range(10)))
```
* or
```python
squares = [x**2 for x in range(10)]
```
* a list comprehension contains an expression followed by a for clause, then
  zero or more for or if clauses. The result will be a new list resulting from
  evaluating the expression in the context of the for and if clauses that
  follows
* for example
```python
[(x, y) for x in [1, 2, 3] for y in [3, 1, 4] if x != y]
# is [(1, 3), (1, 4), (2, 3), (2, 1), (2, 4), (3, 1), (3, 4)]
```
* mapping
```python
[x*2 for x in vec]
```
* filtering
```python
[x for x in vect if x >= 0]
```
* list comprehensions can contain complex expressions and nested functions

### Nested list comprehensions

* The initial expression in a list comprehension can be any arbitrary
  expression, including another list comprehension
```python
matrix = [
	[1, 2, 3, 4],
	[5, 6, 7, 8],
	[9, 10, 11, 12],
]

[[row[i] for row in matrix] for i in range(4)]
# is [[1, 5, 9], [2, 6, 10], [3, 7, 11], 4, 8, 12]]
```
* in the real world, prefer built in functions to complex flow statements
* the following has the same result of the previous code
```python
list(zip(*matrix))
```

## The `del` statement

* the del statement removes an item from a list given its index instead of the
  value
```python
del a[0]
```
* dal can be used to remove slices
* del can be used to delete variables

## Tuples and Sequences

* lists and strings are examples of sequence data types
* another sequence data type is the tuple
* a tuple is a number of values separated by commas
```python
t = 12345, 54321, `hell0!`
```
* tuples may be nested
* it is not possible to assign to the individual items of a tuple
* tuples are immutable
* tuples usually contain a heterogeneous sequence of elements
* lists are mutable and are usually omogeneous
* `()` this is an empty tuple
* `t = 'hello',` is a tuple with one item
* tuples, like any other sequence, can be unpacked
```python
x, y, z = t
```
* sequence unpacking requires that there are as many variables on the left side
  as there are elements in the sequence
* multiple assignment is a combination of tuple packing and unpacking

## Sets

* a set is an unordered collection with no duplicate elements
* sets support union `|`, intersection `&`, difference `-`, and symmetric 
  difference `^`
* `set()` or `{` can be used to create sets
* `{}` this creates an empty dictionary
```python
basket = {`apple`, `orange`, `apple`, `pear`, `orange`, `banana`}
# basket is {`orange`, `banana`, `pear`, `apple`}
`orange` in basket
# true
`crabgrass` in basaket
# false
```
* set comprehensions are supported

## Dictionaries

* dictionaries are indexed by keys
* keys can be of any immutable type
* `{}` is the empty dictionary
* placing a comma separated list of key: vlaue pairs within curly braces adds
  initial pairs to a dictionary
* a pair can be deleted with `del`
* `list(d)` on a dictionary returns all keys in the dictionary, in insertion
  order
* to check if a key is in the dictionary use `in`
* `dict()` builds a dictionary from a sequence of key: value pairs
* comprehensions can be used
```python
{x : x**2 for x in (2, 4, 6)}
# {2: 4, 4: 16, 6: 36}
```
* when keys are strings, keyword arguments can be used with `dict()`

## Looping Techniques

* `items()` methods gets a sequence of key: value pairs of a dictionary
* when looping through a sequence, the position index and the corresponding
  value can be retrieved at the same time using the `enumerate()` function
* to loop over two or more sequences at the same time, the entries can be
  paired with the `zip()` function
* to loop in reverse, use the `reverse()` function
* to loop over a sequence in sorted order, use the `sorted()` function
* when looping over a list, don't modify it; create a new one

## More on Conditions

* conditions can contain any operator
* `in` and `not in` check if an element occour in a sequence
* `is` and `is not` compare whether two objects are really the same
* comparisons may be combined with `and`, `or`
* a comparison may be negated with `not`
* `and` and `or` short circuit
* when not used as a Boolean, the return value of a short-circuit operator is
  the last evaluated argument

## Comparing Sequences and Other Types

* sequence objects may be compared to other objects with the same sequence type
* this comparison uses lexicographical ordering
* if two items to be compared are themselves sequences of the same type, the
  lexicographical comparison is carried out recursively

# Modules

* a module is a file containing definitions and statements
* definitions from a module can be imported into other modules or into the main
  module
* the file name is the module name with a .py at the end
* `import` is use to import a module
* `import` does not enter the names defined in a module directly
* `import module` only enters the name `module`
* using the module name, you can access the names defined in it with the `.`
  operator

## More on Modules

* a module can contain also executable statements
* these statements are intended to initialize the module
* these are executed only the first time that the module name is encountered
  in an import statement
* each module has it's private symbol table
* you can access and modify a module's global variables
* modules can import other modules
* usually all import statements are at the top of the file
* `from module import name1, name2` directly imports name1 and name2 from
  module
* this does not introduce the module name
* `from module import *` imports all names in the module, except those
  beginning with _
* the latter form of import, is not recommended
* if the module name is followed by `as`, then the name following `as` is bound
  directly to the imported module
* this can be used also with `from`
* to run a module use `pthon module.py <args>`
* the variable `__name__` in the module will have value `"__main__"` when the 
  module is executed

### The Module Search Path

* when a module is imported, the interpreter first searches for a built in
  module
* it then searches for a file with the module name, followed by .py, in a list
  of directories given by the variable `sys.path`
* `sys.path` is initialized from the following locations
* the directory containing the script
* `PYTHONPATH`, like `PATH`
* the installation dependent default

### "Compiled" Python files

* to speed up module loading, Python caches the compiled version of each module
  in the `__pycahce__` directory under the name `module.version.pyc`

## Standard Modules

* Python comes with a library of standard modules
* standard modules are described [here](https://docs.python.org/3/library/index.html)

## The `dir()` Function

* `dir(module)` is used to find out which names a module defines
* `dir()` lists all currently defined names
* `dir()` does not list built-in names
* they are defined in the standard module `builtins`

## Packages

* a package is a collection of modules
* packages are a way of structuring Python's module namespace by using dotted
  module names
* the module name `A.B` designates a submodule named `B` in a package named `A`
* the use of dotted module names saves the authors of multi module packages
  from having to worry about each other's module names
* the file `__init__.py` is required to make Python treat directories
  containing the file as packages
* `__init__.py` can be an empty file, but it can also execute initialization
  code
* users of a package can import individual modules from the package
```python
import sound.effects.echo
```
* the imported module must be referenced with its full name
* the `from` keyword can also be used to make only the submodule available
```python
from sound.effects import echo
```
* `from` can be used to import single functions or variables

### Intra-package References

* when packages are structured into subpackages you can use absolute imports to
  refer to submodules of siblings packages
* relative imports can also be used with `..` and `.`

### Packages in Multiple Directories

* packages support a special attribute called `__path__`
* this is a list of the names of the directory holding the package's
  `__init__.py` before the code in that file is executed
* this variable can be modified, affecting future searches for modules and
  subpackages contained in the package
