# integer, float, string
```int, float, str```

# useful functions and methods for lists.
<pre>
max(list): Returns the list item with the maximum value
min(list): Returns the list item with minimum value
len(list): Return the length of a list
sum(list): Return the sum of all elements in a list

print(min(1, 2, 3, 4, 0, 2, 1))
print(max([1, 4, 9, 2, 5, 6, 8]))
print(sum([1, 2, 3, 4, 5]))

nums = [55, 44, 33, 22, 11]

if all([i > 5 for i in nums]):
   print("All larger than 5")

if any([i % 2 == 0 for i in nums]):
   print("At least one is even")

for v in enumerate(nums):
   print(v)
   
>>>
All larger than 5
At least one is even
(0, 55)
(1, 44)
(2, 33)
(3, 22)
(4, 11)
>>>

</pre>

# list methods
<pre>
list.count(obj): Returns a count of how many times an item occurs in a list
list.remove(obj): Removes an object from a list
list.reverse(): Reverses objects in a list
list.append(item)
list.insert(index, item)
</pre>

# try-with-resources
<pre>
with open("filename.txt") as f:
   print(f.read())
</pre>

# define a list, dictionary, tuple
<pre>
# list
list = ["one", "two"]
 
# dictionary 
dict = {1:"one", 2:"two"}
 
# tuple 
tp = ("one", "two")
</pre>

# set
<pre>
num_set = {1, 2, 3, 4, 5}
word_set = set(["spam", "eggs", "sausage"])
Instead of using append to add to a set, use add.
The method remove removes a specific element from a set; pop removes an arbitrary element.

To create an empty set, you must use set(), as {} creates an empty dictionary.
The union operator | combines two sets to form a new one containing items in either.
The intersection operator & gets items only in both.
The difference operator - gets items in the first set but not in the second.
The symmetric difference operator ^ gets items in either set, but not both.

first = {1, 2, 3, 4, 5, 6}
second = {4, 5, 6, 7, 8, 9}

print(first | second)
print(first & second)
print(first - second)
print(second - first)
print(first ^ second)

>>>
{1, 2, 3, 4, 5, 6, 7, 8, 9}
{4, 5, 6}
{1, 2, 3}
{8, 9, 7}
{1, 2, 3, 7, 8, 9}
>>>

</pre>

# list Slicing
<pre>
squares = [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
print(squares[2:6]) # [4, 9, 16, 25]

If the first number in a slice is omitted, it is taken to be the start of the list.
If the second number is omitted, it is taken to be the end.

squares = [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
print(squares[:7]) # [0, 1, 4, 9, 16, 25, 36]
print(squares[7:]) # [49, 64, 81]

Slices with 3 arguments: start, end, step
print(squares[2:8:3]) # [4, 25] 
[2:8:3] will include elements starting from the 2nd index up to the 8th with a step of 3.

Slices with negative argument. The negative argument will start from the end
squares = [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
print(squares[1:-1]) # [1, 4, 9, 16, 25, 36, 49, 64]

If a negative value is used for the step, the slice is done backwards.
Using [::-1] as a slice is a common and idiomatic way to reverse a list.
</pre>

# list comprehension
<pre>
cubes = [i**3 for i in range(5)]
[0, 1, 8, 27, 64]


Trying to create a list in a very extensive range will result in a MemoryError.
even = [2*i for i in range(10**100)]
MemoryError
</pre>

# string formatting
<pre>
nums = [4, 5, 6]
msg = "Numbers: {0} {1} {2}". format(nums[0], nums[1], nums[2])
print(msg)

# string formatting with names arguments
a = "{x}, {y}".format(x=5, y=12)
print(a)
</pre>

# string functions

<pre>
print(", ".join(["spam", "eggs", "ham"]))
#prints "spam, eggs, ham"

print("Hello ME".replace("ME", "world"))
#prints "Hello world"

print("This is a sentence.".startswith("This"))
# prints "True"

print("This is a sentence.".endswith("sentence."))
# prints "True"

print("This is a sentence.".upper())
# prints "THIS IS A SENTENCE."

print("AN ALL CAPS SENTENCE".lower())
#prints "an all caps sentence"

print("spam, eggs, ham".split(", "))
#prints "['spam', 'eggs', 'ham']"
</pre>

# functional programming
<pre>
# lamdas
(lambda x: x * x)(8)

nums = [4, 5, 6]

# map takes as arguments a lambda and a list
result = list(map(lambda x: x + 5, nums))

# filter takes as a argument a lambda (predicate) and a list
result = list(filter(lambda x: x % 2 == 0, nums))

# generators
yield

# decorators
def decor(func):
  def wrap():
    print("============")
    func()
    print("============")
  return wrap

def print_text():
  print("Hello world!")

decorated = decor(print_text)
decorated()

@decor
def print_text():
  print("Hello world!")


</pre>

# itertools
<pre>
The function count counts up infinitely from a value.
The function cycle infinitely iterates through an iterable (for instance a list or string).
The function repeat repeats an object, either infinitely or a specific number of 
from itertools import count

for i in count(3):
  print(i)
  if i >=5:
    break

>>>
3
4
5
>>>

takewhile - takes items from an iterable while a predicate function remains true;
chain - combines several iterables into one long one;
accumulate - returns a running total of values in an iterable.

from itertools import accumulate, takewhile

nums = list(accumulate(range(8)))
print(nums)
print(list(takewhile(lambda x: x<= 6, nums)))

>>>
[0, 1, 3, 6, 10, 15, 21, 28]
[0, 1, 3, 6]
>>>

There are also several combinatoric functions in itertool, such as product and permutation.
These are used when you want to accomplish a task with all possible combinations of some items.
from itertools import product, permutations

letters = ("A", "B")
print(list(product(letters, range(2))))
print(list(permutations(letters))) 
>>>
[('A', 0), ('A', 1), ('B', 0), ('B', 1)]
[('A', 'B'), ('B', 'A')]
>>>

</pre>

# magic methods
<pre>
Magic Methods

More magic methods for common operators:
__sub__ for -
__mul__ for *
__truediv__ for /
__floordiv__ for //
__mod__ for %
__pow__ for **
__and__ for &
__xor__ for ^
__or__ for |

The expression x + y is translated into x.__add__(y).
However, if x hasn't implemented __add__, and x and y are of different types, then y.__radd__(x) is called.
There are equivalent r methods for all magic methods just mentioned.
</pre>