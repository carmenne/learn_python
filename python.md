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

# define a class
<pre>
class Cat:
	def __init__(self, color, legs):
		self.color = color
		self.legs = legs

miau = Cat("black", 4)
tiau = Cat("yellow", 3)

print(miau.color)

Classes can also have class attributes, created by assigning variables within the body of the class. 
These can be accessed either from instances of the class, or the class itself.

class Dog:
    legs = 4

print(Dog.legs)

Trying to access an attribute of an instance that isn't defined causes an AttributeError. 
This also applies when you call an undefined method.
</pre>

# inheritance:
<pre>
class Animal: 
  def __init__(self, name, color):
    self.name = name
    self.color = color

class Cat(Animal):
  def purr(self):
    print("Purr...")
        
class Dog(Animal):
  def bark(self):
    print("Woof!")

fido = Dog("Fido", "brown")
print(fido.color)
fido.bark()

If a class inherits from another with the same attributes or methods, it overrides them.

The function super is a useful inheritance-related function that refers to the parent class. 
It can be used to find the method with a certain name in an object's superclass.

class A:
  def spam(self):
    print(1)

class B(A):
  def spam(self):
    print(2)
    super().spam()
            
B().spam()

>>>
2
1    
>>> 

</pre>

# methods
<pre>
Classes can have other methods defined to add functionality to them.
Remember, that all methods must have self as their first parameter.
These methods are accessed using the same dot syntax as attributes.
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

# data hiding
<pre>
Weakly private methods and attributes have a single underscore at the beginning.
This signals that they are private, and shouldn't be used by external code. However, it is mostly only a convention, 
and does not stop external code from accessing them.
Its only actual effect is that from module_name import * won't import variables that start with a single underscore.

class Queue:
  def __init__(self, contents):
    self._hiddenlist = list(contents)

  def push(self, value):
    self._hiddenlist.insert(0, value)
   
  def pop(self):
    return self._hiddenlist.pop(-1)

  def __repr__(self):
    return "Queue({})".format(self._hiddenlist)

queue = Queue([1, 2, 3])
print(queue)
queue.push(0)
print(queue)
queue.pop()
print(queue)
print(queue._hiddenlist)

>>>
Queue([1, 2, 3])
Queue([0, 1, 2, 3])
Queue([0, 1, 2])
[0, 1, 2]
>>> 

Strongly private methods and attributes have a double underscore at the beginning of their names. 
This causes their names to be mangled, which means that they can't be accessed from outside the class.
The purpose of this isn't to ensure that they are kept private, 
but to avoid bugs if there are subclasses that have methods or attributes with the same names.
Name mangled methods can still be accessed externally, but by a different name. 
The method __privatemethod of class Spam could be accessed externally with _Spam__privatemethod.

class Spam:
  __egg = 7
  def print_egg(self):
    print(self.__egg)

s = Spam()
s.print_egg()
print(s._Spam__egg)
print(s.__egg)

>>>
7
7
AttributeError: 'Spam' object has no attribute '__egg'
>>>

</pre>

# class methods
<pre>
Methods of objects we've looked at so far are called by an instance of a class, which is then passed 
to the self parameter of the method.
Class methods are different - they are called by a class, which is passed to the cls parameter of the method.
A common use of these are factory methods, which instantiate an instance of a class, using different parameters 
than those usually passed to the class constructor.
Class methods are marked with a classmethod decorator.

class Rectangle:
  def __init__(self, width, height):
    self.width = width
    self.height = height

  def calculate_area(self):
    return self.width * self.height

  @classmethod
  def new_square(cls, side_length):
    return cls(side_length, side_length)

square = Rectangle.new_square(5)
print(square.calculate_area())

new_square is a class method and is called on the class, rather than on an instance of the class. 
It returns a new object of the class cls.

>>>
25
>>>

</pre>

# static methods
<pre>
Static methods are similar to class methods, except they don't receive any additional arguments; 
they are identical to normal functions that belong to a class.
They are marked with the staticmethod decorator.

class Pizza:
  def __init__(self, toppings):
    self.toppings = toppings

  @staticmethod
  def validate_topping(topping):
    if topping == "pineapple":
      raise ValueError("No pineapples!")
    else:
      return True

ingredients = ["cheese", "onions", "spam"]
if all(Pizza.validate_topping(i) for i in ingredients):
  pizza = Pizza(ingredients) 

</pre>

# properties
<pre>
Properties provide a way of customizing access to instance attributes.
They are created by putting the property decorator above a method, 
which means when the instance attribute with the same name as the method is accessed, the method will be called instead.
One common use of a property is to make an attribute read-only.

class Pizza:
  def __init__(self, toppings):
    self.toppings = toppings
    
  @property
  def pineapple_allowed(self):
    return False

pizza = Pizza(["cheese", "tomato"])
print(pizza.pineapple_allowed)
pizza.pineapple_allowed = True

>>>
False

AttributeError: can't set attribute
>>>

Properties can also be set by defining setter/getter functions.
The setter function sets the corresponding property's value.
The getter gets the value.
To define a setter, you need to use a decorator of the same name as the property, 
followed by a dot and the setter keyword.
The same applies to defining getter functions.

class Pizza:
  def __init__(self, toppings):
    self.toppings = toppings
    self._pineapple_allowed = False

  @property
  def pineapple_allowed(self):
    return self._pineapple_allowed

  @pineapple_allowed.setter
  def pineapple_allowed(self, value):
    if value:
      password = input("Enter the password: ")
      if password == "Sw0rdf1sh!":
        self._pineapple_allowed = value
      else:
        raise ValueError("Alert! Intruder!")

pizza = Pizza(["cheese", "tomato"])
print(pizza.pineapple_allowed)
pizza.pineapple_allowed = True
print(pizza.pineapple_allowed)

>>>
False
Enter the password: Sw0rdf1sh!
True

</pre>