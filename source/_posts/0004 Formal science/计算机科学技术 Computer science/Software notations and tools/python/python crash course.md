---
title: python crash course
categories: [0004 Formal science, 计算机科学技术 Computer science]
tags: [python]
---

## Getting Started

### Setting up your Programming Environment

#### installing Python

<https://www.python.org/downloads/>

run the installer. Make sure you select the option Add Python to PATH, which will make it easier to configure your system correctly. Figure 1-1 shows this option selected.

![Alt text](</assets/images/python crash course/image.png>)

#### Running Python in a Terminal Session

Open a new command window and enter python in lowercase. You should
see a Python prompt (>>>), which means Windows has found the version of
Python you just installed.

#### Installing the Python Extension for VS Code

To install the Python extension, click the Manage icon, which looks
like a gear in the lower-left corner of the VS Code app. In the menu that
appears, click **Extensions**. Enter **python** in the search box and click the
Python extension. (If you see more than one extension named Python,
choose the one supplied by Microsoft.)

#### running hello_world.py

folder: python_work

file: hello_world.py

`print("Hello Python world!")`

vscode -> run -> Run Without Debugging or press CTRL-F5

`Hello Python world!`

#### Running Python Programs from a Terminal

terminal to run hello_world.py:

```bash
C:\> cd Desktop\python_work
C:\Desktop\python_work> dir
hello_world.py
C:\Desktop\python_work> python hello_world.py
Hello Python world!
```

First, use the `cd` command to navigate to the python_work folder, which is in the Desktop folder.

Next, use the `dir` command to make sure hello_world.py is in this folder.

Then run the file using the command `python hello_world.py`.

## Variables and Simple Data Types

### variable

```py
message = "Hello Python world!"
print(message)
```

output

`Hello Python world!`

We’ve added a *variable* named *message*.

Every variable is connected to a
*value*, which is the information associated with that variable.

---

```py
message = "Hello Python world!"
print(message)
message = "Hello Python Crash Course world!"
print(message)
```

output:

```bash
Hello Python world!
Hello Python Crash Course world!
```

You can change the value of a variable in your program at any time,
and Python will always keep track of its current value.

#### Naming and Using Variables

rules:

- Variable names can contain only letters, numbers, and underscores.
They can start with a letter or an underscore, but not with a number.
For instance, you can call a variable message_1 but not 1_message.
- Spaces are not allowed in variable names, but underscores can be used
to separate words in variable names. For example, greeting_message works
but greeting message will cause errors.
- Avoid using Python keywords and function names as variable names.
For example, do not use the word print as a variable name; Python
has reserved it for a particular programmatic purpose. (See “Python
Keywords and Built-in Functions” on page 466.)
- Variable names should be short but descriptive. For example, name is
better than n, student_name is better than s_n, and name_length is better
than length_of_persons_name.
- Be careful when using the lowercase letter l and the uppercase letter O
because they could be confused with the numbers 1 and 0.

> The Python variables you’re using at this point should be lowercase. You won’t get errors if you use uppercase letters, but uppercase letters in variable names have special meanings that we’ll discuss in later chapters.

#### Avoiding Name Errors When Using Variables

```py
message = "Hello Python Crash Course reader!"
print(mesage)
```

When an error occurs in your program, The interpreter provides
a ***traceback*** when a program cannot run successfully.

A traceback is a record of where the interpreter ran into trouble when trying to execute your code.

example:

```bash
Traceback (most recent call last):
File "hello_world.py", line 2, in <module> # 1 
print(mesage) # 2
 ^^^^^^
NameError: name 'mesage' is not defined. Did you mean: 'message'? # 3
```

The output reports that an error occurs in **line 2** of the file **hello_world.py** and tells us **what kind of error** it found 3.
In this case it found a name error
and reports that the variable being printed, mesage, has not been defined.

A name error usually means we either forgot to set a variable’s value before using it, or we made a spelling mistake when entering the variable’s name.

If Python finds a variable name that’s similar to the one it doesn’t recognize, it will ask if that’s the name you meant to use.

#### Variables Are Labels

 It’s much better to think of variables as labels that you can assign to values. You can
also say that a variable references a certain value.

### Strings

A string is a series of characters.
Anything inside quotes is considered a string in Python, and you can use single or double quotes around your

strings like this:

"This is a string."
'This is also a string.'

use quotes and apostrophes within your strings:

'I told my friend, "Python is my favorite language!"'
"The language 'Python' is named after Monty Python, not the snake."
"One of Python's strengths is its diverse and supportive community."

#### Changing Case in a String with Methods

string.title()

Return a version of the string where each word is titlecased.
More specifically, words start with uppercased characters and all remaining cased characters have lower case.

```py
name = "ada lovelace"
print(name.title())
```

output:
`Ada Lovelace`

A `method` is an action that Python can perform on a piece of data. The dot (.) after name in `name.title()` tells Python to make the `title()` method act on the variable `name`.

Every method is followed by a set of parentheses, because
methods often need additional information to do their work. That information is provided inside the parentheses.

The title() function doesn’t need
any additional information, so its parentheses are empty.

---

change a string to all uppercase or all lowercase letters like this:

```py
name = "Ada Lovelace"
print(name.upper())
print(name.lower())
```

This will display the following:

ADA LOVELACE
ada lovelace

> The lower() method is particularly useful for storing data. You typically won’t want to trust the capitalization that your users provide, so you’ll convert strings to lowercase before storing them. Then when you want to display the information, you’ll use the case that makes the most sense foreach string.

#### Using Variables in Strings

use a variable’s value inside a string:

```py
first_name = "ada"
last_name = "lovelace"
full_name = f"{first_name} {last_name}" # 1
print(full_name)
```

place the letter f immediately
before the opening quotation mark 1. Put braces around the name or
names of any variable you want to use inside the string.

These strings are called **f-strings**. The f is for format, because Python
formats the string by replacing the name of any variable in braces with its
value. The output from the previous code is:
`ada lovelace`

---

another example:

```py
first_name = "ada"
last_name = "lovelace"
full_name = f"{first_name} {last_name}"
print(f"Hello, {full_name.title()}!") # 1 
```

output:

Hello, Ada Lovelace!

#### Adding Whitespace to Strings with Tabs or Newlines

whitespace refers to any nonprinting characters, such as
spaces, tabs, and end-of-line symbols.
use whitespace to organize your output so it’s easier for users to read.

a tab `\t`:

```bash
>>> print("Python")
Python
>>> print("\tPython")
    Python
```

newline `\n`:

```bash
>>> print("Languages:\nPython\nC\nJavaScript")
Languages:
Python
C
JavaScript
```

combine tabs and newlines:

```bash
>>> print("Languages:\n\tPython\n\tC\n\tJavaScript")
Languages:
    Python
    C
    JavaScript
```

#### Stripping Whitespace

'python' and 'python ' to a program, they are two different strings.

often you’ll want to compare two strings to determine whether they are the same. Extra whitespace can be confusing in much simpler situations as well.

eliminate extra whitespace from data that people enter.

---

To ensure that no whitespace exists at the right side of a string, use
the `rstrip()` method:

```bash
>>> favorite_language = 'python ' # 1
>>> favorite_language  # 2
'python '
>>> favorite_language.rstrip() # 3
'python'
>>> favorite_language  # 4
'python '
```

---

However, it is only removed temporarily. If you ask for the value
of favorite_language again, the string looks the same as when it was entered,
including the extra whitespace 4.
To remove the whitespace from the string permanently, you have to
associate the stripped value with the variable name:

```bash
>>> favorite_language = 'python '
>>> favorite_language = favorite_language.rstrip() # 1
>>> favorite_language
'python'
```

---
strip whitespace from the left side of a string using the `lstrip()` method
from both sides at once using `strip()`:

```bash
>>> favorite_language = ' python '  # 1 
>>> favorite_language.rstrip()  # 2 
' python'
>>> favorite_language.lstrip() # 3 
'python '
>>> favorite_language.strip() # 4 
'python'
```

In the real world, these stripping functions are used most often to clean up
user input before it’s stored in a program.

#### Removing Prefixes

remove a prefix.

```bash
>>> nostarch_url = 'https://nostarch.com'
>>> nostarch_url.removeprefix('https://')
'nostarch.com'
```

Enter the name of the variable followed by a dot, and then the method
`removeprefix()`. Inside the parentheses, enter the prefix you want to remove
from the original string.

Like the methods for removing whitespace, removeprefix() leaves the
original string unchanged. If you want to keep the new value with the prefix removed, either reassign it to the original variable or assign it to a new
variable:

`>>> simple_url = nostarch_url.removeprefix('https://')`

#### Avoiding Syntax Errors with Strings

A syntax error occurs when Python doesn’t recognize a section of your program as valid Python code.

example

```py
message = 'One of Python's strengths is its diverse community.'
print(message)
```

You’ll see the following output:

```bash
File "apostrophe.py", line 1
message = 'One of Python's strengths is its diverse community.'
1 ^
SyntaxError: unterminated string literal (detected at line 1)
```

> Your editor’s *syntax highlighting feature* should help you spot some syntax errors quickly as you write your programs. If you see Python code highlighted as if it’s English or English highlighted as if it’s Python code, you probably have a mismatched quotation mark somewhere in your file.

### Numbers

#### Integers

You can add (+), subtract (-), multiply (*), and divide (/) integers in Python.

```bash
>>> 2 + 3
5
>>> 3 - 2
1
>>> 2 * 3
6
>>> 3 / 2
1.5
```

uses two multiplication symbols to represent **exponents**:

```bash
>>> 3 ** 2
9
>>> 3 ** 3
27
>>> 10 ** 6
1000000
```

Python supports the **order of operations** too, so you can use multiple
operations in one expression. You can also use **parentheses** to modify the
order of operations. For example:

```bash
>>> 2 + 3*4
14
>>> (2 + 3) * 4
20
```

> The spacing in these examples has no effect on how Python evaluates the expressions; it simply helps you more quickly spot the operations that have priority when you’re reading through the code.

### Floats

Python calls any number with a decimal point a float. it refers to the fact that a decimal point Variables and can appear at any position in a number.

For the most part, you can use floats without worrying about how they
behave. Simply enter the numbers you want to use, and Python will most
likely do what you expect:

```bash
>>> 0.1 + 0.1
0.2
>>> 0.2 + 0.2
0.4
>>> 2 *0.1
0.2
>>> 2* 0.2
0.4
```

---

However, be aware that you can sometimes get an arbitrary number of
decimal places in your answer:

```bash
>>> 0.2 + 0.1
0.30000000000000004
>>> 3 * 0.1
0.30000000000000004
```

This happens in all languages and is of little concern. Python tries to
find a way to represent the result as precisely as possible, which is sometimes
difficult given how computers have to represent numbers internally.

#### Integers and Floats

When you divide any two numbers, even if they are integers that result in a
whole number, you’ll always get a float:

```bash
>>> 4/2
2.0
```

If you mix an integer and a float in any other operation, you’ll get a
float as well:

```bash
>>> 1 + 2.0
3.0
>>> 2 * 3.0
6.0
>>> 3.0 ** 2
9.0
```

Python defaults to a float in any operation that uses a float, even if the
output is a whole number.

#### Underscores in Numbers

When you’re writing long numbers, you can group digits using underscores
to make large numbers more readable:

```bash
>>> universe_age = 14_000_000_000
>>> print(universe_age)
14000000000
```

Python ignores the underscores when storing these kinds of values.

Even if you don’t group the digits in threes, the value will still be unaffected. To Python, 1000 is the same as 1_000, which is the same as 10_00. This
feature works for both integers and floats.

#### Multiple Assignment

You can assign values to more than one variable using just a single line of
code. This can help shorten your programs and make them easier to read;

you’ll use this technique most often when initializing a set of numbers.
For example, here’s how you can initialize the variables x, y, and z to zero:

`>>> x, y, z = 0, 0, 0`

You need to separate the variable names with commas, and do the same
with the values, and Python will assign each value to its respective variable.
As long as the number of values matches the number of variables, Python
will match them up correctly

#### Constants

A constant is a variable whose value stays the same throughout the life of a
program.

Python doesn’t have built-in constant types, but Python programmers use all capital letters to indicate a variable should be treated as a constant and never be changed:

MAX_CONNECTIONS = 5000

### Comments

u should add notes within your programs that describe your overall approach to the
problem you’re solving.

A comment allows you to write notes in your spoken
language, within your programs.

#### How Do You Write Comments?

In Python, the hash mark (#) indicates a comment. Anything following a
hash mark in your code is ignored by the Python interpreter. For example:

```py
# Say hello to everyone.
print("Hello Python people!")
```

Python ignores the first line and executes the second line.
Hello Python people!

## Introducing Lists

### what is a list

A list is a collection of items in a particular order

Because a list usually contains more than one element, it’s a good idea to make the name of your list plural, such as `letters`, `digits`, or `names`

In Python, square brackets ([]) indicate a list, and individual elements in the list are separated by commas.example

```python
bicycles = ['trek', 'cannondale', 'redline', 'specialized']
print(bicycles)
```

output:
`['trek', 'cannondale', 'redline', 'specialized']`

#### Accessing Elements in a List

Lists are ordered collections, so you can access any element in a list by
telling Python the position, or index, of the item desired. To access an element in a list, write the name of the list followed by the index of the item
enclosed in square brackets.

```py
bicycles = ['trek', 'cannondale', 'redline', 'specialized']
print(bicycles[0])
```

output
`trek`

#### Index Positions Start at 0, Not 1

Python has a special syntax for accessing the last element in a list. If you
ask for the item at index -1, Python always returns the last item in the list:

```py
bicy
cles = ['trek', 'cannondale', 'redline', 'specialized']
print(bicycles[-1])
```

The index -2 returns the second item from the end of the list, the index -3 returns the third item from the end, and so forth.

#### Using Individual Values from a List

You can use individual values from a list just as you would any other variable.

```py
bicycles = ['trek', 'cannondale', 'redline', 'specialized']
message = f"My first bicycle was a {bicycles[0].title()}."
print(message)
```

### Modifying, Adding, and Removing Elements

Most lists you create will be dynamic, meaning you’ll build a list and then
add and remove elements from it as your program runs its course.

#### Modifying Elements in a List

To change an element, use the name of the list followed
by the index of the element you want to change, and then provide the new
value you want that item to have.

```py
motorcycles = ['honda', 'yamaha', 'suzuki']
print(motorcycles)
motorcycles[0] = 'ducati'
print(motorcycles)
```

output
['honda', 'yamaha', 'suzuki']
['ducati', 'yamaha', 'suzuki']

#### Adding Elements to a List

##### Appending Elements to the End of a List

`append` the item to the
list. When you `append` an item to a list, the new element is added to the end
of the list

```py
motorcycles = ['honda', 'yamaha', 'suzuki']
print(motorcycles)
motorcycles.append('ducati')
print(motorcycles)
```

---

To put your users in control, start by defining an empty list that
will hold the users’ values. Then append each new value provided to the list
you just created.

For example,

```python
motorcycles = []
motorcycles.append('honda')
motorcycles.append('yamaha')
motorcycles.append('suzuki')
print(motorcycles)
```

output
['honda', 'yamaha', 'suzuki']

##### Inserting Elements into a List

You can add a new element at any position in your list by using the insert()
method. You do this by specifying the index of the new element and the
value of the new item:
This operation shifts every other value in the list one position to the
right.

```py
motorcycles = ['honda', 'yamaha', 'suzuki']
motorcycles.insert(0, 'ducati')
print(motorcycles)
```

output
[ducati', 'honda', 'yamaha', 'suzuki']

#### Removing Elements from a List

##### Removing an Item Using the del Statement

know the position of the item you want to remove from a list, you can
use the del statement:

motorcycles = ['honda', 'yamaha', 'suzuki']
print(motorcycles)
del motorcycles[0]
print(motorcycles)

##### Removing an Item Using the pop() Method

The pop() method removes the last item in a list, but it lets you work
with that item after removing it. The term pop comes from thinking of a
list as a stack of items and popping one item off the top of the stack. In this
analogy, the top of a stack corresponds to the end of a list.

```py
motorcycles = ['honda', 'yamaha', 'suzuki']
print(motorcycles)
popped_motorcycle = motorcycles.pop()
print(motorcycles)
print(popped_motorcycle)
```

['honda', 'yamaha', 'suzuki']
['honda', 'yamaha']
suzuki

##### Popping Items from Any Position in a List

```py
motorcycles = ['honda', 'yamaha', 'suzuki']
first_owned = motorcycles.pop(0)
print(f"The first motorcycle I owned was a {first_owned.title()}.")
```

The first motorcycle I owned was a Honda.

Remember that each time you use pop(), the item you work with is no
longer stored in the list.

> when you want to delete an item from a list and not use that item in any way, use the del statement; if you want to use an item as you remove it, use the pop() method.

##### Removing an Item by Value

If you only know the value of the item you want to remove, you
can use the remove() method

```py
motorcycles = ['honda', 'yamaha', 'suzuki', 'ducati']
print(motorcycles)
motorcycles.remove('ducati')
print(motorcycles)
```

['honda', 'yamaha', 'suzuki', 'ducati']
['honda', 'yamaha', 'suzuki']

> The remove() method deletes only the first occurrence of the value you specify. If there’s a possibility the value appears more than once in the list, you’ll need to use a loop to make sure all occurrences of the value are removed.

### Organizing a List

Sometimes you’ll want
to preserve the original order of your list, and other times you’ll want to
change the original order.

#### Sorting a List Permanently with the sort() Method

The sort() method changes the order of the list permanently. The cars
are now in alphabetical order, and we can never revert to the original order:

```py
cars = ['bmw', 'audi', 'toyota', 'subaru']
cars.sort()
print(cars)
```

['audi', 'bmw', 'subaru', 'toyota']

o sort this list in reverse-alphabetical order

```py
cars = ['bmw', 'audi', 'toyota', 'subaru']
cars.sort(reverse=True)
print(cars)
```

['toyota', 'subaru', 'bmw', 'audi']

#### Sorting a List Temporarily with the sorted() Function

The sorted() function lets you display your list
in a particular order, but doesn’t affect the actual order of the list.

```py
cars = ['bmw', 'audi', 'toyota', 'subaru']
print("Here is the original list:")
print(cars)
print("\nHere is the sorted list:")
print(sorted(cars))
print("\nHere is the original list again:")
print(cars)
```

output:

Here is the original list:
['bmw', 'audi', 'toyota', 'subaru']
Here is the sorted list:
['audi', 'bmw', 'subaru', 'toyota']
1 Here is the original list again:
['bmw', 'audi', 'toyota', 'subaru']

The sorted() function can also accept a reverse=True
argument if you want to display a list in reverse-alphabetical order.

> Sorting a list alphabetically is a bit more complicated when all the values are not in lowercase

#### Printing a List in Reverse Order

If we originally stored the list of cars in chronological order according to when
we owned them, we could easily rearrange the list into reverse-chronological
order:

```py
cars = ['bmw', 'audi', 'toyota', 'subaru']
print(cars)
cars.reverse()
print(cars)
```

['bmw', 'audi', 'toyota', 'subaru']
['subaru', 'toyota', 'audi', 'bmw']

#### Finding the Length of a List

>>> cars = ['bmw', 'audi', 'toyota', 'subaru']
>>> len(cars)

### Avoiding Index Errors When Working with Lists

```py
motorcycles = ['honda', 'yamaha', 'suzuki']
print(motorcycles[3])
```

This example results in an index error:

```bash
Traceback (most recent call last):
 File "motorcycles.py", line 2, in <module>
 print(motorcycles[3])
 ~~~~~~~~~~~^^^
IndexError: list index out of range
```

Keep in mind that whenever you want to access the last item in a list,
you should use the index -1. This will always work, even if your list has
changed size since the last time you accessed it:

motorcycles = ['honda', 'yamaha', 'suzuki']
print(motorcycles[-1])

output:

suzuki

---

The only time this approach will cause an error is when you request the
last item from an empty list:

```py
motorcycles = []
print(motorcycles[-1])
```

No items are in motorcycles, so Python returns another index error:

```bash
Traceback (most recent call last):
 File "motorcyles.py", line 3, in <module>
 print(motorcycles[-1])
 ~~~~~~~~~~~^^^^
IndexError: list index out of range

```

> If an index error occurs and you can’t figure out how to resolve it, try
printing your list or just printing the length of your list. Your list might look
much different than you thought it did, especially if it has been managed
dynamically by your program. Seeing the actual list, or the exact number of
items in your list, can help you sort out such logical errors.

## Working with Lists

Looping allows you to take the same action, or set
of actions, with every item in a list

### Looping Through an Entire List

Say we have a list of magicians’ names, and we want to print out each name in the list.

We could do this by retrieving each name from the list individually, but this approach could cause several problems. For one, it would
be repetitive to do this with a long list of names. Also, we’d have to change
our code each time the list’s length changed. Using a for loop avoids both of
these issues by letting Python manage these issues internally.

```py
magicians = ['alice', 'david', 'carolina']
for magician in magicians:
    print(magician)
```

alice
david
carolina

#### A Closer Look at Looping

`for magician in magicians:`

This line tells Python to retrieve the *first value* from the list *magicians* and associate it with the variable *magician*. 

the set of steps is repeated once for each item in the list, no matter how many items
are in the list.

you can choose
any name you want for the temporary variable that will be associated with
each value in the list. However, it’s helpful to choose a meaningful name
that represents a single item from the list.

Using singular and plural names can help
you identify whether a section of code is working with a single element from
the list or the entire list.

#### Doing More Work Within a for Loop

```py
magicians = ['alice', 'david', 'carolina']
for magician in magicians:
    print(f"{magician.title()}, that was a great trick!")
    print(f"I can't wait to see your next trick, {magician.title()}.\n")
```

Alice, that was a great trick!
I can't wait to see your next trick, Alice.

David, that was a great trick!
I can't wait to see your next trick, David.

Carolina, that was a great trick!
I can't wait to see your next trick, Carolina.

#### Doing Something After a for Loop

Any lines of code after the for loop that are not indented are executed
once without repetition.

```py
magicians = ['alice', 'david', 'carolina']
for magician in magicians:
 print(f"{magician.title()}, that was a great trick!")
 print(f"I can't wait to see your next trick, {magician.title()}.\n")
print("Thank you, everyone. That was a great magic show!")
```

Alice, that was a great trick!
I can't wait to see your next trick, Alice.

David, that was a great trick!
Working with Lists   53
I can't wait to see your next trick, David.

Carolina, that was a great trick!
I can't wait to see your next trick, Carolina.

Thank you, everyone. That was a great magic show!

### Avoiding Indentation Errors

Python uses indentation to determine how a line, or group of lines, is related
to the rest of the program.

common indentation errors. For example, people
sometimes indent lines of code that don’t need to be indented or forget
to indent lines that need to be indented.

#### Forgetting to Indent

```py
magicians = ['alice', 'david', 'carolina']
for magician in magicians:
print(magician)
```

```bash
File "magicians.py", line 3
 print(magician)
 ^
IndentationError: expected an indented block after 'for' statement on line 2
```


#### Forgetting to Indent Additional Lines

This is a logical error. The syntax is valid Python code, but the code does
not produce the desired result because a problem occurs in its logic. If you
expect to see a certain action repeated once for each item in a list and it’s
executed only once, determine whether you need to simply indent a line or
a group of lines.


```py
magicians = ['alice', 'david', 'carolina']
for magician in magicians:
    print(f"{magician.title()}, that was a great trick!")
print(f"I can't wait to see your next trick, {magician.title()}.\n")
```
output:

Alice, that was a great trick!
David, that was a great trick!
Carolina, that was a great trick!
I can't wait to see your next trick, Carolina.


#### Indenting Unnecessarily

```py
message = "Hello Python world!"
    print(message)
```


File "hello_world.py", line 2
 print(message)
 ^
IndentationError: unexpected indent

You can avoid unexpected indentation errors by indenting only when you have a specific reason to do so.

#### Indenting Unnecessarily After the Loop

```py
magicians = ['alice', 'david', 'carolina']
for magician in magicians:
    print(f"{magician.title()}, that was a great trick!")
    print(f"I can't wait to see your next trick, {magician.title()}.\n")
    print("Thank you everyone, that was a great magic show!")
```

```bash
Alice, that was a great trick!
I can't wait to see your next trick, Alice.

Thank you everyone, that was a great magic show!
David, that was a great trick!
I can't wait to see your next trick, David.

Thank you everyone, that was a great magic show!
Carolina, that was a great trick!
I can't wait to see your next trick, Carolina.

Thank you everyone, that was a great magic show!
```


This is another ***logical error***, similar to the one in “Forgetting to Indent
Additional Lines” on page 54. Because Python doesn’t know what you’re
trying to accomplish with your code, it will run all code that is written in
valid syntax. If an action is repeated many times when it should be executed
only once, you probably need to unindent the code for that action.


#### Forgetting the Colon

```py
magicians = ['alice', 'david', 'carolina']
for magician in magicians
    print(magician)
```

```bash
 File "magicians.py", line 2
 for magician in magicians
 ^
SyntaxError: expected ':'
```


## if Statements

## Dictionaries

## User Input and while Loops

## Functions

## Classes

## Files and Exceptions

## Testing Your Code
