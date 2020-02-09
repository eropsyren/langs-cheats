## Numbers

* The / operator always returns a float
* The // does integer division
* The ** operator calculates powers. For example  2 ** 3 is 8
* In interactive mode _ stores the last printed expression

## Strings

* " or ' can be both used for string literals
* use print() to print a string
* with """ or ''' a string can span multiple lines
* + concatenates strings
* * repeats strings
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
