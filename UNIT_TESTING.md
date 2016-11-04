# Unit testing 

## What are unit tests?
* Unit tests are been designed to test a specific functionality of code
* They are used by the programmer to make sure the code is doing what it's supposed to be doing
* A unit test could, for example, verify the behavior of one function in a class or module
* Unit tests compare the output of a piece of code with something you know it should be producing

## Why create unit tests?
* They tell us whether the code in question is working correctly
* They help ensure new commits don't break the functionality of the code
* They place basic guaranties on end-users that code is minimally trustworthy

### Unit tests versus integration tests
* Unit tests verify whether a piece of code---or _unit_ of code---is working correctly, whereas an integration test ensures that
different pieces of code work together as whole i.e. that different pieces of code are well _integrated_.

## Examples

For the sake of example, let's say we've created the function below

```
def make_integer(float_number):
    """ 
    Function to turn floats into integers.
    """
    return int(float_number)
```  

A unit test for this function could be

```
def test_make_integer(float_number):
    """
    Tests whether 'make_integer' outputs integers
    """
    assert type(make_integer(float_number)) == int
```

The test is simple, has an informative name, and verifies a single aspect of the code.

Writing unit tests for scientific computing is usually more difficult.
* Highlight particularly nice tests from around the Choderalab Github repository.

## Python software
There are a few programs that can be used to automate the testing of the code, such as
* pytest: http://doc.pytest.org/en/latest/
* unittest: https://docs.python.org/3/library/unittest.html#module-unittest
* nose2: http://nose2.readthedocs.io/en/latest/

### Example of using Pytest
[To do]

## The format of tests
* The naming convention of tests
* Separate folder for all tests, called `tests`
* Examples from the lab

## References and further reading
http://docs.python-guide.org/en/latest/writing/tests/
http://pythontesting.net/framework/pytest/pytest-introduction/
http://www.codesimplicity.com/post/the-philosophy-of-testing/