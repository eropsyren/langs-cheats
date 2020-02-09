# Numbers

* The / operator always returns a float
* The // does integer division
* The ** operator calculates powers. For example  2 ** 3 is 8
* In interactive mode _ stores the last printed expression

# Strings

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

# Lists

* [1, 2, 3, 4] is a list
* like strings, they can be indexed and sliced
* slice operations always return a new list
* lists are mutable
* l.append(3) appends 3 to l
* assignment to slices can even change the list size
* len(l) returns the length of the list
* lists can be nested

# First steps

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
# For
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

# break, continue and else on Loops

* loops can have an else clause, which is executed once the loop has reaches
   exhaustion, but not when the loop is terminated by a break statement
* the continue statement skips to the next iteration of the loop

# pass Statement

* pass does nothing
* can be used when a statement is required syntactically but the program
   requires no action
* can be used as placeholder when working on new code

# Functions

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

# More on Defining Functions

