---
title: Intro to Python
layout: tutorial
---
# Intro to Python

<!-- TOC depthFrom:1 depthTo:6 withLinks:1 updateOnSave:1 orderedList:0 -->

- [Intro to Python](#intro-to-python)
	- [Setting Up](#setting-up)
		- [Installing Python](#installing-python)
			- [Linux](#linux)
			- [Mac](#mac)
			- [Windows](#windows)
		- [Setuptools and Pip](#setuptools-and-pip)
			- [Linux](#linux)
			- [Mac](#mac)
			- [Windows](#windows)
		- [Difference between Python 2.x and 3.x](#difference-between-python-2x-and-3x)
			- [What are the differences](#what-are-the-differences)
			- [What version should I use?](#what-version-should-i-use)
			- [Learn More](#learn-more)
	- [Using the interactive shell](#using-the-interactive-shell)
		- [Simple Math](#simple-math)
		- [Data Types](#data-types)
		- [String Concatenation and Replication](#string-concatenation-and-replication)
		- [Variables](#variables)
			- [Assignment Statements](#assignment-statements)
			- [Variable Names](#variable-names)
	- [Writing and Running your first program](#writing-and-running-your-first-program)
- [This program says hello and asks for my name.](#this-program-says-hello-and-asks-for-my-name)
		- [Dissecting Your Program](#dissecting-your-program)
			- [Comments](#comments)
- [This program says hello and asks for my name.](#this-program-says-hello-and-asks-for-my-name)
			- [The print() Function](#the-print-function)
			- [The input() Function](#the-input-function)
			- [Printing the User’s Name](#printing-the-users-name)
			- [The len() function](#the-len-function)
			- [The str(), int(), and float() Functions](#the-str-int-and-float-functions)
	- [Flow Control](#flow-control)
		- [Boolean values](#boolean-values)
		- [Comparison Operators](#comparison-operators)
		- [Boolean operators](#boolean-operators)
		- [Flow Control Statements](#flow-control-statements)
			- [if Statements](#if-statements)
			- [else Statements](#else-statements)
			- [elif Statements](#elif-statements)
			- [while statements](#while-statements)
			- [break Statements](#break-statements)
			- [continue statements](#continue-statements)
			- [for Loops and the range() Function](#for-loops-and-the-range-function)
	- [Importing Modules](#importing-modules)
		- [from import Statements](#from-import-statements)
		- [Ending a Program Early with sys.exit()](#ending-a-program-early-with-sysexit)
	- [Functions](#functions)
		- [Functions with parameters](#functions-with-parameters)
		- [Functions with return statements](#functions-with-return-statements)
		- [The None Value](#the-none-value)
		- [Keyword Arguments](#keyword-arguments)
	- [A Short Program: Guess the Number](#a-short-program-guess-the-number)
	- [Lists](#lists)
		- [Getting Individual Values in a List with Indexes](#getting-individual-values-in-a-list-with-indexes)
		- [Multidimensional List](#multidimensional-list)
		- [Negative Indexes](#negative-indexes)
		- [Getting Sublists with Slices](#getting-sublists-with-slices)
		- [Getting a List’s Length with len()](#getting-a-lists-length-with-len)
		- [Removing Values from Lists with del Statements](#removing-values-from-lists-with-del-statements)
		- [Using for Loops with Lists](#using-for-loops-with-lists)
		- [Finding a Value in a List with the index() Method](#finding-a-value-in-a-list-with-the-index-method)
		- [Adding Values to Lists with the append() and insert() Methods](#adding-values-to-lists-with-the-append-and-insert-methods)
	- [The Dictionary Data Type](#the-dictionary-data-type)
		- [The keys(), values(), and items() Methods](#the-keys-values-and-items-methods)
		- [Checking Whether a Key or Value Exists in a Dictionary](#checking-whether-a-key-or-value-exists-in-a-dictionary)
		- [Pretty Printing](#pretty-printing)

<!-- /TOC -->

## Setting Up

### Installing Python

#### Linux

Most installations of linux have Python 2.7.x and Python 3.x preinstalled so you shouldn't have any trouble using python on it. To verify your python installation try the following commands in the shell. If your version of linux happens to not have python preinstalled (which is very rare), you can download and build python from source or use the inbuilt package manager (eg. apt) to install it. Since installation instructions vary between various flavors, its best to simply google the instructions for your version.

```
python -V
```
```
python3 -V
```

#### Mac

Much like linux, Mac also comes with python 2.7.x preinstalled on the system. You can verify the installation by running the following in the shell

```
python -V
```

If you would like to upgrade your version of python or install python3 then you can download the latest install from https://www.python.org/downloads/mac-osx/

#### Windows

Unlike the UNIX based operating systems, windows does not come with python preinstalled and because OS level differences, there are certain libraries that don't work on windows (and some that dont work on unix but those are rarer). To install python on your windows machine, download the latest release of the python installer from https://www.python.org/downloads/windows/

After the installation is finished, the python interpreter is stored in `C:\Python27` (might differ based on your version of python). You will also see the python shell in your installed programs. To use python from your normal command line or Powershell you need to add python to your PATH. You can do that by adding `C:\Python27\;C:\Python27\Scripts\` or by running the following in the Powershell.

```
[Environment]::SetEnvironmentVariable("Path", "$env:Path;C:\Python27\;C:\Python27\Scripts\", "User")
```

### Setuptools and Pip

Setuptools is a python library that facilitates packaging projects by enhancing the Python standard library distutils . Pip is the package manager used by Python. You will use this to install new libraries and to keep them up to date. They both go hand in hand are a key part of any python programmer's toolbelt.

#### Linux

To install Setuptools on a Linux machine, run the following command in the terminal

```
wget https://bootstrap.pypa.io/ez_setup.py -O - | sudo python
```

Once that is done, you can use the Setuptools to install Pip

```
sudo easy_install pip
```

#### Mac

The installation instructions for Mac are almost identical installing it on a Linux machine. You run

```
curl https://bootstrap.pypa.io/ez_setup.py -o - | sudo python
```

and then

```
sudo easy_install pip
```

#### Windows

The easiest way to install Setuptools on windows is to run the following in Powershell or downloading the file the command links to and running it in python.

```
(Invoke-WebRequest https://bootstrap.pypa.io/ez_setup.py).Content | python -
```

To install, you need to download the [get_pip.py](https://bootstrap.pypa.io/get-pip.py) file and running it in python.

### Difference between Python 2.x and 3.x

#### What are the differences

Short version: Python 2.x is legacy, Python 3.x is the present and future of the language

Python 3.0 was released in 2008. The final 2.x version 2.7 release came out in mid-2010, with a statement of extended support for this end-of-life release. The 2.x branch will see no new major releases after that. 3.x is under active development and has already seen over five years of stable releases, including version 3.3 in 2012, 3.4 in 2014, and 3.5 in 2015. This means that all recent standard library improvements, for example, are only available by default in Python 3.x.

Guido van Rossum (the original creator of the Python language) decided to clean up Python 2.x properly, with less regard for backwards compatibility than is the case for new releases in the 2.x range. The most drastic improvement is the better Unicode support (with all text strings being Unicode by default) as well as saner bytes/Unicode separation.

#### What version should I use?

If you can do exactly what you want with Python 3.x, great! There are a few minor downsides, such as very slightly worse library support and the fact that some current Linux distributions and Macs are still using 2.x as default (although Python 3 ships with many of them), but as a language Python 3.x is definitely ready. As long as Python 3.x is installed on your user's computers (which ought to be easy, since many people reading this may only be developing something for themselves or an environment they control) and you're writing things where you know none of the Python 2.x modules are needed, it is an excellent choice.

However, there are some key issues that may require you to use Python 2 rather than Python 3.

* Firstly, if you're deploying to an environment you don't control, that may impose a specific version, rather than allowing you a free selection from the available versions.
* Secondly, if you want to use a specific third party package or utility that doesn't yet have a released version that is compatible with Python 3, and porting that package is a non-trivial task, you may choose to use Python 2 in order to retain access to that package.

For the intents and purposes of this tutorial, it doesn't matter what version of python of python you use. I will be using version 2.7.10 mostly because I'm too lazy to install Python3 on this computer and also because typing python is easier than typing python3 (And I'm too lazy to setup an alias to go around that)

#### Learn More

* [Python2 or Python3](https://wiki.python.org/moin/Python2orPython3)
  + This is the website I quoted in the above section
* [The key differences between Python 2.7.x and Python 3.x with examples](http://sebastianraschka.com/Articles/2014_python_2_3_key_diff.html)

## Using the interactive shell

This section has a few examples that encourage you to type into the interactive shell, which lets you execute Python instructions one at a time and shows you the results instantly. Using the interactive shell is great for learning what basic Python instructions do, so give it a try as you follow along. You’ll remember the things you do much better than the things you only read.

You launch the interactive shell by typing `python` in your shell. This will launch your shell and give you information about your installation such as version and platform.

### Simple Math

Once you run the command, A window with the >>> prompt should appear; that’s the interactive shell. Enter 2 + 2 at the prompt to have Python do some simple math.

```shell
>>> 2 + 2
4
```

In Python, 2 + 2 is called an expression, which is the most basic kind of programming instruction in the language. Expressions consist of values (such as 2) and operators (such as +), and they can always evaluate (that is, reduce) down to a single value. That means you can use expressions anywhere in Python code that you could also use a value. In the previous example, 2 + 2 is evaluated down to a single value, 4. A single value with no operators is also considered an expression, though it evaluates only to itself, as shown here:

```shell
>>> 2
2
```

There are plenty of operators you can use in python and the following table lists a few of them ordered in order of precedence.

| Operator | Operation | Example | Evaluates to |
|:-------------:|:-------------:|:-------------:|:-------------:|:-------------:|
| ** | Exponent | 2 ** 3 | 8|
| % | Modulus/remainder | 22 % 8 | 6|
| // | Integer division/floored quotient | 22 // 8 | 2|
| / | Division | 22 / 8 | 2.75|
| * | Multiplication | 3 * 5 | 15|
| - | Subtraction | 5 - 2 | 3|
| + | Addition | 2 + 2 | 4|

The following are some examples of math in the python shell.

```shell
>>> 2 + 3 * 6
20
>>> (2 + 3) * 6
30
>>> 48565878 * 578453
28093077826734
>>> 2 ** 8
256
>>> 23 / 7
3.2857142857142856
>>> 23 // 7
3
>>> 23 % 7
2
>>> 2 + 2
4
>>> (5 - 1) * ((7 + 1) / (3 - 1))
16.0
```

### Data Types
Remember that expressions are just values combined with operators, and they always evaluate down to a single value. A data type is a category for values, and every value belongs to exactly one data type. The most Python Basics 17 common data types in Python are listed in Table 1-2. The values -2 and 30, for example, are said to be integer values. The integer (or int) data type indicates values that are whole numbers. Numbers with a decimal point, such as 3.14, are called floating-point numbers (or floats). Note that even though the value 42 is an integer, the value 42.0 would be a floating-point number.

| Data type | Examples |
|:-------------:|:-------------:|
|Integers | -2, -1, 0, 1, 2, 3, 4, 5 |
Floating-point numbers | -1.25, -1.0, --0.5, 0.0, 0.5, 1.0, 1.25 |
Strings | 'a', 'aa', 'aaa', 'Hello!', '11 cats' |

Note: Strings can be single quoted or double quoted and there is no difference between them.<sup>[source](https://docs.python.org/2.0/ref/strings.html)</sup>

### String Concatenation and Replication

The meaning of an operator may change based on the data types of the values next to it. For example, + is the addition operator when it operates on two integers or floating-point values. However, when + is used on two string values, it joins the strings as the string concatenation operator. Enter the following into the interactive shell:

```shell
>>> 'Alice' + 'Bob'
'AliceBob'
```

The expression evaluates down to a single, new string value that combines the text of the two strings. However, if you try to use the + operator on a string and an integer value, Python will not know how to handle this, and it will display an error message.

```
>>> 'Alice' + 42
Traceback (most recent call last):
 File "<pyshell#26>", line 1, in <module>
 'Alice' + 42
TypeError: Can't convert 'int' object to str implicitly
```

The * operator is used for multiplication when it operates on two integer
or floating-point values. But when the * operator is used on one string
value and one integer value, it becomes the string replication operator. Enter
a string multiplied by a number into the interactive shell to see this in action.

```shell
>>> 'Alice' * 5
'AliceAliceAliceAliceAlice'
```

### Variables

A variable is like a box in the computer’s memory where you can store a single value. If you want to use the result of an evaluated expression later in your program, you can save it inside a variable.

#### Assignment Statements

You’ll store values in variables with an assignment statement. An assignment statement consists of a variable name, an equal sign (called the assignment operator), and the value to be stored. If you enter the assignment statement foo = 42, then a variable named foo will have the integer value 42 stored in it

For example, enter the following into the interactive shell:

```
>>> foo = 40
>>> foo
40
>>> eggs = 2
>>> foo + eggs
42
>>> foo + eggs + foo
82
>>> foo = foo + 2
>>> foo
42
```

#### Variable Names

The following table has examples of legal variable names. You can name a variable
anything as long as it obeys the following three rules:
1. It can be only one word.
2. It can use only letters, numbers, and the underscore (\_) character.
3. It can’t begin with a number.

| Valid variable names | Invalid variable names |
| :-------------|:-------------|
balance | current-balance (hyphens are not allowed)
currentBalance | current balance (spaces are not allowed)
current_balance | 4account (can’t begin with a number)
\_spam | 42 (can’t begin with a number)
foo | total_$um (special characters like $ are not allowed)
account4 | 'hello' (special characters like ' are not allowed)

## Writing and Running your first program

While the interactive shell is good for running Python instructions one at a time, to write entire Python programs, you’ll type the instructions into a text editor. Popular text editors are Sublime Text, Atom and Vim. You can also use a python IDE such as Pycharm or IDLE which is like a text editor but has more features for writing code.

Enter the following code in a file.

```python
# This program says hello and asks for my name.
print('Hello world!')
print('What is your name?') # ask for their name
myName = input()
print('It is good to meet you, ' + myName)
print('The length of your name is:')
print(len(myName))
print('What is your age?') # ask for their age
myAge = input()
print('You will be ' + str(int(myAge) + 1) + ' in a year.')
```

Once you're done writing the program, you can run it by hitting run in Pycharm or by using the terminal and typing `python <filename>.py`

### Dissecting Your Program
With your new program open in the file editor, let’s take a quick tour of the Python instructions it uses by looking at what each line of code does.

#### Comments

The following line is called a comment.

```python
# This program says hello and asks for my name.
```
Python ignores comments, and you can use them to write notes or remind yourself what the code is trying to do. Any text for the rest of the line following a hash mark (#) is part of a comment.

Sometimes, programmers will put a # in front of a line of code to temporarily remove it while testing a program. This is called commenting out code, and it can be useful when you’re trying to figure out why a program doesn’t work. You can remove the # later when you are ready to put the line back in.

#### The print() Function

The print() function displays the string value inside the parentheses on the
screen.

```python
print('Hello world!')
print('What is your name?') # ask for their name
```

The line print('Hello world!') means “Print out the text in the string 'Hello world!'.” When Python executes this line, you say that Python is calling the print() function and the string value is being passed to the function. A value that is passed to a function call is an argument. Notice that the quotes are not printed to the screen. They just mark where the string begins and ends; they are not part of the string value.

#### The input() Function
The input() function waits for the user to type some text on the keyboard and press enter.

```python
myName = input()
```

This function call evaluates to a string equal to the user’s text, and the previous line of code assigns the myName variable to this string value.
You can think of the input() function call as an expression that evaluates to whatever string the user typed in. If the user entered 'Al', then the expression would evaluate to myName = 'Al'.

#### Printing the User’s Name

The following call to print() actually contains the expression 'It is good to meet you, ' + myName between the parentheses.

```
print('It is good to meet you, ' + myName)
```

Remember that expressions can always evaluate to a single value. If 'Al' is the value stored in myName on the previous line, then this expression evaluates to 'It is good to meet you, Al'. This single string value is then passed to print(), which prints it on the screen.

#### The len() function

You can pass the len() function a string value (or a variable containing a string), and the function evaluates to the integer value of the number of characters in that string.

```python
print('The length of your name is:')
print(len(myName))
```

Enter the following into the interactive shell to try this:

```shell
>>> len('hello')
5
>>> len('Mckenna is awesome')
18
>>> len('')
0
```

Just like those examples, len(myName) evaluates to an integer. It is then passed to print() to be displayed on the screen. Notice that print() allows you to pass it either integer values or string values.

#### The str(), int(), and float() Functions

If you want to concatenate an integer such as 29 with a string to pass to print(), you’ll need to get the value '29', which is the string form of 29. The str() function can be passed an integer value and will evaluate to a string value version of it, as follows:

```shell
>>> str(29)
'29'
>>> print('I am ' + str(29) + ' years old.')
I am 29 years old.
```

Because str(29) evaluates to '29', the expression 'I am ' + str(29) + ' years old.' evaluates to 'I am ' + '29' + ' years old.', which in turn evaluates to 'I am 29 years old.'. This is the value that is passed to the print() function.

The str(), int(), and float() functions will evaluate to the string, integer, and floating-point forms of the value you pass, respectively. Try converting some values in the interactive shell with these functions, and watch what happens.

```
>>> str(0)
'0'
>>> str(-3.14)
'-3.14'
>>> int('42')
42
>>> int('-99')
-99
>>> int(1.25)
1
>>> int(1.99)
1
>>> float('3.14')
3.14
>>> float(10)
10.0
```

## Flow Control

So you know the basics of individual instructions and that a program is just a series of instructions. But the real strength of programming isn’t just running (or executing) one instruction after another like a weekend errand list. Based on how the expressions evaluate, the program can decide to skip instructions, repeat them, or choose one of several instructions to run. In fact, you almost never want your programs to start from the first line of code and simply execute every line, straight to the end. Flow control statements can decide which Python instructions to execute under which conditions. These flow control statements directly correspond to the symbols in a flowchart, so I’ll provide flowchart versions of the code discussed in this section. The following image shows a flowchart for what to do if it’s raining. Follow the path made by the arrows from Start to End.

![Flowchart](/img/flow.png)

In a flowchart, there is usually more than one way to go from the start to the end. The same is true for lines of code in a computer program. Flowcharts represent these branching points with diamonds, while the other steps are represented with rectangles. The starting and ending steps are represented with rounded rectangles.

### Boolean values

While the integer, floating-point, and string data types have an unlimited number of possible values, the Boolean data type has only two values: True and False. (Boolean is capitalized because the data type is named after mathematician George Boole.) When typed as Python code, the Boolean values True and False lack the quotes you place around strings, and they always start with a capital T or F, with the rest of the word in lowercase.

### Comparison Operators

Comparison operators compare two values and evaluate down to a single Boolean value. Table 2-1 lists the comparison operators.

| Operator | Meaning |
|:-------------|:-------------|
== | Equal to
!= | Not equal to
< | Less than
\> | Greater than
<= | Less than or equal to
\>= | Greater than or equal to

These operators evaluate to True or False depending on the values you give them. Let’s try some operators now, starting with == and !=.

```
>>> 42 == 42
True
>>> 42 == 99
False
>>> 2 != 3
True
>>> 2 != 2
False
```

As you might expect, == (equal to) evaluates to True when the values
on both sides are the same, and != (not equal to) evaluates to True when
the two values are different. The == and != operators can actually work with
values of any data type.

### Boolean operators

The three Boolean operators (and, or, and not) are used to compare Boolean values. Like comparison operators, they evaluate these expressions down to a Boolean value. Let’s explore these operators in detail, starting with the and operator.

The and and or operators always take two Boolean values (or expressions), so they’re considered binary operators. The and operator evaluates an expression to True if both Boolean values are True; otherwise, it evaluates to False. Enter some expressions using and into the interactive shell to see it in action.

```shell
>>> True and True
True
>>> True and False
False
```

A truth table shows every possible result of a Boolean operator. The following is the truth table for the and operator.

| Expression | Evaluates to|
|:-------------|:-------------|
True and True | True
True and False | False
False and True | False
False and False | False

On the other hand, the or operator evaluates an expression to True if either of the two Boolean values is True. If both are False, it evaluates to False.

```shell
>>> False or True
True
>>> False or False
False
```

Unlike and and or, the not operator operates on only one Boolean value (or expression). The not operator simply evaluates to the opposite Boolean value.

```shell
>>> not True
False
u >>> not not not not True
True
```

### Flow Control Statements
Now, let’s explore the most important piece of flow control: the statements themselves. The statements represent the diamonds you saw in the flowchart in above figure, and they are the actual decisions your programs will make.

#### if Statements

The most common type of flow control statement is the if statement. An if statement’s clause (that is, the block following the if statement) will execute if the statement’s condition is True. The clause is skipped if the condition is False.

In plain English, an if statement could be read as, “If this condition is true, execute the code in the clause.” In Python, an if statement consists of the following:

* The if keyword
* A condition (that is, an expression that evaluates to True or False)
* A colon
* Starting on the next line, an indented block of code (called the if clause)

For example, let’s say you have some code that checks to see whether someone’s name is Alice. (Pretend name was assigned some value earlier.)

```python
if name == 'Alice':
    print('Hi, Alice.')
```

All flow control statements end with a colon and are followed by a new block of code (the clause). This if statement’s clause is the block with print('Hi, Alice.').

#### else Statements

An if clause can optionally be followed by an else statement. The else clause is executed only when the if statement’s condition is False. In plain English, an else statement could be read as, “If this condition is true, execute this code. Or else, execute that code.” An else statement doesn’t have a condition, and in code, an else statement always consists of the following:
* The else keyword
* A colon
* Starting on the next line, an indented block of code (called the else clause)

Returning to the Alice example, let’s look at some code that uses an else statement to offer a different greeting if the person’s name isn’t Alice.

```python
if name == 'Alice':
    print('Hi, Alice.')
else:
    print('Hello, stranger.')
```

#### elif Statements

While only one of the if or else clauses will execute, you may have a case where you want one of many possible clauses to execute. The elif statement is an “else if” statement that always follows an if or another elif statement. It provides another condition that is checked only if any of the previous conditions were False. In code, an elif statement always consists of the following:

* The elif keyword
* A condition (that is, an expression that evaluates to True or False)
* A colon
* Starting on the next line, an indented block of code (called the elif clause)

Let’s add an elif to the name checker to see this statement in action.

```python
if name == 'Alice':
    print('Hi, Alice.')
elif age < 12:
    print('You are not Alice, kiddo.')
```

You can also chain multiple elifs together. It will evaluate them one by one and as soon as one is found to be try it will execute that and skip to the end.

```python
if name == 'Alice':
    print('Hi, Alice.')
elif age < 12:
    print('You are not Alice, kiddo.')
elif age > 2000:
    print('Unlike you, Alice is not an undead, immortal vampire.')
elif age > 100:
    print('You are not Alice, grannie.')
```

#### while statements

You can make a block of code execute over and over again with a while statement. The code in a while clause will be executed as long as the while statement’s condition is True.

```python
foo = 0
while foo < 5:
    print('Hello, world.')
    foo = foo + 1
```

#### break Statements

There is a shortcut to getting the program execution to break out of a while loop’s clause early. If the execution reaches a break statement, it immediately exits the while loop’s clause. In code, a break statement simply contains the break keyword.

Pretty simple, right? Here’s a program that does the same thing as the previous program, but it uses a break statement to escape the loop. Enter the following codea and run it

```python
while True:
    print('Please type your name.')
    name = input()
    if name == 'your name':
        break
print('Thank you!')
```

The first line creates an infinite loop; it is a while loop whose condition is always True. (The expression True, after all, always evaluates down to the value True.) The program execution will always enter the loop and will exit it only when a break statement is executed. (An infinite loop that never exits is a common programming bug.)

#### continue statements

Like break statements, continue statements are used inside loops. When the program execution reaches a continue statement, the program execution immediately jumps back to the start of the loop and reevaluates the loop’s condition. (This is also what happens when the execution reaches the end of the loop.)

Let’s use continue to write a program that asks for a name and password.
Enter the following code into a new file editor window and save the program
as swordfish.py.

```python
while True:
    print('Who are you?')
    name = input()
    if name != 'Joe':
        continue
    print('Hello, Joe. What is the password? (It is a fish.)')
    password = input()
    if password == 'swordfish':
        break
print('Access granted.')
```

#### for Loops and the range() Function
The while loop keeps looping while its condition is True (which is the reason
for its name), but what if you want to execute a block of code only a certain
number of times? You can do this with a for loop statement and the range()
function.

Let’s create a new program called `fiveTimes.py` to help you see a for loop in action.

```
print('My name is')
for i in range(5):
    print('Jimmy Five Times (' + str(i) + ')')
```

## Importing Modules

All Python programs can call a basic set of functions called built-in functions, including the print(), input(), and len() functions you’ve seen before. Python also comes with a set of modules called the standard library. Each module is a Python program that contains a related group of functions that can be embedded in your programs. For example, the math module has mathematics related functions, the random module has random number–related functions, and so on.

Before you can use the functions in a module, you must import the module with an import statement. In code, an import statement consists of the following:
* The import keyword
* The name of the module
* Optionally, more module names, as long as they are separated by commas

Once you import a module, you can use all the cool functions of that
module. Let’s give it a try with the random module, which will give us access
to the `random.randint()` function.

Enter this code into the file editor, and save it as printRandom.py:

```python
import random
for i in range(5):
    print(random.randint(1, 10))
```

The random.randint() function call evaluates to a random integer value between the two integers that you pass it. Since randint() is in the random module, you must first type random. in front of the function name to tell Python to look for this function inside the random module.

Here’s an example of an import statement that imports four different modules:

```
import random, sys, os, math
```

Now we can use any of the functions in these four modules.

### from import Statements

An alternative form of the import statement is composed of the from keyword, followed by the module name, the import keyword, and a star; for example

```python
from random import *.
```

With this form of import statement, calls to functions in random will not need the random. prefix. However, using the full name makes for more readable code, so it is better to use the normal form of the import statement.

### Ending a Program Early with sys.exit()

The last flow control concept to cover is how to terminate the program. This always happens if the program execution reaches the bottom of the instructions. However, you can cause the program to terminate, or exit, by calling the sys.exit() function. Since this function is in the sys module, you have to import sys before your program can use it.
Open a new file editor window and enter the following code, saving it as exitExample.py:

```python
import sys
while True:
    print('Type exit to exit.')
    response = input()
    if response == 'exit':
        sys.exit()
print('You typed ' + response + '.')
```

## Functions

You’re already familiar with the print(), input(), and len() functions from the previous sections. Python provides several builtin functions like these, but you can also write your own functions. A function is like a mini-program within a program.

To better understand how functions work, let’s create one. Type this program into the file editor and save it as helloFunc.py:

```python
def hello():
    print('Howdy!')
    print('Howdy!!!')
    print('Hello there.')
hello()
hello()
hello()
```

### Functions with parameters

When you call the print() or len() function, you pass in values, called arguments in this context, by typing them between the parentheses. You can also define your own functions that accept arguments. Type this example into the file editor and save it as helloFunc2.py:

```python
def hello(name):
    print('Hello ' + name)
    hello('Alice')
    hello('Bob')
```

When you run this program, the output looks like this:

```
Hello Alice
Hello Bob
```

The definition of the hello() function in this program has a parameter called name. A parameter is a variable that an argument is stored in when a function is called. The first time the hello() function is called, it’s with the argument 'Alice'. The program execution enters the function, and the variable name is automatically set to 'Alice', which is what gets printed by the print() statement.

### Functions with return statements

When you call the len() function and pass it an argument such as 'Hello', the function call evaluates to the integer value 5, which is the length of the string you passed it. In general, the value that a function call evaluates to is called the return value of the function.

When creating a function using the def statement, you can specify what the return value should be with a return statement. A return statement consists of the following:

* The return keyword
* The value or expression that the function should return

When an expression is used with a return statement, the return value is what this expression evaluates to. For example, the following program defines a function that returns a different string depending on what number it is passed as an argument. Type this code into the file editor and save it as magic8Ball.py:

```python
import random
def getAnswer(answerNumber):
    if answerNumber == 1:
        return 'It is certain'
    elif answerNumber == 2:
        return 'It is decidedly so'
    elif answerNumber == 3:
        return 'Yes'
    elif answerNumber == 4:
        return 'Reply hazy try again'
    elif answerNumber == 5:
        return 'Ask again later'
    elif answerNumber == 6:
        return 'Concentrate and ask again'
    elif answerNumber == 7:
        return 'My reply is no'
    elif answerNumber == 8:
        return 'Outlook not so good'
    elif answerNumber == 9:
        return 'Very doubtful'
r = random.randint(1, 9)
fortune = getAnswer(r)
print(fortune)
```

### The None Value

In Python there is a value called None, which represents the absence of a value. None is the only value of the NoneType data type. (Other programming languages might call this value null, nil, or undefined.) Just like the Boolean True and False values, None must be typed with a capital N.

This value-without-a-value can be helpful when you need to store something that won’t be confused for a real value in a variable.

### Keyword Arguments

Most arguments are identified by their position in the function call. For example, random.randint(1, 10) is different from random.randint(10, 1). The function call random.randint(1, 10) will return a random integer between 1 and 10, because the first argument is the low end of the range and the second argument is the high end (while random.randint(10, 1) causes an error).

However, keyword arguments are identified by the keyword put before them in the function call. Keyword arguments are often used for optional parameters. For example, the print() function has the optional parameters end and sep to specify what should be printed at the end of its arguments and between its arguments (separating them), respectively.

If you ran the following program:

```python
print('Hello')
print('World')
```

the output would look like this:

```shell
Hello
World
```

The two strings appear on separate lines because the print() function automatically adds a newline character to the end of the string it is passed. However, you can set the end keyword argument to change this to a different string. For example, if the program were this:

```python
print('Hello', end='')
print('World')
```

the output would look like this:

```shell
HelloWorld
```

## A Short Program: Guess the Number

The toy examples I’ve show you so far are useful for introducing basic concepts, but now let’s see how everything you’ve learned comes together in a more complete program. In this section, I’ll show you a simple “guess the number” game. When you run this program, the output will look something like this:

```
I am thinking of a number between 1 and 20.
Take a guess.
10
Your guess is too low.
Take a guess.
15
Your guess is too low.
Take a guess.
17
Your guess is too high.
Take a guess.
16
Good job! You guessed my number in 4 guesses!
```

## Lists

The List Data Type
A list is a value that contains multiple values in an ordered sequence. The term list value refers to the list itself (which is a value that can be stored in a variable or passed to a function like any other value), not the values inside the list value. A list value looks like this: `['cat', 'bat', 'rat', 'elephant']`. Just as string values are typed with quote characters to mark where the string begins and ends, a list begins with an opening square bracket and ends with a closing square bracket, []. Values inside the list are also called items. Items are separated with commas (that is, they are comma-delimited). For example, enter the following into the interactive shell:

```shell
>>> [1, 2, 3]
[1, 2, 3]
>>> ['cat', 'bat', 'rat', 'elephant']
['cat', 'bat', 'rat', 'elephant']
>>> ['hello', 3.1415, True, None, 42]
['hello', 3.1415, True, None, 42]
>>> foo = ['cat', 'bat', 'rat', 'elephant']
>>> foo
['cat', 'bat', 'rat', 'elephant']
```

### Getting Individual Values in a List with Indexes
Say you have the list `['cat', 'bat', 'rat', 'elephant']` stored in a variable named foo. The Python code foo[0] would evaluate to 'cat', and foo[1] would evaluate to 'bat', and so on. The integer inside the square brackets that follows the list is called an index. The first value in the list is at index 0, the second value is at index 1, the third value is at index 2, and so on. Figure 4-1 shows a list value assigned to foo, along with what the index expressions would evaluate to. For example, type the following expressions into the interactive shell. Start by assigning a list to the variable foo.

```shell
>>> foo = ['cat', 'bat', 'rat', 'elephant']
>>> foo[0]
'cat'
>>> foo[1]
'bat'
>>> foo[2]
'rat'
>>> foo[3]
'elephant'
foo = ["cat", "bat", "rat", "elephant"]
>>> ['cat', 'bat', 'rat', 'elephant'][3]
'elephant'
>>> 'Hello ' + foo[0]
'Hello cat'
>>> 'The ' + foo[1] + ' ate the ' + foo[0] + '.'
'The bat ate the cat.'
```

### Multidimensional List

Lists can also contain other list values. The values in these lists of lists can be accessed using multiple indexes, like so:

```shell
>>> foo = [['cat', 'bat'], [10, 20, 30, 40, 50]]
>>> foo[0]
['cat', 'bat']
>>> foo[0][1]
'bat'
>>> foo[1][4]
50
```

### Negative Indexes

While indexes start at 0 and go up, you can also use negative integers for
the index. The integer value -1 refers to the last index in a list, the value -2
refers to the second-to-last index in a list, and so on. Enter the following
into the interactive shell:

```shell
>>> foo = ['cat', 'bat', 'rat', 'elephant']
>>> foo[-1]
'elephant'
>>> foo[-3]
'bat'
>>> 'The ' + foo[-1] + ' is afraid of the ' + foo[-3] + '.'
'The elephant is afraid of the bat.'
```

### Getting Sublists with Slices
Just as an index can get a single value from a list, a slice can get several values from a list, in the form of a new list. A slice is typed between square brackets, like an index, but it has two integers separated by a colon. Notice the difference between indexes and slices.

* foo[2] is a list with an index (one integer).
* foo[1:4] is a list with a slice (two integers).

In a slice, the first integer is the index where the slice starts. The second
integer is the index where the slice ends. A slice goes up to, but will not
include, the value at the second index. A slice evaluates to a new list value.
Enter the following into the interactive shell:

```shell
>>> foo = ['cat', 'bat', 'rat', 'elephant']
>>> foo[0:4]
['cat', 'bat', 'rat', 'elephant']
>>> foo[1:3]
['bat', 'rat']
>>> foo[0:-1]
['cat', 'bat', 'rat']
```

### Getting a List’s Length with len()

The len() function will return the number of values that are in a list value passed to it, just like it can count the number of characters in a string value. Enter the following into the interactive shell:

```shell
>>> foo = ['cat', 'dog', 'moose']
>>> len(foo)
3
```

### Removing Values from Lists with del Statements

The del statement will delete values at an index in a list. All of the values in the list after the deleted value will be moved up one index. For example, enter the following into the interactive shell:

```
>>> foo = ['cat', 'bat', 'rat', 'elephant']
>>> del foo[2]
>>> foo
['cat', 'bat', 'elephant']
>>> del foo[2]
>>> foo
['cat', 'bat']
```

### Using for Loops with Lists
Earlier, you learned about using for loops to execute a block of code a certain number of times. Technically, a for loop repeats the code block once for each value in a list or list-like value. For example, if you ran this code:

```python
for i in range(4):
	print(i)
```

The output of this program would be as follows:

```
0
1
2
3
```

This is because the return value from range(4) is a list-like value that
Python considers similar to [0, 1, 2, 3]. The following program has the
same output as the previous one:

```python
for i in [0, 1, 2, 3]:
	print(i)
```

### Finding a Value in a List with the index() Method

List values have an index() method that can be passed a value, and if that
value exists in the list, the index of the value is returned. If the value isn’t
in the list, then Python produces a ValueError error. Enter the following into
the interactive shell:

```python
>>> foo = ['hello', 'hi', 'howdy', 'heyas']
>>> foo.index('hello')
0
>>> foo.index('heyas')
3
>>> foo.index('howdy howdy howdy')
Traceback (most recent call last):
 File "<pyshell#31>", line 1, in <module>
 foo.index('howdy howdy howdy')
ValueError: 'howdy howdy howdy' is not in list
```

When there are duplicates of the value in the list, the index of its first
appearance is returned. Enter the following into the interactive shell, and
notice that index() returns 1, not 3:

```
>>> foo = ['Zophie', 'Pooka', 'Fat-tail', 'Pooka']
>>> foo.index('Pooka')
1
```

### Adding Values to Lists with the append() and insert() Methods

To add new values to a list, use the append() and insert() methods. Enter the following into the interactive shell to call the append() method on a list value stored in the variable foo:

```python
>>> foo = ['cat', 'dog', 'bat']
>>> foo.append('moose')
>>> foo
['cat', 'dog', 'bat', 'moose']
```

The previous append() method call adds the argument to the end of the list. The insert() method can insert a value at any index in the list. The first argument to insert() is the index for the new value, and the second argument is the new value to be inserted. Enter the following into the interactive shell:

```python
>>> foo = ['cat', 'dog', 'bat']
>>> foo.insert(1, 'chicken')
>>> foo
['cat', 'chicken', 'dog', 'bat']
```

## The Dictionary Data Type

Like a list, a dictionary is a collection of many values. But unlike indexes for lists, indexes for dictionaries can use many different data types, not just integers. Indexes for dictionaries are called keys, and a key with its associated value is called a key-value pair.
In code, a dictionary is typed with braces, {}. Enter the following into the interactive shell:

```shell
>>> myCat = {'size': 'fat', 'color': 'gray', 'disposition': 'loud'}
```

This assigns a dictionary to the myCat variable. This dictionary’s keys are 'size', 'color', and 'disposition'. The values for these keys are 'fat', 'gray', and 'loud', respectively. You can access these values through their keys:

```shell
>>> myCat['size']
'fat'
>>> 'My cat has ' + myCat['color'] + ' fur.'
'My cat has gray fur.'
```

Dictionaries can still use integer values as keys, just like lists use integers for indexes, but they do not have to start at 0 and can be any number.

```shell
>>> foo = {12345: 'Luggage Combination', 42: 'The Answer'}
```

### The keys(), values(), and items() Methods

There are three dictionary methods that will return list-like values of the dictionary’s keys, values, or both keys and values: keys(), values(), and items(). The values returned by these methods are not true lists: They cannot be modified and do not have an append() method. But these data types (dict_keys, dict_values, and dict_items, respectively) can be used in for loops. To seehow these methods work, enter the following into the interactive shell:

```
>>> foo = {'color': 'red', 'age': 42}
>>> for v in foo.values():
 print(v)
red
42
```

Here, a for loop iterates over each of the values in the foo dictionary. A for loop can also iterate over the keys or both keys and values:

```
>>> for k in foo.keys():
 print(k)
color
age
>>> for i in foo.items():
 print(i)
('color', 'red')
('age', 42)
```

Using the keys(), values(), and items() methods, a for loop can iterate over the keys, values, or key-value pairs in a dictionary, respectively. Notice that the values in the dict_items value returned by the items() method are tuples of the key and value. If you want a true list from one of these methods, pass its list-like return value to the list() function. Enter the following into the interactive shell:

```
>>> foo = {'color': 'red', 'age': 42}
>>> foo.keys()
dict_keys(['color', 'age'])
>>> list(foo.keys())
['color', 'age']
```

The list(foo.keys()) line takes the dict_keys value returned from keys() and passes it to list(), which then returns a list value of ['color', 'age']. You can also use the multiple assignment trick in a for loop to assign the key and value to separate variables. Enter the following into the interactive shell:

```
>>> foo = {'color': 'red', 'age': 42}
>>> for k, v in foo.items():
 print('Key: ' + k + ' Value: ' + str(v))
Key: age Value: 42
Key: color Value: red
```

### Checking Whether a Key or Value Exists in a Dictionary

Recall from the previous section that the in and not in operators can check whether a value exists in a list. You can also use these operators to see whether a certain key or value exists in a dictionary. Enter the following into the interactive shell:

```
>>> foo = {'name': 'Zophie', 'age': 7}
>>> 'name' in foo.keys()
True
>>> 'Zophie' in foo.values()
True
>>> 'color' in foo.keys()
False
>>> 'color' not in foo.keys()
True
>>> 'color' in foo
False
```

### Pretty Printing

If you import the pprint module into your programs, you’ll have access to the pprint() and pformat() functions that will “pretty print” a dictionary’s values. This is helpful when you want a cleaner display of the items in a dictionary than what print() provides. Modify the previous characterCount.py program and save it as prettyCharacterCount.py.

```python
import pprint
message = 'It was a bright cold day in April, and the clocks were striking
thirteen.'
count = {}
for character in message:
 count.setdefault(character, 0)
 count[character] = count[character] + 1
pprint.pprint(count)
```

This time, when the program is run, the output looks much cleaner, with the keys sorted.

```json
{
	" ": 13,
	",": 1,
	".": 1,
	"A": 1,
	"I": 1,
	"a": 4,
	"b": 1,
	"c": 3,
	"d": 3,
	"e": 5,
	"g": 2,
	"h": 3,
	"i": 6,
	"k": 2,
	"l": 3,
	"n": 4,
	"o": 2,
	"p": 1,
	"r": 5,
	"s": 3,
	"t": 6,
	"w": 2,
	"y": 1
}
```
The pprint.pprint() function is especially helpful when the dictionary itself contains nested lists or dictionaries.
