# Python coding best practices

You are writing code that you and other people will read and modify multiple times, so there are few things to keep in mind that will simplify your life:
- **Keep it simple, clean and documented.** Your code is your best methods section! Write it so that your colleagues can understand it easily. Write the documentation so that you will remember what you did 6 months from now.
- **Make it robust and extensible.** Writing robust code means you will spend less time debugging, or (even worse) analyzing results from an incorrect code. Writing extensible code means you will spend less time modifying it.

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
Docstrings are special strings used to document your code that are internally supported by Python. The general guidelines are defined by [PEP257](https://www.python.org/dev/peps/pep-0257/), but there are specific formats that can be parsed by **automatic documentation generators**, most commonly [Sphinx](http://www.sphinx-doc.org/en/1.4.8/):

- [reStructuredText](http://docutils.sourceforge.net/docs/user/rst/quickstart.html): The most common format. Very flexible and natively supported by Sphinx.
- [Numpydoc](https://github.com/numpy/numpy/blob/master/doc/HOWTO_DOCUMENT.rst.txt): Generally more readable, but harder to comply to. A plugin adds Numpydoc support to Sphinx.
- Google style: The Numpydoc syntax is based on this.
- Epydoc: Based on Javadoc. It is now discontinued (last release was 2008), but it can still be found in certain projects.

See [this tutorial]() to get started. Here is a very minimal example with Numpydoc syntax. If you have a module called `mymodule.py`
```python
"""Docstring for my module.py.

All docstrings start and end with triple double quotes.

"""


def add_numbers(number1, number2):
    """For obvious functions a single-line description is enough."""
    return number1 + number2


class MyClass:
    """One-line summary of MyClass.

    For more complex code, give a one-line summary followed by a
    further description that can go over multiple lines.

    Attributes
    ----------
    my_float : float
        Description of attribute.

    """

    def __init__(self, my_float):
        self.my_float = my_float

    def multiply(self, number):
        """Return number * self.my_float.

        Parameters
        ----------
        number : float
            This is multiplied by self.my_float.

        Returns
        -------
        float
            Result of multiplication.

        """
        return self.my_float * number
```
you can use
```
python
>>> import mymodule
>>> help(mymodule)
>>> help(mymodule.MyClass.multiply)
```
to obtain information on how to use the code in `mymodule.py`.


## Find bugs before they find you
Nothing wastes your time like a bug that does not raise an error. You can spend several week on some results before you realize your code is incorrect. There are few practices that can help you to **prevent introducing bugs.**
- **First and foremost, write tests!** The paradigm of test-driven development is simple:
  1. Create a test that fails, so that you know you are testing the right thing.
  2. Implement only the feature that make you pass the test.
  3. Clean up your code (refactor, update docs, etc.) and repeat.

  Several Python tools (pytest, nose2, unittest), allow you to run tests automatically. This will lower the chances of introducing regressions when you modify your code. See this [tutorial on testing]() for more information, and to get started.
- **Do not compare floats for equality.** Because computers represent real numbers in binary with finite precision, you can obtain unexpected results. For example, `0.1` has a periodic binary representation, and it cannot be expressed by a finite number of bits.

   ```python
>>> 0.1 + 0.1 + 0.1 == 0.3
False
```
It is generally fine to compare for equality floats up to some finite precision
   ```python
>>> round(0.1 + 0.1 + 0.1, 10) == round(0.3, 10)
True
```
- **Do not use mutable types as default arguments.**  Python creates default arguments when functions are defined, not when they are called, so changes to your default object will be permanent.

   ```python
def append(element, list_=[]):
        list_.append(element)
        return list_

>>> print(append(0))
[0]
>>> print(append(1))
[0, 1]
```
   instead prefer
   ```python
def append(element, list_=None):
        if list_ is None:
            list_ = []
        list_.append(element)
        return list_
```
- **Avoid generic type coercion when possible.** It is easy to catch in the mix unwanted types and mask a bug upstream.
   ```python
squared_lookup_table = [x*x for x in range(100)]

def square_integers(integer_list):
        """Element-wise square of the given list of integers."""
        integer_list = [int(x) for x in integer_list]  # let's convert floats to int
        return [squared_lookup_table[i] for i in integer_list]

>>> square_integers([0, 4, 10])
[0, 16, 100]
>>> square_integers('92')  # you want this to fail to catch a bug!
[81, 4]
```
   If you absolutely have to coerce a type, tighten it up to be sure you are coercing only those you want.
   ```python
def square_integers(integer_list):
        integer_list = [int(round(x)) for x in integer_list]  # This always fails with strings.
        return [squared_lookup_table[i] for i in integer_list]
```
   It is generally safer to leave any type of coercion to the user of the function since he knows what kind of data he intends to pass.
- **Avoid abusing kwargs.** Using `**kwargs` is a general way to forward keyword arguments to another (possibly unknown) function, but when used instead of normal keyword arguments, it can mask bugs in your program.
   ```python
def decorate_str(decorated, **kwargs):
        """Prepend and append a decoration string."""
        separator = kwargs.get('separator', '_')  # default is '_'
        decoration = kwargs.get('decoration_string', '')  # default is ''
        return decoration + separator + decorated + separator + decoration

>>> decorate_str('decorated', decoration_string='foo')
'foo_decorated_foo'
>>> decorate_str('decorated', decoration_str='foo')  # Whops! No Error because kwargs disrupt introspection!
'_decorated_'
```
   If you want to use `**kwargs` instead of normal keyword argument, add manually some control logic.
   ```python
def decorate_str(decorated, **kwargs):
        """Prepend and append a decoration string."""
        separator = kwargs.pop('separator', '_')  # default is '_'
        decoration = kwargs.pop('decoration_string', '')  # default is empty string
        if kwargs != {}:
            raise TypeError('got unexpected keyword arguments {}'.format(kwargs))
        return decoration + separator + decorated + separator + decoration
```
   But it is usually more readable to just use keyword arguments (and does not break the autocompletion feature).
   ```python
def decorate_str(decorated, separator='_', decoration_string=''):
        return decoration_string + separator + decorated + separator + decoration_string
```

## Know the basic OOP design principles
The main goal of object-oriented programming (OOP) design is to provide guidelines to write **code that is fast to change without breaking backwards compatibility**. In science, breaking backwards compatibility often means impeding easy reproducibility. While this is especially important if you are writing a Python tool that other people will use, consider that you are the first user of your code, and learning about this principles (and when _not_ to apply them) can speed you up considerably. There is a [separate article]() with practical advices on Python library/tool-making.
