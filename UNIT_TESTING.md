# Unit testing 

## What are unit tests?
* Unit tests are been designed to test a specific functionality of code
* They are used by the programmer to make sure the code is doing what it's supposed to be doing
* A unit test could, for example, verify the behavior of one function in a class or module
* Unit tests compare the output of a piece of code with something you know it should be producing

## Why create unit tests?
* They tell us whether the code in question is working correctly
* They place basic guaranties on end-users that code is minimally trustworthy
* They help ensure new commits don't break the functionality of the code

### Unit tests versus integration tests
Unit tests verify whether a piece of code---or _unit_ of code---is working correctly, whereas an integration test ensures that
different pieces of code work together as whole i.e. that different pieces of code are well _integrated_.

## Simple example

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

In this example, the test has been written using the `assert` command, which throws an `AssertionError` if the logical statement that proceeds
it is false. 

## Unit tests for scientific computing

When writing tests for scientific software, unit tests are especially important 
to help verify the code is capable of addressing the scientific questions one has. 
This can be achieved by test the code on a problem one already knows the answer to.
For instance, if the scientific tool is a global optimization algorithm, a basic test
would be to find the minimum of a simple quadratic function, such as `y = x*x`.
Or, if the scientific tool is a Markov chain Monte Carlo sampler, then one can generate samples
from a distribution one already knows the statistical properties, such as a Gaussian distribution. 
 
Good example of tests for scientific computing are the `pymbar` tests:

https://github.com/choderalab/pymbar/blob/master/pymbar/tests/test_mbar.py

## Python software
There are a few programs that can be used to automate the testing of the code, such as
* pytest: http://doc.pytest.org/en/latest/
* unittest: https://docs.python.org/3/library/unittest.html#module-unittest
* nose2: http://nose2.readthedocs.io/en/latest/

## Additional points and conventions
* Typically all tests are contained in a folder called `tests`
* Functions that evaluate tests follow the naming convention `test_foo_bar`
* Classes that contain a number of related tests follow the naming convention `TestsFooBar`
* Unit tests should be as fast as possible

## References and further reading
http://docs.python-guide.org/en/latest/writing/tests/
http://pythontesting.net/framework/pytest/pytest-introduction/
http://www.codesimplicity.com/post/the-philosophy-of-testing/