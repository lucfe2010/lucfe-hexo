---
title: python crash course
categories: [0004 Formal science, 计算机科学技术 Computer science]
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
>>> simple_url = nostarch_url.removeprefix('https://')

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

## Working with Lists

## if Statements

## Dictionaries

## User Input and while Loops

## Functions

## Classes

## Files and Exceptions

## Testing Your Code
