# Python coding best practices

You are writing code that you and other people will read and modify multiple times, so there are few things to keep in mind that will simplify your life:
- **Keep it simple, clean and documented.** Your code is your best methods section! Write it so that your colleagues can understand it easily. Write it so that you will remember what you did in 6 months from now.
- **Make it robust and extensible.** Writing robust code means you will spend less time debugging, or (even worse) analyzing results from an incorrect code. Writing extensible code means you will spend less time modifying your code.

This article tries to offer practical suggestions on how to achieve these two (sometimes clashing) goals.

1. [Use a modern environment](#use-a-modern-environment)
2. [Keep clean and adhere to PEP8](#keep-clean-and-adhere-to-pep8)
3. [Document your code](#document-your-code)
4. [Find bugs before they find you](#find-bugs-before-they-find-you)
5. [Know the basic OOP design principles](#know-the-basic-oop-design-principles)


## Use a modern environment

- **Use Python 3!** Almost all scientific packages have now added Python 3 support, and many are making plans to drop Python 2 support.

- **Use a good editor.** Until you try, you have no idea how much it can speed you up. It will catch syntactic (and some semantic) errors for you. Autocompletion will save you from misspelling variable/function names. The "jump to definition" (and documentation) feature will spare you a lot of file browsing looking for other code. My personal favorite is PyCharm, but any editor with those features will do.


## Keep clean and adhere to PEP8

[PEP8](https://www.python.org/dev/peps/pep-0008/) is document defining a stylistic standard to make Python code more readable/understandable. Almost the entirety of python packages out there adopt it. The document is not the most exciting read, but the good news is __you don't have to read it if you are using a good editor__ that will highlight PEP8 violations. Here are summarized the most practically useful guidelines with a brief rationale.

- **Favor consistency over PEP8.** First, know when *not* adhere to PEP8. It is a standard set of guidelines, not rules. If you are working on a codebase adopting other conventions, stick with them. Just have a consistent style throughout your project. If you are writing new code, there is no really good reason to not adhere to PEP8.

- **Adopt different naming conventions for constants, variables, types, and modules.** It is much easier to understand the code if you can immediately distinguish functions from classes just based on their name.

Public | Internal usage only
-------|--------------------
`modulename` and `packagename` | `_modulename` and `_packagename`
`ClassName` (and `ExceptionName`) | `_ClassName` (and `_ExceptionName`)
`variable_name` | `_variable_name`
`function_name()` | `_function_name()`
`CONSTANT_NAME` | `_CONSTANT_NAME`

- **Know where you put your spaces.** It will be easier to search things in your code and browse it.
```python
# No spaces before or inside parentheses and brackets
spam(ham[1], {eggs: 2})  # Yes
spam( ham[ 1 ], { eggs: 2 } )  # No

# A single space on either side of assignment, comparison, and boolean operators
x = 1; y <= x; x and y  # Yes
 x=1;  y <=x; x  and  y  # No
function(arg1=3, arg2=4.0)  # Exception: no spaces for keyword arguments

# A space after commas, colons, and semi-colons
if x == 4: print x, y; x, y = y, x  # Yes
if x == 4 : print x , y ; x , y = y , x  # No
ham[1:9], ham[1:9:3], ham[:9:3], ham[1::3], ham[1:9:]  # Exception: when using colon as slice operator
```

- **Keep your lines short.** It allows to have two columns of code side by side, which is handy when reviewing diff in version control. You can use parentheses or `\` to go to a new line.
```python
my_long_string = ("can be divided over multiple "
                  "lines using parentheses.")
```

## Document your code
- Add docstrings to functions
- Use one-line docstring for obvious functions
- Example of multi-line docstring
- Using specific formats allow you to use existing software (Sphinx) which parses python code and automatically generate documentation in many formats (e.g. HTML, PDF, LaTex). The main standard formats:
	- reStructuredText (link): the most common
	- Numpydoc (link): more readable but harder to comply to
	- Google style (link): Numpydoc is based on this
	- Epydoc (link): based on javadoc, discontinued (last release in 2008) but still found in old projects
- Link to main documentation tutorial

## Find bugs before they find you
Testing and common subtle pitfalls
- TDD (see separate tutorial on testing)
- don't use equal comparison on floats
- don't use mutable types as default arguments of functions
- avoid coercing types when possible
- avoid functions arguments that can have multiple types
- avoid abusing kwargs

## Know the basic OOP design principles
The main goal of object-oriented programming (OOP) design is to provide guidelines to write **code that is fast to change without breaking backwards compatibility**. In science, breaking backwards compatibility often means impeding easy reproducibility. While this is especially important if you are writing a Python tool that other people will use, consider that you are the first user of your code, and learning about this principles (and when _not_ to apply them) can speed you up considerably. There is a [separate article]() with practical advices on Python library/tool-making.
