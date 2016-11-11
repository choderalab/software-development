# Unit testing

## What are unit tests?
* [Unit tests](https://en.wikipedia.org/wiki/Unit_testing) are designed to test a specific functionality of code
* They are used by the programmer to make sure the code is doing what it's supposed to be doing
* A unit test could, for example, verify the behavior of a single function in a class or module
* Unit tests compare the output of a piece of code with expected output to determine whether the test should pass or fail

## Why create unit tests?
* They tell us whether the code in question is working as expected
* They help to catch bugs
* They provide basic guaranties that code is minimally trustworthy
* They help ensure new commits don't break the functionality of the code

### Unit tests versus integration tests
Unit tests verify whether a piece of code---or _unit_ of code---is working correctly, whereas an [integration test](https://en.wikipedia.org/wiki/Integration_testing) ensures that
different pieces of code work together correctly as whole, i.e., that different pieces of code are well _integrated_.

## Simple example

For the sake of example, let's say we've created the function below

```python
def make_integer(float_number):
    """
    Function to turn floats into integers.
    """
    return int(float_number)
```  

A unit test for this function could be

```python
def test_make_integer(float_number):
    """
    Tests whether 'make_integer' outputs integers
    """
    assert type(make_integer(float_number)) == int
```

The test is simple, has an informative name, and verifies a single aspect of the code.

In this example, the test has been written using the [`assert`](https://wiki.python.org/moin/UsingAssertionsEffectively) statement,
which throws an [`AssertionError`](https://docs.python.org/3/library/exceptions.html) if the logical statement that proceeds it evaluates to `False`.

## Unit tests for scientific computing

When writing tests for scientific software, unit tests are especially important
to help verify the code is capable of addressing the scientific questions at hand.
This can be achieved by testing the code on a problem one already knows the answer to.
For instance, if the scientific tool is an optimization algorithm, a basic test
would be to find the minimum of a simple quadratic function, such as `y = x*x`.
Or, if the scientific tool is a Markov chain Monte Carlo sampler, then one can generate samples
from a distribution with known statistical properties, such as a Gaussian distribution, and
check to ensure that moments are correctly reproduced to within some minimal statistical error.

Good example of tests for scientific computing are the `pymbar` tests:

https://github.com/choderalab/pymbar/blob/master/pymbar/tests/test_mbar.py

## Python software
There are a few programs that can be used to automate the testing of the code, such as
* [`pytest`](http://doc.pytest.org/en/latest/): The recommended modern testing framework
* [`nose2`](http://nose2.readthedocs.io/en/latest/): A modern replacement for the now-unmaintained (and no longer recommended) [`nose`](http://nose.readthedocs.io/en/latest/) testing framework
* [`unittest`](https://docs.python.org/3/library/unittest.html#module-unittest): A standard Python testing framework with some limitations

Once you have the tests automated, you can also enable [continuous integration](https://github.com/choderalab/software-development/blob/master/CONTINUOUS_INTEGRATION.md) for your project to ensure these tests are run on any proposed code changes and ensure changes do not break the code.

## Additional points and conventions
* All tests are typically contained in a folder called `tests/`.
* The tests folder is typically installed along with the package (by placing it in `packagename/tests/`), which allows the installed package to be tested in place.
* Functions that evaluate tests follow the naming convention `test_foo_bar`
* Classes that contain a number of related tests follow the naming convention `TestsFooBar`
* Unit tests should be as fast as possible so that they can be used in [continuous integration](https://github.com/choderalab/software-development/blob/master/CONTINUOUS_INTEGRATION.md) environments.

## References and further reading
* http://docs.python-guide.org/en/latest/writing/tests/
* http://pythontesting.net/framework/pytest/pytest-introduction/
* http://www.codesimplicity.com/post/the-philosophy-of-testing/

## Advanced topics
* Testing code with stochastic outcomes
* Evaluating test coverage with tools like [coveralls](https://coveralls.io/)
* [Test-driven development](https://en.wikipedia.org/wiki/Test-driven_development)

## Help Make this Page Better

Want to contribute to this repository? Have a suggestion for an improvement?
Spot a typo? We're always looking to improve this document for the betterment of all.

* Please feel free to [open a new issue](https://github.com/choderalab/software-development/issues/new) with your feedback and suggestions!
* Or [make a pull request](https://github.com/choderalab/software-development/compare) from your branch or fork!
